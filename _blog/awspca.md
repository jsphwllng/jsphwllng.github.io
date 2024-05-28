---
layout: default
title: AWS Private Certificate Authority
description: "Using AWSPCA to issue certificates on EKS"
order: 18
---

AWS Private Certificate Authority (AWS Private CA) is a managed service that provides users with the ability to create and manage private certificates for their internal applications and services. AWSPCA allows the issuance of private TLS/SSL certificates for securing communication between Kubernetes components, such as pods, services, and applications. 

This service helps automate the lifecycle of certificates, ensuring timely renewal and revocation, thereby reducing the risk of security breaches due to expired or compromised certificates. 


<div class="mermaid" markdown="0">
graph TD
  
aws-privateca-->|issues on cluster|cert-manager
cert-manager-->|checks validity of certificate|aws-privateca
cert-manager-->|issues and renews|certificate
subgraph aws-resources
subgraph EKS cluster
        subgraph aws-pca-namespace
            aws-privateca
        end
        subgraph cert-manager-namespace
            cert-manager
        end  
        subgraph example-application-namespace
            application
            application-ingress
            certificate
        end
  end
    subgraph aws-certificate-manager
        root-authority
        subordinate-authority
    end
    subgraph load balancers
        example-application-lb
    end
    end
application<-->|exposed via|application-ingress
certificate[certificate as an encrypted secret]-->|passed into config|application-ingress
application-ingress<-->|accepts requests|example-application-lb
root-authority-->|grants|subordinate-authority
subordinate-authority-->|issues certificates using service role|aws-privateca
example-application-lb-->|DNS used in certificate request|cert-manager
</div>