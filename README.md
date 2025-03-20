# Wazuh Monitoring Setup
# Overview
This project sets up a secure, scalable infrastructure for deploying Wazuh, using Terraform to provision AWS resources, an installation script to configure an EC2 instance, and a Docker Compose file for managing Wazuh services. The setup is designed to adhere to cloud security best practices and enables effective monitoring and management.

**Deliverables**:
- Terraform Code: Provisions the AWS infrastructure, including VPC, subnets, routing tables, NAT Gateway, EC2 instance, IAM roles, and S3 bucket for Terraform state management.
- Installation Script: Automates the setup of Docker, Docker Compose, and Wazuh deployment on the EC2 instance.
- Docker Compose File: Configures Wazuh services (Manager, Indexer, Dashboard) with persistence and secure communication.
- README Documentation: Comprehensive setup and usage guide.

# Infrastructure Setup
**Prerequisites:**
- Install Terraform on your local machine.
- Ensure AWS CLI is installed and configured with appropriate permissions.

**Steps**:
```bash
sudo adduser devops
sudo usermod -aG sudo devops
```





