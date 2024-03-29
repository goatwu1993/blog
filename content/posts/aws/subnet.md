---
title: Subnet
date: 2022-09-23
draft: false
tags: [aws, vpc]
slug: subnet
summary: subnet
---

## What

Subnet belongs to a VPC. One subnet belongs to an AZ.

## AWS Reserved IP

AWS reserve **5** IP address in each subnet.

Example: For a subnet with CIDR 10.0.0.0/24

1. 10.0.0.0 is the subnet address
1. 10.0.0.1 is aws reserved IP for VPC router
1. 10.0.0.2 is aws reserved IP for AWS hosted DNS server
1. 10.0.0.3 is aws reserved IP for future usage...
1. 10.0.0.255 is the broadcast IP address. However AWS does not allow broadcasting in VPC, therefore reserved.

Therefore, if you needs 28 IP address in a subnet, you must open a CIDR with /26, since /27 will have 32-5 = 27 max IP address available.

## More Info

1. Subnet can have settings of Auto Assign Public IP settings, which will apply to resouces in subnet by default.

## Tips

1. For subnets with same usage, allocate to different AZ to have HA.
1. Can be associate to a route table.

## Private Subnet vs Public Subnet

### Public subnet

1. Public subnet is accessible from the Internet.
1. Public subnet attach to a public route table, usually with Internet Gateway route.
1. For public subnet to access Internet, use Internet Gateway.

### Private subnet

1. Private subnet is **NOT** accessible from the Internet.
1. Private subnet attach to a private route table, **without Internet Gateway**.
1. For private subnet to access Internet, use NAT Gateway.
1. If really needs public accees from the Internet to private subnet, use a **Bastion Host**.
