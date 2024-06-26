---
layout: default
title: monitor your internet speed with python
description: "I live in Germany and Germany is known for its diversity. The people are diverse, the culture is diverse and the quality of internet connections are equally as diverse."
order: 1
---

I live in Germany and Germany is known for its diversity. The people are diverse, the culture is diverse and the quality of internet connections are equally as diverse. Having spoken to my internet provider who insisted I had no problems with my internet connection I decided to write a program to monitor my upload and download speed.

Getting started
---------------

We will be using two cool packages in python namely speedtest and matplotlib. speedtest will provide us with the information about our internet connection and matplotlib will allow us to generate graphs based on this information. Whether you're in a virtual environment or not using one you will have to install speedtest and matplotlib.

`pip install matplotlib pip install speedtest-cli`

We will also be using a few built in python packages datetime and csv. CSV (or comma separated values) are a quick way of storing data. We will be using this to store the information about our internet speeds and then using matplotlib to make this information visual.

Gathering data
--------------

Create a python file called monitor.py

and let's put the following code on the inside 

```sh
pip install matplotlib pip install speedtest-cli
```

and we should be greeted by the following output before hitting ctrl + C to get out of this infinite loop.

`75020309.22943133 24381170.373616524 105192450.00822952 40653433.153288215`

So by creating a new instance of speedtest as s and testing the upload and download speed we are given the upload and download speed in bits per second. To convert this to megabits per second (Mb/s) we can do the following to include the time of the test too:

```python
import speedtest 
import datetime 
s = speedtest.Speedtest() 
while True: 
  time = datetime.datetime.now().strftime("%H:%M:%S") 
  downspeed = round((round(s.download()) / 1048576), 2) 
  upspeed = round((round(s.upload()) / 1048576), 2) 
  print(f"time: {time}, downspeed: {downspeed} Mb/s, 
  upspeed: {upspeed} Mb/s")

```

```py
import speedtest
import datetime
import time
s = speedtest.Speedtest()

while True:
    time_now = datetime.datetime.now().strftime("%H:%M:%S")
    downspeed = round((round(s.download()) / 1048576), 2)
    upspeed = round((round(s.upload()) / 1048576), 2)
    print(f"time: {time_now}, downspeed: {downspeed} Mb/s, upspeed: {upspeed} Mb/s")
    # 60 seconds sleep
    time.sleep(60)

```

Which yields:

`time: 12:44:15, downspeed: 95.04 Mb/s, upspeed: 32.85 Mb/s time: 12:44:35, downspeed: 99.46 Mb/s, upspeed: 38.76 Mb/s time: 12:44:56, downspeed: 100.59 Mb/s, upspeed: 38.94 Mb/s`

Now we will move on to recording this in a CSV file. CSVs are large text files which values separated by commas. Here is an example of one of mine:

`time,downspeed,upspeed 12:17:01,100.05,38.28 12:17:21,100.53,37.85 12:17:42,74.87,25.92`

In order to record into a csv file in python we need to import the CSV package and 'open' a CSV file (if one doesn't exist it will create one).

```py
import speedtest
import datetime
import csv
import time

s = speedtest.Speedtest()

with open('test.csv', mode='w') as speedcsv:
    csv_writer = csv.DictWriter(speedcsv, fieldnames=['time', 'downspeed', 'upspeed'])
    csv_writer.writeheader()
    while True:
        time_now = datetime.datetime.now().strftime("%H:%M:%S")
        downspeed = round((round(s.download()) / 1048576), 2)
        upspeed = round((round(s.upload()) / 1048576), 2)
        csv_writer.writerow({
            'time': time_now,
            'downspeed': downspeed,
            "upspeed": upspeed
        })
        # 60 seconds sleep
        time.sleep(60)
```

So while you let this code run for 4-5 minutes we can discuss what is going on. Line 7 with open essentiallly creates a csv file with the name test.csv with the headers name, downspeed and upspeed and writers them into the csv. Then the loop begins and every time a test is performed by speedtest it writes a new row into the csv with the time, download speed and upload speed we specified before. So let's go and look at that now.

`time,downspeed,upspeed 12:51:16,99.29,38.66 12:51:37,100.67,38.79 12:51:57,99.7,38.79 12:52:17,92.89,31.99 12:52:38,99.4,38.96`

Cool now we are gathering information and storing it in a csv. You could do all sorts of clever stuff with the filename like name it today's date using datetime but for now I will keep it as test. You could also set up a check to see if a certain amount of time has passed and to stop the application after that but I will leave that up to your own creativity.

Visualising the data
--------------------

Let's make another python file to generate the graph of our internet connection. This is where we will use matplotlib.

```py
import matplotlib.pyplot as plt 
import csv import matplotlib.ticker as ticker 
times = [] 
download = [] 
upload = []
```

The easiest way to generate a graph is by using an array. In order to populate our arrays we will have to iterate through our new csv file

```py
with open('test.csv', 'r') as csvfile: 
  plots = csv.reader(csvfile, delimiter=',') 
  next(csvfile) 
  for row in plots: 
    times.append(str(row[0])) 
    download.append(float(row[1])) 
    upload.append(float(row[2])) 
    print(times, "\n", download, "\n", upload)`
```

 `['12:51:16', '12:51:37', '12:51:57', '12:52:17', '12:52:38'] [99.29, 100.67, 99.7, 92.89, 99.4] [38.66, 38.79, 38.79, 31.99, 38.96]`

So now we are parsing our data! The next(csvfile) essentially skipss the row of headers (that were for our benefit only, not python's). Now we come on to using [matplotlib](https://matplotlib.org/) which I am by no standards and expert on.

 ![](https://res.cloudinary.com/practicaldev/image/fetch/s--dpaMDQ21--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/1n9w54gko2qcaqc4cadd.jpg)
