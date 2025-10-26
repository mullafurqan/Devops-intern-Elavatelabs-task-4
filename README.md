# Task-04: Infrastructure as Code (IaC) using Terraform with Docker

## Objective
Provision and manage an Nginx Docker container using Terraform.

## Tools Used
- Terraform
- Docker Desktop

## Project Description
This project demonstrates automation of infrastructure provisioning using Terraform. It pulls the Nginx Docker image and deploys a container running on port 8080.

## File Structure
Task-04/
|
└── main.tf      # Terraform configuration file

## Terraform Configuration
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name = "nginx:latest"
}

resource "docker_container" "nginx_container" {
  name  = "nginx_container"
  image = docker_image.nginx.image_id

  ports {
    internal = 80
    external = 8080
  }
}

## Commands to Execute

### Step 1: Initialize Terraform
terraform init

### Step 2: Validate execution plan
terraform plan

### Step 3: Apply configuration (Deploy container)
terraform apply
(then type yes)

### Step 4: Verify running container
docker ps

Open in browser:
http://localhost:8080

## State Management Commands
terraform state list
terraform state show docker_container.nginx_container

## Destroy Infrastructure
terraform destroy
(then type yes)

## Expected Output Screenshots (for submission)
1. terraform init output
2. terraform apply output
3. docker ps result
4. Running Nginx page in browser
5. terraform destroy output

## Outcome
Successfully deployed and managed a Docker container using Terraform with complete lifecycle automation.
