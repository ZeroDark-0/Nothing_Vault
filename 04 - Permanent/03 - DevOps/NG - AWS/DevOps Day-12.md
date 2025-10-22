---
date: 2025-06-29T10:50
tags: []
---

# Virtual Private Cloud (VPC)

It's a **private, isolated section of a cloud provider’s network** where you can launch and manage cloud resources like virtual machines.                     

# Cloud 9 AWS

**cloud-based Integrated Development Environment (IDE)** provided by Amazon Web Services
# How to Run Terraform on AWS

```bash
sudo yum update -y

# Install AWS CLI
sudo yum install -y awscli

# Install unzip and curl for Terraform
sudo yum install -y unzip curl

# Install Terraform (adjust version if needed)
curl -O https://releases.hashicorp.com/terraform/1.5.8/terraform_1.5.8_linux_amd64.zip
unzip terraform_1.5.8_linux_amd64.zip
sudo mv terraform /usr/local/bin/

# Verify
terraform version
aws --version
```

Then AWS config

```bash 
aws configure
# Use region: eu-north-1
# Set output format to json or table
```

Set Up Project Directory

```bash
mkdir terraform-aws-project && cd terraform-aws-project
touch main.tf
```

After this upload the .pem file on the AWS

now the main.tf

```bash
provider "aws" {
  region = "eu-north-1"          # change the region
}

# Get latest Amazon Linux 2 AMI
data "aws_ami" "al2" {
  most_recent = true
  owners      = ["amazon"]

  filter {
    name   = "name"
    values = ["amzn2-ami-hvm-*-x86_64-gp2"]
  }
}

# Create a VPC
resource "aws_vpc" "main_vpc" {
  cidr_block = "10.0.0.0/16"
  tags = {
    Name = "devops-vpc"
  }
}

# Create a public subnet
resource "aws_subnet" "public" {
  vpc_id                  = aws_vpc.main_vpc.id
  cidr_block              = "10.0.1.0/24"
  availability_zone       = "eu-north-1b"   # change the region
  map_public_ip_on_launch = true

  tags = {
    Name = "public-subnet"
  }
}

# Create an internet gateway
resource "aws_internet_gateway" "igw" {
  vpc_id = aws_vpc.main_vpc.id

  tags = {
    Name = "main-igw"
  }
}

# Route table for public subnet
resource "aws_route_table" "public_rt" {
  vpc_id = aws_vpc.main_vpc.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.igw.id
  }

  tags = {
    Name = "public-route-table"
  }
}

# Associate route table with public subnet
resource "aws_route_table_association" "public_assoc" {
  subnet_id      = aws_subnet.public.id
  route_table_id = aws_route_table.public_rt.id
}

# Security Group: Allow SSH and HTTP
resource "aws_security_group" "web_sg" {
  name        = "web-sg"
  description = "Allow SSH and HTTP"
  vpc_id      = aws_vpc.main_vpc.id

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name = "web-sg"
  }
}

# Launch EC2 Instance in public subnet
resource "aws_instance" "web" {
  ami                         = data.aws_ami.al2.id
  instance_type               = "t3.micro"
  subnet_id                   = aws_subnet.public.id
  associate_public_ip_address = true
  vpc_security_group_ids      = [aws_security_group.web_sg.id]
  key_name                    = "terra_ec2"  # key name (not filename)

  user_data = <<-EOF
              #!/bin/bash
              yum update -y
              yum install -y httpd
              echo "<h1>Hello from Terraform in EU North!</h1>" > /var/www/html/index.html
              systemctl start httpd
              systemctl enable httpd
              EOF

  tags = {
    Name = "web-instance"
  }
}
output "instance_public_ip" {
  value = aws_instance.web.public_ip
}
```

After this 
```bash
terraform init
terraform plan -out plan.out
terraform apply plan.out
```
and 
```bash
terraform apply -auto-approve
```

And finally to get the IP 
`terraform output instance_public_ip`


You can see the result on 
`http://<public-ip>`
