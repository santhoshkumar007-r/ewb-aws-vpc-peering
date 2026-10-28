# AWS VPC Peering Project – EWB Courses

## 1. Project Overview

This project demonstrates communication between two separate Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering. It uses private EC2 instances, route tables, security groups, and an EC2 Instance Connect Endpoint to establish and test private network connectivity.

## 2. Objectives

- Create two isolated VPCs with different IPv4 CIDR blocks.
- Configure public and private subnets.
- Establish a VPC peering connection between the two VPCs.
- Configure route tables to enable communication across the peering connection.
- Apply security group rules to control network traffic.
- Test connectivity between EC2 instances using ICMP ping.

## 3. AWS Services Used

- Amazon VPC
- Amazon EC2
- VPC Peering
- Internet Gateway
- Route Tables
- Security Groups
- Network ACLs
- EC2 Instance Connect Endpoint

## 4. Network Architecture

### VPC A – 10.10.0.0/16

- Public subnet: `10.10.1.0/24`
- Private subnet: `10.10.2.0/24`
- Bastion instance: `10.10.1.24`
- App-A instance: `10.10.2.10`

### VPC B – 10.20.0.0/16

- Private subnet: `10.20.1.0/24`
- App-B instance: `10.20.1.10`

### Peering Connection

The VPC peering connection links VPC A and VPC B. Routes are configured in both VPCs to direct traffic to the remote VPC CIDR through the peering connection.

## 5. Implementation Steps

1. Created VPC A and VPC B with non-overlapping CIDR ranges.
2. Created public and private subnets.
3. Attached an Internet Gateway to VPC A.
4. Launched the Bastion, App-A, and App-B EC2 instances.
5. Created and activated the VPC peering connection.
6. Added the required routes to the route tables in both VPCs.
7. Configured security groups to allow the required SSH and ICMP traffic.
8. Created an EC2 Instance Connect Endpoint in VPC B to access the private App-B instance.
9. Tested communication between the private instances.

## 6. Connectivity Testing

The connectivity test was performed from App-B to App-A using the command:

```bash
ping -c 4 10.10.2.10
```

**Observed result:** Four packets were received with 0% packet loss. This confirms successful ICMP connectivity from App-B to App-A across the VPC peering connection.

## 7. Project Evidence

AWS console screenshots documenting the VPC configuration, peering connection, route tables, EC2 instances, and connectivity tests are included in this repository.

## 8. Conclusion

This project demonstrates how AWS VPC Peering enables private communication between resources in two separate VPCs. Correct routing and security group configuration allow the instances to communicate without requiring public IP addresses on the private application instances.

---

**Project:** AWS VPC Peering  
**Training:** EWB Courses  
**Platform:** Amazon Web Services (AWS)
