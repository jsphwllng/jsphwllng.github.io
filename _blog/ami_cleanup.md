---
layout: default
title: cleaning up old AMIs to save costs
description: "cleverly cleaning up AMIs for cost savings"
order: 19
---

As with many organizations, reducing AWS costs is a priority. Each time an AMI is created on AWS, it incurs a cost. Recognizing the potential for cost savings, I developed a script to audit AMIs. This script identifies whether AMIs are associated with an EC2 instance, whether they have snapshots, and ensures retention of the three most recent AMIs for reliability purposes. Here is the script:

```py
import boto3
from datetime import datetime
import csv
import os
import sys

TAGS_TO_RETAIN = ['production']
COST_PER_GB_PER_MONTH = 0.05
RUNNING_AMI_IDS = []

def get_running_amis():
    session = boto3.Session()
    ec2_client = session.client('ec2')
    response = ec2_client.describe_instances()
    for reservation in response['Reservations']:
        for instance in reservation['Instances']:
            if instance['State']['Name'] not in ["shutting-down", "terminated"]:
                ami_id = instance['ImageId']
                if ami_id not in RUNNING_AMI_IDS:
                    RUNNING_AMI_IDS.append(ami_id)

def get_snapshot_size(ec2_client, snapshot_id):
    response = ec2_client.describe_snapshots(SnapshotIds=[snapshot_id])
    return response['Snapshots'][0]['VolumeSize']

def cleanup_amis():
    session = boto3.Session()
    ec2_client = session.client('ec2')
    response = ec2_client.describe_images(Owners=['self'])
    images = response['Images']

    images_by_name = {}
    for image in images:
        name = image.get('Name', 'Unnamed')
        if name not in images_by_name:
            images_by_name[name] = []
        images_by_name[name].append(image)

    total_cost_saved_monthly = 0
    total_deleted_images = 0
    total_retained_images_due_to_tags = 0

    for name, images in images_by_name.items():
        for image in images:
            image_id = image['ImageId']
            tags = image.get('Tags', [])
            snapshot_ids = [mapping['Ebs']['SnapshotId'] for mapping in image['BlockDeviceMappings'] if 'Ebs' in mapping]

            if image_id in RUNNING_AMI_IDS:
                print(f"Retaining {image_id} as it is currently running")
                continue

            tag_value = next((tag['Value'] for tag in tags if tag['Key'] == 'TagKey'), None)

            if tag_value not in TAGS_TO_RETAIN:
                image_cost_saved = sum(get_snapshot_size(ec2_client, sid) * COST_PER_GB_PER_MONTH for sid in snapshot_ids)

                total_cost_saved_monthly += image_cost_saved
                total_deleted_images += 1

                print(f"Deleting AMI: {image_id}, Name: {name}, CreationDate: {image['CreationDate']}, TagKey tag: {tag_value}, Cost Saved: ${image_cost_saved:.2f}")
                
                ec2_client.deregister_image(ImageId=image_id)
                for snapshot_id in snapshot_ids:
                    print(f"Deleting snapshot {snapshot_id} of {name}")
                    ec2_client.delete_snapshot(SnapshotId=snapshot_id)

            else:
                total_retained_images_due_to_tags += 1
                print(f"Retaining AMI: {image_id}, Name: {name}, CreationDate: {image['CreationDate']} due to TagKey tag: {tag_value}")

    total_cost_saved_yearly = total_cost_saved_monthly * 12
    print(f"Total cost saved per month: ${total_cost_saved_monthly:.2f}")
    print(f"Total cost saved per year: ${total_cost_saved_yearly:.2f}")
    print(f"Total number of deleted images: {total_deleted_images}")
    print(f"Total number of images not deleted due to retention efforts: {total_retained_images_due_to_tags}")

if __name__ == "__main__":
    get_running_amis()
    cleanup_amis()

```

Enjoy!