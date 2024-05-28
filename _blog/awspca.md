---
layout: default
title: AWS Private Certificate Authority
description: "Using AWSPCA to issue certificates on EKS"
order: 18
---
  <script src="https://unpkg.com/mermaid@8.9.3/dist/mermaid.min.js"></script>
<script>
  $(document).ready(function () {
    mermaid.initialize({
      startOnLoad:true,
      theme: "default",
    });
    window.mermaid.init(undefined, document.querySelectorAll('.language-mermaid'));
  });
</script>
 
 ```
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
 ```