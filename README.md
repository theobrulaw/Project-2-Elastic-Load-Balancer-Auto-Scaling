# Project 2: Elastic Load Balancer Auto Scaling

## Objective

This lab demonstrates how to design and deploy a highly available, fault-tolerant EC2 environment using an Elastic Load Balancer (ELB) and Auto Scaling Groups (ASG) in AWS.

The project simulates real-world production workloads where traffic fluctuates and infrastructure must automatically scale while maintaining performance and uptime. This architecture is foundational for modern cloud-native applications, DevOps pipelines, and resilient systems engineering.

---

## Architecture / Environment Overview

The environment consists of:

- Amazon EC2 instances deployed across multiple Availability Zones  
- Application Load Balancer (ALB) to distribute incoming traffic  
- Auto Scaling Group configured for automatic scale-out and scale-in  
- Amazon CloudWatch for metrics, alarms, and scaling triggers  
- Security Groups controlling inbound and outbound traffic  
- Custom AMI used as the EC2 launch template  

### Core Components

- **Load Balancer:** Routes HTTP traffic evenly across EC2 instances  
- **Auto Scaling Group:** Automatically adjusts capacity based on demand  
- **CloudWatch Alarms:** Monitor CPU utilization and trigger scaling events  
- **Launch Template:** Standardized EC2 configuration for scaling  

---

## Prerequisites

- AWS account with EC2, ELB, Auto Scaling, and CloudWatch permissions  
- Basic knowledge of:
  - EC2 instance deployment
  - Networking concepts (VPC, subnets, security groups)
  - Load balancing fundamentals  
- AWS CLI or AWS Management Console access  

---

## Steps Performed

1. Created a custom AMI with preconfigured web server
2. Configured a Launch Template using the AMI
3. Deployed an Application Load Balancer across multiple subnets
4. Created a Target Group for EC2 instances
5. Built an Auto Scaling Group linked to the load balancer
6. Defined scaling policies based on CPU utilization thresholds
7. Configured CloudWatch alarms to trigger scaling events
8. Tested load distribution and auto-healing behavior

---

## Validation & Verification

The system was verified using:

- Successful HTTP responses through Load Balancer DNS name  
- CloudWatch metrics showing traffic and CPU utilization  
- Automatic instance creation during simulated high load  
- Automatic termination of instances when load decreased  

### Key Observations

- Traffic evenly distributed across healthy instances  
- New EC2 instances registered automatically with ALB  
- Failed instances replaced without manual intervention  

---

## Security & Operational Considerations

- Security Groups restricted access to required ports only (HTTP/SSH)
- Instances placed in private subnets where applicable
- Load Balancer exposed publicly while backend instances remained protected
- IAM roles applied for CloudWatch monitoring permissions

### Operational Trade-offs

- Scaling thresholds must balance cost vs performance
- Health check tuning affects recovery speed
- Over-scaling can increase cloud spend

---

## Lessons Learned

- Auto Scaling significantly improves resilience and uptime  
- CloudWatch metrics are critical for proactive infrastructure response  
- Launch templates simplify standardized deployments  
- Proper health check configuration is essential for stability  

### Future Improvements

- Add HTTPS with AWS Certificate Manager  
- Implement infrastructure as code (Terraform or CloudFormation)  
- Integrate logging with CloudWatch Logs or ELK stack  
- Add WAF for application-layer protection  

---

## Project Summary

Implemented an auto-healing, load-balanced EC2 environment with CloudWatch monitoring and scaling policies to handle variable traffic loads automatically.

This project reflects real-world cloud architecture used in production systems to ensure availability, performance, and scalability.
