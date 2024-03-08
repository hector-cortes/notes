---
tags: aws, aws/networking, dns
title: AWS DNS
---

## DNS

### DNS Hostnames (enableDnsHostnames)

* Determines whether the VPC supports assigning public DNS hostnames to instances with public IP addresses
  * If *both* DNS settings are true, instances in the VPC get public DNS hostnames
  * Default: False, unless the VPC is the default VPC or the VPC is being created using the VPC console wizard

### DNS Resolution (enableDnsSupport)

![DNS](drawings/dnsresolution.drawio.svg)

* Decides if DNS resolution from Route53 Resolver Server is supported by the VPC
  * Queries the Amazon Provider DNS Server at 169.254.169.253 or the reserved IP at the base of the VPC IPv4 network range plus two (.2)
  * Default: True, no matter how the VPC is created

#### Rules and Considerations

Rules

* If both attributes are True:

  * Instances with public IP addresses receive corresponding public DNS hostnames
  * Amazon Route 53 Resolver server can resolve Amazon-provided private DNS hostnames
* If at least one attribute is false:
  * Instances with public IPs do not receive corresponding public DNS names
  * Amazon Route 53 Resolver cannot resolve Amazon-provided private DNS hostnames
  * Instances receive custom private DNS hostnames if there is a custom domain name in the DHCP options set
    * If the Route53 Resolver is not being used, your custom domain name servers must resolve the hostname as appropriate

Considerations

* If you use custom DNS domain names defined in an Amazon Route53 private hosted zone, or use private DNS with interface VPC endpoints (AWS PrivateLink), you must set both the enableDnsHostnames and enableDnsSupport attributes to true
