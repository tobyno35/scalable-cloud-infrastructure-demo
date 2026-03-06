# Scalable & High-Availability AWS Infrastructure
    
    This repository demonstrates a production-ready AWS architecture designed for high availability and automatic scalability. The project focuses on infrastructure-level resilience and performance optimization.
    
    ## Architecture Overview
    The infrastructure is built across multiple Availability Zones to ensure fault tolerance and seamless traffic management.
    
    ### Key Components:
    - **Custom Amazon Machine Image (AMI):** Created a baseline image to ensure consistent software configuration for all launched instances.
    - **Application Load Balancer (ALB):** Deployed an internet-facing ALB to distribute traffic efficiently across the application tier.
    - **Auto Scaling Group (ASG):** Implemented an ASG to dynamically adjust capacity based on real-time demand.
    - **Target Tracking Scaling Policy:** Configured to maintain average CPU utilization at 50%, allowing the system to scale out during peaks and scale in to optimize costs.
    - **Health Monitoring:** Integrated ELB health checks to automatically replace unhealthy instances.
    
    ## Technical Details
    - **Environment:** Amazon Web Services (AWS)
    - **Instance Type:** t3.micro
    - **Networking:** Multi-AZ VPC with Public and Private subnets
    - **Monitoring:** Amazon CloudWatch Alarms
    
