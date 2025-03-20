# Wazuh Monitoring Setup

# Overview
This project sets up a secure, scalable infrastructure for deploying Wazuh, using Terraform to provision AWS resources, an installation script to configure an EC2 instance, and a Docker Compose file for managing Wazuh services. The setup is designed to adhere to cloud security best practices and enables effective monitoring and management.

**Prerequisites:**
- Create key pair in your aws account for ec2 instance with name assessement.pem, otherwise terraform will fail.
- Create the s3 bucket for terraform state manually in aws otherwise backend wont initialize, terraform init command will fail.

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
cd assessement/terraform/
terraform init
terraform apply
```
**Confirm the following resources are created:**
- VPC with public and private subnets.
- Internet Gateway and NAT Gateway for routing.
- EC2 instance in the private subnet.
- Security groups with minimal access.
- IAM roles for EC2 and SSM.

# Configuration Setup

**Prerequisites:**
- Ensure SSH access is available using the private key file for the EC2 instance.
- Confirm the EC2 instance is running successfully

**Steps**:
```bash
ssh -i assessement.pem ec2-user@<instance-ip>
bash assessement/scripts/setup.sh
```
**What the Script Does:**
- Installs Docker and Docker Compose.
- Pulls the official Wazuh Docker repository.
- Sets up certificates for secure communication.
- Deploys Wazuh services using Docker Compose.

# Access Information

**Wazuh Services:**
- Dashboard: Accessible at https://<INSTANCE_PUBLIC_IP>:443.
- Manager API: Available at https://<INSTANCE_PRIVATE_IP>:55000.

**Logs**:
- System logs are stored in /var/log/.
- Wazuh-specific logs are located in /opt/wazuh.
  
**Credentials:**
- API Username: Admin
- API Password: Instance ID of ec2 instance with I in caps

# Cleanup

**Steps:**
```bash
cd terraform/
terraform destroy
```

# Best Practice Followed
  
**Security:**
- EC2 instance is in a private subnet, accessible only via SSM.
- All resources are tagged for easy identification.
- IAM roles are used instead of hardcoded credentials.

**Efficiency:**
- Docker Compose enables multi-container orchestration with persistent data storage.
- Automated scripting reduces manual setup effort.

**Logging and Monitoring:**
- Configured basic logging for system and application-level events.
- Wazuh services provide extensive monitoring capabilities.





