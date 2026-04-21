# Scalable Cloud Infrastructure Demo

A production-style AWS infrastructure deployment demonstrating horizontal scaling, load balancing, and automated health monitoring. Built to simulate real-world high-availability architecture for web applications.

---

## Architecture Overview

```
Internet
    │
    ▼
Elastic Load Balancer (ALB)
    │
    ├──▶ EC2 Instance (AZ-1a)
    ├──▶ EC2 Instance (AZ-1b)  ◀── Auto Scaling Group
    └──▶ EC2 Instance (AZ-1c)
              │
              ▼
         CloudWatch Monitoring
              │
              ▼
         SNS Alerts
```

---

## Features

- **Auto Scaling Group** — automatically provisions or terminates EC2 instances based on CPU/load thresholds
- **Application Load Balancer** — distributes traffic across instances in multiple Availability Zones
- **Launch Template** — standardized EC2 configuration for consistent instance provisioning
- **CloudWatch Alarms** — monitors CPU utilization, request latency, and unhealthy host counts
- **SNS Notifications** — alerts on scaling events and threshold breaches
- **Multi-AZ Deployment** — high availability across multiple AWS Availability Zones

---

## Tech Stack

| Component | Service |
|---|---|
| Compute | AWS EC2 (Amazon Linux 2) |
| Load Balancing | AWS Application Load Balancer (ALB) |
| Auto Scaling | AWS Auto Scaling Group |
| Monitoring | AWS CloudWatch |
| Alerting | AWS SNS |
| Networking | AWS VPC, Subnets, Security Groups |
| Configuration | AWS Launch Templates, User Data scripts |

---

## Project Structure

```
scalable-cloud-infrastructure-demo/
├── scripts/
│   ├── launch_template.sh       # EC2 user data bootstrap script
│   ├── create_alb.sh            # ALB provisioning script
│   └── setup_autoscaling.sh     # Auto Scaling Group configuration
├── monitoring/
│   ├── cloudwatch_alarms.sh     # CloudWatch alarm definitions
│   └── sns_setup.sh             # SNS topic and subscription setup
├── docs/
│   └── architecture.md          # Detailed architecture notes
└── README.md
```

---

## Setup & Deployment

### Prerequisites
- AWS CLI configured with appropriate IAM permissions
- An existing VPC with at least 2 public subnets across different AZs

### Steps

**1. Deploy the Launch Template**
```bash
bash scripts/launch_template.sh
```

**2. Create the Application Load Balancer**
```bash
bash scripts/create_alb.sh --vpc-id <your-vpc-id> --subnets <subnet-1,subnet-2>
```

**3. Configure Auto Scaling**
```bash
bash scripts/setup_autoscaling.sh --min 2 --max 6 --desired 2
```

**4. Set Up Monitoring**
```bash
bash scripts/cloudwatch_alarms.sh
bash scripts/sns_setup.sh --email your@email.com
```

---

## Scaling Policy

| Metric | Scale Out Trigger | Scale In Trigger |
|---|---|---|
| CPU Utilization | > 70% for 2 periods | < 30% for 5 periods |
| Healthy Host Count | < 2 hosts | - |

---

## Key Concepts Demonstrated

- **Horizontal scaling** vs vertical scaling tradeoffs
- **Health check** configuration at ALB and Auto Scaling levels
- **Cooldown periods** to prevent scaling thrash
- **Cross-AZ load balancing** for fault tolerance
- **Least-privilege IAM** roles for EC2 instances

---

## Author

**Toby Orisadare** — AWS Cloud Practitioner | [LinkedIn](https://linkedin.com/in/toby-orisadare) | [GitHub](https://github.com/tobyno35)
