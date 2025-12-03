# Complete DevOps Engineering Roadmap: Zero to Job-Ready

**Duration:** 16-20 weeks (4-5 months) | **Target Role:** Junior DevOps Engineer
**Skill Level:** Beginner → Intermediate → Job-Ready

---

## Table of Contents
1. [Roadmap Overview](#roadmap-overview)
2. [Weekly Breakdown](#weekly-breakdown)
3. [Main Projects](#main-projects)
4. [Capstone Project](#capstone-project)
5. [Certifications](#certifications)
6. [Job-Readiness Checklist](#job-readiness-checklist)
7. [Interview Preparation](#interview-preparation)

---

## Roadmap Overview

This roadmap is structured in 4 phases:
- **Phase 1 (Weeks 1-4):** Foundations - Linux, Git, Bash
- **Phase 2 (Weeks 5-8):** Containerization - Docker, Docker Compose
- **Phase 3 (Weeks 9-14):** Orchestration & Infrastructure - Kubernetes, Terraform, AWS
- **Phase 4 (Weeks 15-20):** Automation & Observability - CI/CD, Monitoring, GitOps

---

## Weekly Breakdown

### PHASE 1: FOUNDATIONS (Weeks 1-4)

#### **Week 1: Linux Fundamentals & System Administration**

**Topics to Learn:**
- Linux distributions (Ubuntu, CentOS concepts)
- File system structure (`/`, `/home`, `/etc`, `/var`, `/usr`)
- User & permission management (users, groups, `chmod`, `chown`)
- File operations (ls, cd, pwd, mkdir, rm, cp, mv, find, grep)
- Process management (ps, top, kill, systemctl, journalctl)
- Package managers (apt, yum)
- File editors (nano, vi/vim)

**Tools & Concepts:**
- Ubuntu 22.04 LTS (or latest stable)
- SSH key generation and authentication
- sudo privileges and sudoers file
- Environment variables and PATH

**Hands-On Tasks:**
1. Set up a Linux virtual machine (VirtualBox or WSL on Windows)
2. Navigate the file system using commands
3. Create 5 users with different permission levels
4. Practice finding files and filtering output with grep
5. Manage running processes and services

**Micro-Project: Linux Admin Toolkit**
- Create a directory structure for a project
- Set correct permissions (user read/write, group read-only, others none)
- Write down 10 essential Linux commands you'll use daily
- Document your own Linux cheat sheet

**End-of-Week Outcome:**
✓ Can navigate Linux file system confidently
✓ Understand permissions and user management
✓ Comfortable using command-line interface
✓ Know how to manage services and processes

---

#### **Week 2: Advanced Linux & Networking Basics**

**Topics to Learn:**
- Network interfaces and IP addressing (IPv4, IPv6 basics)
- Network tools (ifconfig, ip, netstat, ss, ping, traceroute, nslookup, dig)
- Ports and services (well-known ports: 22 SSH, 80 HTTP, 443 HTTPS, 3306 MySQL, 5432 PostgreSQL)
- DNS concepts (A records, CNAME, MX)
- Firewalls (ufw on Ubuntu, firewalld on CentOS)
- SSH configuration and key-based authentication
- scp and rsync for file transfer
- Network troubleshooting fundamentals
- Disk management (fdisk, lsblk, mount, umount)
- Log files and log analysis (/var/log, tail, less)

**Tools & Concepts:**
- Networking OSI model (basic understanding)
- CIDR notation
- SSH keys (RSA, ED25519)
- Firewall rules

**Hands-On Tasks:**
1. Configure network interfaces on Linux VM
2. Set up SSH key-pair authentication
3. Create firewall rules to allow specific ports
4. Use netstat/ss to monitor open connections
5. Practice file transfer using scp and rsync
6. Analyze system logs to understand events
7. Set up DNS resolution locally

**Micro-Project: Network Diagnostics Script**
- Create a Bash script that:
  - Checks if a server is reachable (ping)
  - Performs DNS lookup
  - Shows open ports on the system
  - Displays current network interfaces
  - Generates a network status report

**End-of-Week Outcome:**
✓ Understand networking fundamentals
✓ Can configure network settings and troubleshoot connectivity
✓ Know how to use SSH for secure access
✓ Familiar with log analysis
✓ Basic firewall configuration skills

---

#### **Week 3: Bash Scripting & Automation**

**Topics to Learn:**
- Bash script structure and shebang
- Variables and variable expansion
- Input/output redirection (>, >>, <, 2>&1, pipe |)
- Conditionals (if-else, case statements)
- Loops (for, while, until)
- Functions and function parameters
- String manipulation and text processing (sed, awk)
- Regular expressions (grep patterns, sed patterns)
- Arrays and associative arrays
- Error handling and exit codes
- Command substitution ($() and backticks)
- Script debugging (bash -x, set -e, set -u)

**Tools & Concepts:**
- Text processing: grep, sed, awk, cut, sort, uniq
- Command chaining and pipes
- Cron jobs for scheduling
- Script permissions and executable files

**Hands-On Tasks:**
1. Write a script that checks system resource usage (CPU, memory, disk)
2. Create a script to backup files with timestamps
3. Write a monitoring script that alerts if disk usage exceeds 80%
4. Create a script to parse and extract data from log files
5. Write a deployment script that handles git pull, restart service

**Micro-Project: Server Health Monitoring Script**
Create a comprehensive Bash script that:
- Checks CPU, memory, and disk usage
- Monitors if critical services are running (sshd, nginx, etc.)
- Checks if ports are listening
- Generates a timestamp-based report
- Optionally sends alerts via email if thresholds are exceeded
- Runs this script daily via cron

**End-of-Week Outcome:**
✓ Can write functional Bash scripts
✓ Automate repetitive system tasks
✓ Process logs and extract data
✓ Understand scheduling with cron
✓ Debug shell scripts effectively

---

#### **Week 4: Version Control - Git & GitHub**

**Topics to Learn:**
- Git fundamentals (repositories, commits, history)
- Local git workflow (git init, add, commit, log, diff)
- Branching strategy (git branch, checkout, merge)
- Remote repositories and GitHub
- SSH keys for GitHub authentication
- Pull requests and code review workflow
- Merge conflicts and resolution
- .gitignore file management
- Git best practices (commit messages, atomic commits)
- GitHub: Issues, Wiki, Projects, Actions overview
- Collaborative workflow (fork, clone, contribute)

**Tools & Concepts:**
- Git branching models (Git Flow, GitHub Flow)
- Conventional commit messages
- Tags and releases
- GitHub Personal Access Tokens

**Hands-On Tasks:**
1. Initialize a local repository and make commits
2. Create branches and merge them
3. Create a GitHub account and push code
4. Set up SSH keys for GitHub
5. Resolve a merge conflict
6. Create a pull request and get feedback
7. Practice with collaborative projects

**Micro-Project: Personal DevOps Notes Repository**
- Create a GitHub repository
- Organize your learning notes by topic (Linux, Bash, Docker, etc.)
- Use branches for different features
- Create documentation with markdown
- Practice pull requests by updating from multiple branches
- Add meaningful commit messages
- Create a README with project description

**End-of-Week Outcome:**
✓ Proficient with Git and GitHub
✓ Understand branching and merging
✓ Can collaborate using pull requests
✓ Know how to write meaningful commit messages
✓ Ready to contribute to open-source projects

---

### PHASE 2: CONTAINERIZATION (Weeks 5-8)

#### **Week 5: Docker Fundamentals**

**Topics to Learn:**
- What is containerization and why it matters
- Docker architecture (Docker daemon, CLI, images, containers)
- Docker images and registries (Docker Hub)
- Image layers and filesystem
- Containers vs virtual machines
- Docker installation and setup
- Docker basic commands (run, pull, push, ps, logs, exec, stop, rm)
- Container lifecycle (create, start, stop, remove)
- Port mapping and network basics
- Volume mounting and data persistence
- Environment variables in containers
- Resource limits and constraints

**Tools & Concepts:**
- Docker Hub registry
- Image naming conventions
- Container vs host filesystem
- Port binding

**Hands-On Tasks:**
1. Install Docker on your Linux system
2. Pull and run pre-built images (nginx, postgres, mysql)
3. Map ports and access services
4. Mount volumes and persist data
5. Set environment variables for containers
6. View container logs and debug issues
7. Stop and remove containers

**Micro-Project: Multi-Container Local Environment**
- Run 3 containers:
  - Nginx web server
  - PostgreSQL database
  - Redis cache
- Map ports correctly
- Mount volumes for data persistence
- Connect to containers using docker exec
- View logs and verify all are running

**End-of-Week Outcome:**
✓ Understand containerization benefits
✓ Can run and manage Docker containers
✓ Know image basics and registries
✓ Comfortable with port mapping and volumes
✓ Can troubleshoot container issues

---

#### **Week 6: Dockerfile & Custom Images**

**Topics to Learn:**
- Dockerfile syntax and structure
- Base images and choosing the right one (alpine, debian, ubuntu, scratch)
- Dockerfile instructions (FROM, RUN, COPY, ADD, EXPOSE, ENV, CMD, ENTRYPOINT)
- Build context and .dockerignore
- Multi-stage builds for optimization
- Layers and caching in Docker builds
- Best practices for Dockerfile
- Running commands and arguments
- Building images (docker build)
- Tagging images
- Image size optimization
- Security best practices (non-root users, minimal base images)

**Tools & Concepts:**
- Dockerfile best practices
- Image tagging conventions (versioning, latest tag)
- Registry authentication and pushing images
- Docker image inspection

**Hands-On Tasks:**
1. Write a Dockerfile for a Node.js application
2. Write a Dockerfile for a Python Flask app
3. Create multi-stage builds to reduce image size
4. Build images with different base images
5. Tag and push images to Docker Hub
6. Create .dockerignore to exclude unnecessary files
7. Practice building and rebuilding with caching

**Micro-Project: Dockerize a Simple Application**
Create Dockerfiles for:
1. A simple Node.js web server (Express)
2. A Python Flask API
3. A static HTML website (Nginx)

For each:
- Write optimized Dockerfile
- Build the image
- Run the container successfully
- Document the steps
- Push to Docker Hub
- Show how to run it locally

**End-of-Week Outcome:**
✓ Can write custom Dockerfiles
✓ Understand image layers and optimization
✓ Apply Docker best practices
✓ Create and push images to registries
✓ Know multi-stage build advantages

---

#### **Week 7: Docker Compose & Multi-Container Applications**

**Topics to Learn:**
- Docker Compose basics and purpose
- docker-compose.yml file structure
- Services, networks, and volumes in Compose
- Environment variables and .env files
- Build context in Compose
- Container dependencies and startup order
- Scaling services (replicas)
- Networking between containers
- Compose commands (up, down, logs, exec, build)
- Overrides and multiple compose files
- Health checks in Compose
- Resource limits and constraints

**Tools & Concepts:**
- YAML syntax basics
- Service networking (internal DNS)
- Named volumes vs bind mounts
- Environment file management

**Hands-On Tasks:**
1. Create a compose file for a web app + database
2. Set up services to communicate with each other
3. Use environment variables from .env file
4. Define volumes for data persistence
5. Scale a service to multiple replicas
6. View logs from all containers
7. Test networking between containers

**Micro-Project: Full Stack Application with Docker Compose**
Create a docker-compose.yml for a complete application:
- Frontend: Node.js (React/Vue) on port 3000
- Backend: Python Flask/Django API on port 5000
- Database: PostgreSQL
- Cache: Redis
- Web server: Nginx (reverse proxy on port 80)

Requirements:
- Containers communicate internally
- Data persists in volumes
- Environment variables for all configurations
- Health checks for services
- Clear documentation on how to run

**End-of-Week Outcome:**
✓ Can orchestrate multi-container applications
✓ Understand service networking and communication
✓ Manage volumes and environment variables
✓ Design scalable local environments
✓ Ready for container orchestration

---

#### **Week 8: Container Registry & Image Management**

**Topics to Learn:**
- Docker Hub registry setup and authentication
- Private registry options (AWS ECR, Azure ACR, GitLab Registry)
- Image naming and versioning best practices
- Pushing and pulling from registries
- Image signing and verification
- Container image scanning for vulnerabilities
- Image cleanup and garbage collection
- Container image best practices summary
- Building CI-ready images
- Image security scanning tools (Trivy, Snyk)

**Tools & Concepts:**
- Registry authentication methods
- Image tags and semantic versioning
- Vulnerability scanning
- Private repositories

**Hands-On Tasks:**
1. Set up AWS ECR account
2. Push images to ECR
3. Pull images from ECR
4. Scan images for vulnerabilities
5. Test image with different tags
6. Clean up old images and layers
7. Set up GitHub Container Registry

**Micro-Project: Container Image Pipeline**
- Build a Docker image for a simple application
- Scan it for vulnerabilities
- Tag it with version numbers
- Push to ECR or Docker Hub
- Create documentation on how to use the image
- Set up automatic cleanup of old images

**End-of-Week Outcome:**
✓ Manage container images professionally
✓ Understand registry concepts
✓ Can scan images for security issues
✓ Apply versioning best practices
✓ Ready for CI/CD integration

---

### PHASE 3: ORCHESTRATION & INFRASTRUCTURE (Weeks 9-14)

#### **Week 9: Kubernetes Fundamentals**

**Topics to Learn:**
- Why Kubernetes (container orchestration)
- Kubernetes architecture (control plane, worker nodes)
- Key concepts: Pods, Deployments, Services, Namespaces, ConfigMaps, Secrets
- kubectl command-line tool
- Kubeconfig and cluster access
- Pod basics and Pod lifecycle
- Labels and selectors
- Replication and scaling
- Service types (ClusterIP, NodePort, LoadBalancer)
- Ingress basics
- YAML manifests structure
- Rolling updates and rollback

**Tools & Concepts:**
- Local Kubernetes (minikube, Docker Desktop Kubernetes, kind)
- kubectl commands and syntax
- Resource definitions in YAML
- Kubernetes namespaces

**Hands-On Tasks:**
1. Set up local Kubernetes cluster (minikube)
2. Create and deploy Pods manually
3. Expose services and access them
4. Create Deployments for scalable applications
5. Scale deployments up and down
6. Perform rolling updates
7. Access logs and debug issues

**Micro-Project: Deploy Simple Application to Kubernetes**
- Dockerize a Node.js application
- Create Kubernetes manifests:
  - Deployment (3 replicas)
  - Service (expose via NodePort)
  - ConfigMap (environment variables)
  - Secret (API keys)
- Deploy to minikube
- Scale the deployment
- Update the image and perform rolling update
- Test access from your machine

**End-of-Week Outcome:**
✓ Understand Kubernetes architecture
✓ Can deploy and manage Pods
✓ Create Deployments with replicas
✓ Expose services and access applications
✓ Comfortable with kubectl commands

---

#### **Week 10: Kubernetes Advanced - Networking, Storage, ConfigMaps, Secrets**

**Topics to Learn:**
- Kubernetes networking model
- Service discovery and DNS
- NetworkPolicies for traffic control
- Ingress for external access
- Persistent Volumes (PV) and Persistent Volume Claims (PVC)
- Storage classes
- ConfigMaps for configuration management
- Secrets for sensitive data (types: Opaque, docker-registry, tls)
- Resource quotas and limits
- Probes: liveness, readiness, startup
- StatefulSets for stateful applications

**Tools & Concepts:**
- Service mesh concepts (basic understanding)
- CNI (Container Network Interface)
- Ingress controllers (Nginx, Traefik)
- Secret management best practices

**Hands-On Tasks:**
1. Create and manage ConfigMaps
2. Create and manage Secrets
3. Mount ConfigMaps as volumes
4. Define resource limits and requests
5. Set up liveness and readiness probes
6. Create Persistent Volumes and Claims
7. Configure Ingress for external access
8. Implement network policies

**Micro-Project: Complete Application Deployment**
Deploy a multi-tier application:
- Frontend pod with Deployment
- Backend API with Deployment
- PostgreSQL StatefulSet
- Redis for caching
- ConfigMap for configuration
- Secrets for database credentials
- Persistent volumes for data
- Ingress to expose frontend
- Resource limits defined
- Health checks configured

**End-of-Week Outcome:**
✓ Advanced Pod configuration
✓ Manage persistent data in Kubernetes
✓ Handle configuration and secrets
✓ Understand networking and Ingress
✓ Create production-like deployments

---

#### **Week 11: Helm & Package Management**

**Topics to Learn:**
- What is Helm and why it matters
- Helm architecture (Charts, Releases, Repositories)
- Chart structure and components
- values.yaml and customization
- Templates and templating syntax
- Helm commands (install, upgrade, rollback, list, delete)
- Helm repositories and searching charts
- Creating custom Helm charts
- Helm hooks and advanced features
- Best practices for Helm charts
- Dependency management between charts

**Tools & Concepts:**
- Chart repositories (Artifact Hub, Bitnami)
- Values overrides and precedence
- Chart versioning and semantic versioning

**Hands-On Tasks:**
1. Search and install a Helm chart from repository
2. Override values during installation
3. Upgrade a release
4. Rollback to previous release
5. Create a custom Helm chart for your application
6. Use templates for configuration
7. Manage chart dependencies

**Micro-Project: Create Helm Chart for Application**
Create a Helm chart that:
- Packages the Node.js + PostgreSQL application from Week 10
- Defines customizable values for replicas, resources, image tags
- Uses templates for all manifests
- Includes README with usage instructions
- Supports multiple environments (dev, staging, prod)
- Demonstrates override capabilities
- Can be installed with single helm install command

**End-of-Week Outcome:**
✓ Understand Helm concepts and usage
✓ Can install and customize charts
✓ Create custom Helm charts
✓ Manage application packaging
✓ Ready for GitOps and infrastructure automation

---

#### **Week 12: AWS Fundamentals for DevOps**

**Topics to Learn:**
- AWS core services overview
- Regions, Availability Zones, edge locations
- EC2: Instance types, AMI, security groups, key pairs
- VPC: Subnets, route tables, NAT, IGW, security groups
- IAM: Users, roles, policies, permissions
- RDS: Managed databases, backups, multi-AZ
- S3: Object storage, versioning, lifecycle policies
- CloudWatch: Metrics, logs, alarms
- Auto Scaling: ASGs and scaling policies
- Load Balancing: ALB, NLB concepts
- CloudFormation basics
- IAM best practices and principle of least privilege

**Tools & Concepts:**
- AWS free tier services
- AWS CLI basics
- Security groups and network ACLs
- IAM best practices

**Hands-On Tasks:**
1. Create EC2 instances and connect via SSH
2. Configure security groups for web traffic
3. Set up VPC with public/private subnets
4. Launch RDS database instance
5. Create S3 bucket and upload objects
6. Configure Auto Scaling group
7. Set up basic CloudWatch monitoring
8. Create IAM user with restricted permissions

**Micro-Project: AWS Infrastructure Setup**
Create basic infrastructure:
- Create custom VPC with public and private subnets
- Launch EC2 instance in public subnet
- Launch PostgreSQL RDS in private subnet
- Create S3 bucket for application data
- Configure security groups for communication
- Create IAM roles for EC2
- Set up CloudWatch alarms
- Document infrastructure decisions

**End-of-Week Outcome:**
✓ Understand AWS core services
✓ Can create basic infrastructure
✓ Know security best practices
✓ Comfortable with AWS console and CLI
✓ Ready for Infrastructure as Code

---

#### **Week 13: Infrastructure as Code - Terraform Fundamentals**

**Topics to Learn:**
- What is IaC and benefits
- Terraform basics: HCL, state, providers
- Terraform workflow: init, plan, apply, destroy
- Resources, data sources, variables
- Outputs and locals
- Modules and reusability
- State management and remote state
- Backends (S3, Terraform Cloud)
- Variable files and terraform.tfvars
- For loops and conditionals in Terraform
- Terraform fmt, validate, and fmt commands
- Tagging and naming conventions

**Tools & Concepts:**
- HCL (HashiCorp Configuration Language)
- Terraform state files and locking
- Provider configuration
- Module registry

**Hands-On Tasks:**
1. Initialize Terraform project
2. Write Terraform code for AWS VPC
3. Create EC2 instances with Terraform
4. Define variables and outputs
5. Use modules for reusable components
6. Manage state locally and remotely
7. Plan and apply changes
8. Destroy infrastructure safely

**Micro-Project: Terraform EC2 Module**
Create reusable Terraform module:
- Module for launching EC2 instance with:
  - Configurable instance type (via variable)
  - Auto-assigned security group
  - EBS volume size as variable
  - Tags for identification
  - Output: instance IP, instance ID, security group ID
- Create main.tf that uses module multiple times
- Define terraform.tfvars with values
- Generate documentation
- Add variable validation

**End-of-Week Outcome:**
✓ Write Terraform code for infrastructure
✓ Understand state management
✓ Create and use modules
✓ Manage infrastructure as code
✓ Ready for CI/CD deployment automation

---

#### **Week 14: Advanced Terraform & AWS Integration**

**Topics to Learn:**
- Terraform workspaces for environment management
- Complex module structures
- Dynamic blocks and for_each loops
- Terraform functions (merge, lookup, file, etc.)
- Error handling in Terraform
- Provisioners and when to use them
- Data sources for referencing existing resources
- State migration and upgrades
- Terraform best practices (DRY, naming, organization)
- Integrating with AWS Services (CodeDeploy, CodeBuild)
- Security best practices (secrets management, IAM policies)

**Tools & Concepts:**
- Terraform workspaces
- aws_instance vs aws_launch_template
- Auto Scaling with Terraform
- Load Balancer configuration in Terraform

**Hands-On Tasks:**
1. Create multi-environment setup (dev, staging, prod)
2. Use workspaces for different environments
3. Implement dynamic blocks for scalable config
4. Use data sources to reference existing resources
5. Create Auto Scaling group with Terraform
6. Configure ALB with target groups
7. Implement IAM roles and policies
8. Use variables for secrets (with best practices warning)

**Micro-Project: Complete AWS Infrastructure with Terraform**
Infrastructure for a scalable web application:
- VPC with public and private subnets
- Auto Scaling group with EC2 instances
- Application Load Balancer
- RDS PostgreSQL in private subnet
- S3 bucket for static assets
- CloudWatch monitoring
- IAM roles for EC2 and RDS
- Security groups properly configured
- Modules for reusability
- Multiple environments (dev, prod)
- Terraform outputs for app deployment

**End-of-Week Outcome:**
✓ Advanced Terraform patterns
✓ Multi-environment infrastructure
✓ Integrate with AWS services
✓ Production-ready IaC setup
✓ Infrastructure automation mastery

---

### PHASE 4: AUTOMATION & OBSERVABILITY (Weeks 15-20)

#### **Week 15: CI/CD Fundamentals - GitHub Actions**

**Topics to Learn:**
- What is CI/CD and why it matters
- GitHub Actions basics: workflows, jobs, steps, actions
- Workflow YAML syntax
- Triggers: push, pull_request, schedule
- Environment variables and secrets in GitHub
- Matrix builds for multiple configurations
- Caching dependencies
- Artifacts and artifact management
- Service containers (database, redis)
- Conditional execution
- Workflow status checks
- GitHub Actions marketplace
- Cost implications and optimization

**Tools & Concepts:**
- Workflow files location (.github/workflows)
- Runners: hosted vs self-hosted
- Actions: official, community, custom

**Hands-On Tasks:**
1. Create simple workflow that runs on push
2. Build and test Node.js application
3. Set up secrets for API keys
4. Create matrix build for multiple Node versions
5. Build and push Docker image to registry
6. Deploy to Kubernetes cluster
7. Run tests on pull requests
8. Set branch protection rules

**Micro-Project: Complete CI Pipeline**
Create GitHub Actions workflow that:
- Triggers on push to main and pull requests
- Runs tests (npm test)
- Builds Docker image
- Scans image for vulnerabilities
- Pushes to Docker Hub / ECR
- Deploys to Kubernetes
- Posts results as comments on PR
- Includes caching for dependencies

**End-of-Week Outcome:**
✓ Understand CI/CD concepts
✓ Create GitHub Actions workflows
✓ Automate testing and building
✓ Deploy Docker images automatically
✓ Implement continuous deployment

---

#### **Week 16: CI/CD Advanced - Jenkins & Deployment Pipelines**

**Topics to Learn:**
- Jenkins basics: Master/Agent architecture
- Jenkins setup and configuration
- Pipeline as code (Declarative and Scripted)
- Jenkinsfile structure
- Stages, steps, and parallel execution
- Jenkins variables and parameters
- Jenkins plugins and integrations
- Webhooks for automated triggers
- Build triggers: poll, webhook, downstream jobs
- Jenkins shared libraries (optional advanced)
- Credentials and secrets management
- Pipeline best practices
- Blue/Green and Canary deployments

**Tools & Concepts:**
- Declarative vs Scripted pipelines
- Jenkins shared libraries concept
- Webhook integration with GitHub
- Jenkins Kubernetes plugin

**Hands-On Tasks:**
1. Install and configure Jenkins
2. Create freestyle job
3. Convert to pipeline with Jenkinsfile
4. Set up GitHub webhook
5. Build and test on code push
6. Push image to registry
7. Deploy to Kubernetes
8. Implement failure notifications

**Micro-Project: Multi-Stage Jenkins Pipeline**
Create Jenkins pipeline with stages:
- Checkout code from GitHub
- Build Docker image
- Run tests inside container
- Scan image for vulnerabilities
- Push to registry
- Deploy to Kubernetes (dev environment)
- Run smoke tests
- Deploy to production (on approval)
- Rollback capability
- Notification on success/failure

**End-of-Week Outcome:**
✓ Jenkins setup and configuration
✓ Create complex pipelines
✓ Integrate with Git repositories
✓ Automate deployment process
✓ Multi-stage deployment patterns

---

#### **Week 17: Monitoring with Prometheus & Grafana**

**Topics to Learn:**
- Observability: Monitoring, Logging, Tracing
- Prometheus basics: Time-series database, scraping
- Prometheus metrics types (Counter, Gauge, Histogram, Summary)
- PromQL: Prometheus Query Language
- Exporters for different services
- Service discovery in Prometheus
- Alerting rules and AlertManager
- Grafana: Dashboard creation and visualization
- Data source configuration
- Dashboard templating and variables
- Alerting from Grafana
- Performance optimization

**Tools & Concepts:**
- Node Exporter for Linux servers
- Application instrumentation (Prometheus client libraries)
- Alert routing and grouping
- Dashboard best practices

**Hands-On Tasks:**
1. Install and configure Prometheus
2. Add targets to scrape
3. Write PromQL queries
4. Set up Node Exporter for Linux monitoring
5. Configure AlertManager
6. Create alert rules
7. Install and configure Grafana
8. Create monitoring dashboards
9. Set up alerts in Grafana

**Micro-Project: Complete Monitoring Stack**
Set up monitoring for Kubernetes cluster:
- Deploy Prometheus to Kubernetes
- Deploy Node Exporter on cluster nodes
- Deploy Grafana
- Create exporters for application metrics
- Create dashboards for:
  - Cluster health and resources
  - Application performance
  - Pod and container metrics
- Configure alerts for:
  - High CPU/memory usage
  - Pod restarts
  - API error rates
- Document key metrics and thresholds

**End-of-Week Outcome:**
✓ Monitor infrastructure with Prometheus
✓ Create effective dashboards
✓ Set up alerts
✓ Understand metrics-driven operations
✓ Ready for production observability

---

#### **Week 18: Logging with ELK Stack / OpenSearch**

**Topics to Learn:**
- Centralized logging benefits
- ELK Stack components: Elasticsearch, Logstash, Kibana
- OpenSearch as alternative
- Log collection strategies
- Logstash filters and processing
- Filebeat and other lightweight agents
- Index management and retention
- Kibana dashboards and visualizations
- Log searching and filtering (Kibana Query Language)
- Alerting on logs
- Performance and scaling considerations
- Log aggregation in Kubernetes

**Tools & Concepts:**
- Elasticsearch cluster concepts
- Index templates and lifecycle management
- Logstash pipeline configuration
- Filebeat modules

**Hands-On Tasks:**
1. Set up Elasticsearch cluster
2. Install and configure Logstash
3. Parse and filter logs
4. Send application logs to Elasticsearch
5. Create Kibana dashboards
6. Search and visualize logs
7. Set up log retention policies
8. Configure alerts based on logs

**Micro-Project: Centralized Logging for Kubernetes**
Implement logging for your Kubernetes application:
- Deploy Filebeat to collect container logs
- Send to Elasticsearch
- Create Kibana dashboards for:
  - Application errors and warnings
  - Request rates and latencies
  - Pod status changes
- Implement log retention (e.g., 30 days)
- Set up alerts for critical errors
- Create documentation for accessing logs

**End-of-Week Outcome:**
✓ Centralized logging infrastructure
✓ Process and filter logs
✓ Create actionable dashboards
✓ Alert on log-based events
✓ Production-grade logging platform

---

#### **Week 19: GitOps - ArgoCD & Infrastructure Management**

**Topics to Learn:**
- GitOps principles and benefits
- Declarative infrastructure
- Git as single source of truth
- ArgoCD basics and architecture
- ArgoCD Applications and Projects
- Helm integration with ArgoCD
- Kustomize and templating
- Sync strategies and automatic sync
- ArgoCD RBAC and multi-tenancy
- Notification and event handling
- Secret management in GitOps
- Disaster recovery with GitOps

**Tools & Concepts:**
- Application vs Application Set in ArgoCD
- Sync wave for ordered deployment
- Notification integrations (Slack, email)
- Secret encryption in Git

**Hands-On Tasks:**
1. Install ArgoCD in Kubernetes cluster
2. Create Git repository for infrastructure
3. Create ArgoCD Application from Helm chart
4. Configure auto-sync
5. Deploy updates via Git commit
6. Implement multi-environment setup
7. Configure notifications
8. Test disaster recovery (recreate from Git)

**Micro-Project: Complete GitOps Setup**
Implement GitOps for your application:
- GitHub repository with:
  - Helm charts in /helm directory
  - Kubernetes manifests (kustomized)
  - ArgoCD ApplicationSet for multiple environments
  - Secrets management strategy
- ArgoCD configured to:
  - Auto-sync on Git changes
  - Send notifications to Slack
  - Manage dev, staging, prod environments
- Document GitOps workflow
- Test full deployment cycle via Git

**End-of-Week Outcome:**
✓ Understand GitOps principles
✓ Implement GitOps with ArgoCD
✓ Git-driven infrastructure management
✓ Multi-environment deployment
✓ Disaster recovery automation

---

#### **Week 20: Capstone Project - End-to-End DevOps Pipeline**

**Topics to Integrate:**
All previous learning combined into production-grade system

**Capstone Project: Complete DevOps Pipeline**

**Project: Deploy a Production-Ready Microservices Application**

### Architecture Overview:
```
GitHub → GitHub Actions → ECR → Terraform (AWS) 
→ EKS Cluster → ArgoCD → Prometheus/Grafana + ELK Stack
```

### Components:

**1. Application Repository**
- Multiple microservices (Frontend, Backend API, Worker)
- Dockerfile for each service
- Helm charts for each service
- Configuration for all environments

**2. Infrastructure Repository**
- Terraform code for AWS infrastructure
- EKS cluster setup
- RDS database
- S3 buckets
- VPC, subnets, security groups
- IAM roles and policies

**3. GitOps Repository**
- ArgoCD ApplicationSets for dev/staging/prod
- Helm values for different environments
- Sealed secrets for sensitive data

**4. CI/CD Pipeline (GitHub Actions)**
- Build and test microservices
- Build Docker images
- Push to ECR
- Run security scans
- Deploy to dev environment automatically
- Optional approval for staging/prod

**5. Infrastructure Automation (Terraform)**
- Create EKS cluster
- RDS database
- CloudWatch monitoring
- Auto-scaling configuration

**6. Container Orchestration (Kubernetes/EKS)**
- Deployments for each microservice
- Horizontal Pod Autoscalers
- Service mesh concepts
- NetworkPolicies

**7. Observability**
- Prometheus scraping metrics
- Grafana dashboards for:
  - Cluster health
  - Application performance
  - Business metrics
- ELK Stack for centralized logging
- Alerts for critical issues

**8. GitOps Deployment (ArgoCD)**
- Automatic syncing from Git
- Multi-environment management
- Rollback capability

### Deliverables:

1. **Working Infrastructure**
   - Deployed on AWS EKS
   - Accessible via public endpoint
   - Monitoring active and alerts configured

2. **GitHub Repositories** (3 total)
   - Application code with CI/CD
   - Infrastructure as Terraform code
   - GitOps configurations

3. **Documentation**
   - Architecture diagram
   - Deployment process
   - How to handle incidents
   - Cost estimates

4. **Portfolio Evidence**
   - Screenshots of:
     - GitHub Actions workflow
     - Docker images in ECR
     - Kubernetes pods running
     - Grafana dashboards
     - Application access
   - Terraform plan/apply output

### Implementation Steps:

**Week 20a: Setup & Infrastructure (Days 1-3)**
1. Create AWS account and free tier resources
2. Write Terraform code for EKS cluster
3. Set up state management
4. Deploy infrastructure: `terraform apply`
5. Verify EKS cluster is running

**Week 20b: Containerization & Registry (Days 4-5)**
1. Create 2-3 simple microservices (Node.js, Python, etc.)
2. Write Dockerfiles for each
3. Build and test locally with Docker Compose
4. Create ECR repositories
5. Push images to ECR

**Week 20c: CI/CD Pipeline (Days 6-7)**
1. Create GitHub Actions workflow
2. Trigger on git push: build → test → scan → push to ECR
3. Deploy to dev environment
4. Test full pipeline with code change

**Week 20d: Kubernetes & GitOps (Days 8-9)**
1. Create Helm charts for each microservice
2. Set up ArgoCD in EKS cluster
3. Create Git repository for ArgoCD
4. Deploy via ArgoCD (not kubectl)
5. Test GitOps workflow via Git commit

**Week 20e: Monitoring & Logging (Days 10-11)**
1. Deploy Prometheus and Grafana
2. Configure metric collection
3. Create meaningful dashboards
4. Deploy ELK stack or use CloudWatch
5. Configure alerts

**Week 20f: Testing & Documentation (Day 12-13)**
1. Full deployment from scratch via Terraform
2. Test failure scenarios
3. Document everything
4. Create portfolio presentation

---

## Main Resume-Ready Projects

### Project 1: Docker Multi-Service Application

**Timeline:** Week 7 (can extend to Week 8)

**Description:** Create a complete microservices application running in Docker containers with Docker Compose.

**Architecture:**
```
┌─────────────┐      ┌──────────────┐      ┌───────────┐
│   Frontend  │─────→│   API Server │─────→│ Database  │
│  (React)    │      │   (Node.js)  │      │(Postgres) │
└─────────────┘      └──────────────┘      └───────────┘
     :3000                :5000                :5432
                      ┌──────────────┐
                      │    Redis     │
                      │   (Cache)    │
                      └──────────────┘
                          :6379
```

**What You'll Build:**
- React frontend (or HTML/CSS/JS)
- Node.js Express API
- PostgreSQL database
- Redis cache
- Nginx reverse proxy

**Expected Output:**
- docker-compose.yml with all services
- Dockerfiles for frontend and backend
- .env file for configuration
- docker-compose override for development
- README with setup instructions
- Accessible application at http://localhost

**Portfolio Value:**
- Shows containerization understanding
- Demonstrates multi-service orchestration
- Proves networking and volume knowledge
- Real-world application architecture

**Hands-On Tasks:**
1. Create React app (or use template)
2. Build API with data persistence
3. Write docker-compose for all services
4. Set up networking between containers
5. Implement health checks
6. Document with clear README

---

### Project 2: Kubernetes Multi-Tier Deployment

**Timeline:** Week 11-12 (Weeks 9-12 learning + building)

**Description:** Deploy a production-like multi-tier application on Kubernetes with Helm charts.

**Architecture:**
```
Internet
    ↓
┌──────────────┐
│    Ingress   │ (nginx-ingress)
└──────┬───────┘
       ↓
   ┌────────┐
   │Frontend│ (3 replicas)
   └────┬───┘
        ↓
   ┌────────┐
   │Backend │ (3 replicas)
   └────┬───┘
        ↓
┌──────────────┐
│  StatefulSet │ (PostgreSQL)
│ (1 instance) │
└──────────────┘
```

**What You'll Build:**
- Kubernetes Deployment for frontend (3 replicas)
- Kubernetes Deployment for backend API (3 replicas)
- Kubernetes StatefulSet for PostgreSQL
- Services to expose components
- Ingress for external access
- Persistent Volumes for database
- ConfigMaps and Secrets
- Helm chart packaging

**Expected Output:**
- helm/ directory with chart
- values-dev.yaml and values-prod.yaml
- Deployment that scales correctly
- Service discovery working
- Data persisted across pod restarts
- Accessible via ingress

**Portfolio Value:**
- Demonstrates orchestration skills
- Production-grade Kubernetes knowledge
- Helm chart creation ability
- Shows understanding of stateful vs stateless

**Hands-On Tasks:**
1. Create deployment manifests
2. Test locally with minikube
3. Package with Helm
4. Deploy to EKS or managed cluster
5. Verify pod communication
6. Test rolling updates
7. Document architecture

---

### Project 3: CI/CD Pipeline with GitHub Actions & Jenkins

**Timeline:** Week 15-16

**Description:** Automated pipeline that tests, builds, and deploys code on every push.

**Pipeline Stages:**
```
1. Trigger (git push)
   ↓
2. Checkout code
   ↓
3. Run tests
   ↓
4. Build Docker image
   ↓
5. Scan image for vulnerabilities
   ↓
6. Push to registry
   ↓
7. Deploy to dev (automatic)
   ↓
8. Deploy to staging (manual approval)
   ↓
9. Deploy to production (manual approval)
   ↓
10. Smoke tests
```

**What You'll Build:**
- GitHub Actions workflow (or Jenkins Jenkinsfile)
- Build Docker image
- Run tests (unit + integration)
- Security scanning (Trivy)
- Multi-environment deployment
- Approval gates for production

**Expected Output:**
- .github/workflows/pipeline.yml
- Automated builds on every commit
- Images pushed to ECR/Docker Hub
- Deployment to Kubernetes
- Failed builds block merge
- Deployment history visible

**Portfolio Value:**
- Critical DevOps skill
- Shows automation mindset
- End-to-end understanding
- Production deployment knowledge

**Hands-On Tasks:**
1. Create workflow file
2. Set up secrets for credentials
3. Write pipeline stages
4. Add approval requirements
5. Deploy to different environments
6. Add rollback capability
7. Create notifications

---

### Project 4: Infrastructure as Code with Terraform

**Timeline:** Week 13-14

**Description:** Complete infrastructure setup on AWS using Terraform.

**Infrastructure Components:**
```
AWS Account
  ├── VPC (10.0.0.0/16)
  │   ├── Public Subnet (10.0.1.0/24)
  │   │   └── NAT Gateway
  │   ├── Private Subnet (10.0.2.0/24)
  │   │   └── EC2 Instances
  │   └── Private Subnet (10.0.3.0/24)
  │       └── RDS Database
  ├── Application Load Balancer
  ├── Auto Scaling Group
  ├── RDS (PostgreSQL)
  ├── S3 (static assets)
  ├── CloudWatch (monitoring)
  └── IAM Roles & Policies
```

**What You'll Build:**
- VPC with public and private subnets
- NAT Gateway for private internet access
- EC2 instances with Auto Scaling
- Application Load Balancer
- RDS PostgreSQL
- S3 bucket
- CloudWatch monitoring
- IAM roles and policies

**Expected Output:**
- Terraform code organized in modules
- main.tf, variables.tf, outputs.tf
- terraform.tfvars for values
- Ability to deploy with: `terraform apply`
- Ability to destroy with: `terraform destroy`
- Infrastructure fully reproducible

**Portfolio Value:**
- Core DevOps infrastructure skill
- Shows automation and reproducibility
- Infrastructure management expertise
- Cost-aware infrastructure design

**Hands-On Tasks:**
1. Set up Terraform project structure
2. Create modules (vpc, ec2, rds, etc.)
3. Write resource definitions
4. Implement variable validation
5. Create comprehensive outputs
6. Add tagging strategy
7. Test destroy and recreate

---

## Capstone Project

### Full DevOps Pipeline: Zero to Production

**Duration:** Week 20 (13 days)

**Objective:** Design and deploy a complete end-to-end DevOps system that demonstrates all learned skills.

**Project Scope:**

**Application Components:**
- Frontend: React application (simple todo app or similar)
- Backend API: Node.js/Python REST API
- Database: PostgreSQL
- Cache: Redis
- Worker: Optional async job processor

**Complete Workflow:**

1. **Development (Day 1-2)**
   - Create simple microservices
   - Containerize each service
   - Test locally with Docker Compose

2. **Infrastructure (Day 3-4)**
   - Write Terraform for AWS EKS cluster
   - Create RDS database
   - Set up VPC and security groups
   - Deploy infrastructure

3. **Repository Setup (Day 5)**
   - Create GitHub repositories:
     - Application code (with CI/CD)
     - Infrastructure (Terraform)
     - GitOps (ArgoCD)
   - Organize with proper structure

4. **CI/CD Implementation (Day 6-7)**
   - Create GitHub Actions workflow
   - Build → Test → Scan → Push → Deploy
   - Multi-environment setup
   - Approval gates for production

5. **Container Registry (Day 8)**
   - Push images to AWS ECR
   - Verify accessibility
   - Document image naming

6. **Kubernetes Deployment (Day 9)**
   - Create Helm charts
   - Deploy to EKS
   - Verify pod communication
   - Test scaling

7. **GitOps Setup (Day 10)**
   - Install ArgoCD
   - Configure automatic syncing
   - Demonstrate Git-driven deployment
   - Test multi-environment

8. **Monitoring & Observability (Day 11)**
   - Deploy Prometheus
   - Create Grafana dashboards
   - Deploy ELK for logging
   - Configure alerts

9. **Testing & Documentation (Day 12-13)**
   - Full deployment test from scratch
   - Documentation of entire workflow
   - Create portfolio presentation

### Expected Final State:

```
✓ Application running on EKS
✓ Accessible via public URL
✓ Metrics visible in Grafana
✓ Logs in Elasticsearch
✓ Deployment via Git commit works
✓ Alerts configured and tested
✓ Multiple environments managed
✓ Infrastructure reproducible with Terraform
✓ CI/CD pipeline functioning
✓ Everything documented
```

### Portfolio Deliverables:

1. **GitHub Repositories**
   - Application with working CI/CD
   - Infrastructure as Terraform code
   - GitOps configurations
   - All publicly accessible

2. **Documentation**
   - Architecture diagram (draw.io)
   - Setup guide
   - Deployment process
   - Troubleshooting guide
   - Cost breakdown

3. **Screenshots**
   - Application running
   - GitHub Actions workflow success
   - Grafana dashboards
   - ArgoCD applications synced
   - CloudWatch logs

4. **Blog Post (Optional)**
   - "How I Built a Complete DevOps Pipeline"
   - Technical walkthrough
   - Lessons learned
   - Tools and technologies used

---

## Certifications

### Recommended Certification Path

**Note:** AWS is transitioning from SysOps Administrator to CloudOps Engineer (Sept 2025). Plan accordingly.

### Tier 1: Foundational (Weeks 8-10)

**AWS Cloud Practitioner (CLF-C02)**
- **When:** After Week 4-5
- **Cost:** $99
- **Duration:** 6 weeks preparation
- **Topics:** AWS basics, services overview, pricing, support
- **Exam Time:** 90 minutes
- **Passing Score:** 70%
- **Value:** Entry-level, builds foundation

**Why Take It:**
- Free tier knowledge required
- Required for other AWS certs
- Validates cloud fundamentals

### Tier 2: Associate Level (Weeks 11-14)

**AWS Certified CloudOps Engineer - Associate (COA-C02)**
- **When:** After Weeks 12-13
- **Previous Name:** SysOps Administrator - Associate (retiring Sept 2025)
- **Cost:** $150
- **Duration:** 8 weeks preparation
- **Topics:** Deployment, operations, monitoring, scaling, security
- **Exam Time:** 130 minutes
- **Passing Score:** 70%
- **Value:** DevOps operations focus

**Why Take It:**
- Directly relevant to DevOps Engineer role
- Validates deployment and operations skills
- High job demand (6,000+ LinkedIn listings)

**HashiCorp Certified: Terraform Associate (003)**
- **When:** After Weeks 13-14
- **Cost:** $70.50
- **Duration:** 4 weeks preparation
- **Topics:** HCL, state, modules, providers, best practices
- **Exam Time:** 60 minutes
- **Passing Score:** 70%
- **Value:** IaC expertise validation

**Why Take It:**
- Essential DevOps skill
- Terraform market dominance
- Straightforward exam format

### Tier 3: Advanced / Optional (Weeks 18-20)

**Certified Kubernetes Administrator (CKA)**
- **When:** After Week 11 (or after more practice)
- **Cost:** $395 (includes exam attempt)
- **Duration:** 8-12 weeks (serious preparation required)
- **Topics:** Cluster architecture, workload management, networking, storage, security, troubleshooting
- **Exam Time:** 120 minutes (practical, hands-on)
- **Passing Score:** 66%
- **Value:** High; marks Kubernetes expertise
- **Prerequisites:** Strong Kubernetes knowledge

**Why Take It:**
- Highly respected in industry
- Hands-on practical exam
- Career advancement significant
- "Kubernetes finally clicked" moment

**When to Attempt:** After Week 14-16 with additional practice

---

### Certification Timeline

```
Week 1-4: Prepare for AWS Cloud Practitioner
Week 4: Take AWS Cloud Practitioner ✓
        (50% discount on next AWS cert)

Week 8-12: Prepare for Terraform Associate
Week 12: Take Terraform Associate ✓

Week 11-14: Prepare for CloudOps Engineer
Week 14: Take CloudOps Engineer ✓

Week 15-20: (Optional) Prepare for CKA
Week 20+: Take CKA (or defer to after job)
```

### Certification Exam Discount Strategy

- **First AWS Cert:** $99 (Cloud Practitioner)
- **Remaining AWS Certs:** $150 × 0.5 = $75 (50% discount)

**Total Certification Cost:**
- Cloud Practitioner: $99
- CloudOps Engineer: $75 (with discount)
- Terraform Associate: $70.50
- **Total: ~$244.50** (budget $300-400 for study materials)

---

## Job-Readiness Checklist

### Skills Mastered

**Foundation Skills:**
- ✓ Linux administration (user, permissions, processes, services)
- ✓ Bash scripting and automation
- ✓ Git and GitHub workflows
- ✓ Networking basics (DNS, ports, SSH, firewalls)

**Containerization:**
- ✓ Docker image creation and optimization
- ✓ Multi-container orchestration with Docker Compose
- ✓ Container registry management
- ✓ Security scanning and best practices

**Kubernetes:**
- ✓ Pod deployment and management
- ✓ Deployments, StatefulSets, Services
- ✓ ConfigMaps and Secrets
- ✓ Networking and Ingress
- ✓ Helm chart creation and management
- ✓ Application scaling and health checks

**Infrastructure as Code:**
- ✓ Terraform HCL syntax
- ✓ AWS resource provisioning
- ✓ Modular IaC design
- ✓ State management
- ✓ Multi-environment setup

**Cloud (AWS):**
- ✓ VPC, subnets, security groups
- ✓ EC2, Auto Scaling, Load Balancing
- ✓ RDS, S3, basic IAM
- ✓ CloudWatch monitoring

**CI/CD & Automation:**
- ✓ GitHub Actions workflow creation
- ✓ Jenkins pipeline creation
- ✓ Docker image building and pushing
- ✓ Multi-stage deployment pipelines
- ✓ Testing automation

**Observability:**
- ✓ Prometheus metrics collection
- ✓ Grafana dashboard creation
- ✓ Alert configuration
- ✓ Centralized logging (ELK/OpenSearch)
- ✓ Log searching and analysis

**GitOps & Deployment:**
- ✓ ArgoCD setup and configuration
- ✓ Git-driven infrastructure management
- ✓ Multi-environment deployment

---

### Portfolio Checklist

**GitHub Repositories:**
- ✓ Application repository with CI/CD
- ✓ Infrastructure repository (Terraform)
- ✓ GitOps repository (ArgoCD)
- ✓ Learning notes/documentation repository
- ✓ At least 50+ commits across projects

**Projects Completed:**
- ✓ Docker Compose multi-service application
- ✓ Kubernetes Helm deployment
- ✓ CI/CD pipeline (GitHub Actions or Jenkins)
- ✓ Infrastructure as Code (Terraform AWS)
- ✓ Full capstone project

**Demonstrations:**
- ✓ Working application deployed on cloud
- ✓ Logs accessible in centralized logging
- ✓ Metrics visible in Grafana
- ✓ Deployment via Git commit (GitOps)

**Documentation:**
- ✓ README files for all projects
- ✓ Architecture diagrams
- ✓ Deployment guides
- ✓ Troubleshooting guides
- ✓ Setup instructions for each tool

---

### Job Titles to Target

Based on your portfolio and skills:

**Entry-Level Positions:**
- **Junior DevOps Engineer** (Primary Target)
- **DevOps Engineer (Entry-Level)**
- **Cloud Operations Engineer**
- **Infrastructure Engineer (Junior)**
- **Site Reliability Engineer (Junior SRE)**
- **Platform Engineer (Entry-Level)**
- **Cloud Support Engineer** (stepping stone)

**Geographic Salary Expectation (India):**
- **Mumbai/Bangalore:** ₹8-12 LPA
- **Hyderabad/Pune:** ₹7-10 LPA
- **Tier 2 cities:** ₹5.5-8 LPA

**Global Remote:**
- **USA:** $80K-120K
- **Europe:** €50K-80K
- **Australia:** $100K-150K AUD

---

## Interview Preparation

### Common Interview Questions & Answers

**1. "Tell us about a project you've built from scratch."**

**Structure Your Answer:**
- What problem it solved
- Technologies used (Docker, Kubernetes, Terraform, AWS, CI/CD)
- Your specific role and contributions
- Challenges faced and how you solved them
- Results and metrics

**Example Answer:**
"I built a complete CI/CD pipeline for a microservices application. The architecture included a Node.js frontend and Python API deployed on Kubernetes using Helm. I used GitHub Actions for CI, pushed Docker images to ECR, and deployed via ArgoCD for GitOps. When faced with slow CI times, I optimized Docker layer caching and parallelized tests, reducing pipeline time from 8 minutes to 3 minutes."

---

**2. "How would you deploy an application to production?"**

**What They're Testing:** End-to-end thinking

**Your Answer Should Cover:**
- Infrastructure setup (Terraform)
- Containerization (Docker)
- Orchestration (Kubernetes)
- CI/CD automation (GitHub Actions/Jenkins)
- Monitoring (Prometheus/Grafana)
- Logging (ELK/Elasticsearch)
- Rollback strategy

**Example Answer:**
"I'd start with infrastructure as code using Terraform to provision an EKS cluster on AWS with proper VPC, security groups, and RDS. The application would be containerized with Docker and deployed via Helm charts. I'd set up a CI/CD pipeline using GitHub Actions that automatically tests, builds, and pushes images on commits. For deployment, I'd use ArgoCD to sync from Git, ensuring GitOps principles. Monitoring would use Prometheus and Grafana, with ELK for centralized logging. I'd implement blue-green deployment for zero-downtime updates."

---

**3. "How do you handle secrets in your infrastructure?"**

**What They're Testing:** Security awareness

**Your Answer Should Include:**
- No secrets in code or config files
- Use Kubernetes Secrets or vaults
- Environment variables in CI/CD
- Secret scanning tools
- Rotation policies

**Example Answer:**
"I never commit secrets to repositories. In Kubernetes, I use Secrets objects and mount them as volumes. In CI/CD pipelines, I use GitHub Secrets for sensitive credentials. For production, I'd recommend HashiCorp Vault for secret management with rotation policies. I also use tools like git-secrets and TruffleHog to scan for accidental commits."

---

**4. "What monitoring do you implement?"**

**What They're Testing:** Observability understanding

**Your Answer Should Include:**
- Application metrics (requests, errors, latency)
- Infrastructure metrics (CPU, memory, disk)
- Business metrics
- Alerting thresholds
- Dashboard strategy

**Example Answer:**
"I use Prometheus for metrics collection with exporters for both application and infrastructure monitoring. Key metrics include request rate, error rate, latency (p50, p95, p99), and resource utilization. Grafana visualizes these with dashboards for different audiences—ops teams see infrastructure health, developers see application performance. I set up AlertManager for critical alerts (high error rate, pod restarts, etc.) and integrate with Slack for notifications."

---

**5. "How would you handle a scaling issue?"**

**What They're Testing:** Problem-solving and DevOps thinking

**Your Answer Should Cover:**
- Identifying the bottleneck (CPU, memory, network, database)
- Horizontal vs vertical scaling
- Auto-scaling configuration
- Database optimization
- Caching strategies

**Example Answer:**
"First, I'd monitor with Prometheus to identify whether it's the application, database, or infrastructure. For the application layer, I'd configure Kubernetes HPA (Horizontal Pod Autoscaler) to scale based on CPU/memory. For database bottlenecks, I'd consider read replicas, connection pooling, or query optimization. I'd also implement caching with Redis for frequently accessed data and use CDN for static content. Vertical scaling (larger nodes) is last resort due to cost."

---

**6. "Tell us about a failure and how you recovered."**

**What They're Testing:** Problem-solving, learning from mistakes

**Structure:**
- What failed and why
- Impact (downtime, users affected)
- Root cause analysis
- Solution implemented
- What you learned

**Example Answer:**
"We had a production incident where database connection pool exhausted due to a slow query. It caused application timeouts. I fixed it by implementing connection timeouts, adding query caching, and setting up alerts for connection pool usage. I also improved monitoring to catch similar issues early. From this, I learned the importance of load testing before production deployment and having circuit breakers for database queries."

---

**7. "What's your experience with Infrastructure as Code?"**

**What They're Testing:** IaC expertise

**Your Answer Should Include:**
- Terraform experience
- Module creation
- State management
- Version control for infrastructure
- Testing infrastructure changes

**Example Answer:**
"I use Terraform to manage AWS infrastructure with a modular structure—separate modules for VPC, EKS, RDS, etc. I store state remotely in S3 with state locking via DynamoDB. I use Terraform workspaces for dev/staging/prod environments and implement code review through Git for all infrastructure changes. Before applying, I always run terraform plan to review changes and often use -target for specific resource updates. I've also created reusable modules for common patterns."

---

**8. "How do you ensure security in your pipelines?"**

**What They're Testing:** DevSecOps mindset

**Your Answer Should Include:**
- Container image scanning
- Credentials management
- Code scanning (SAST)
- Dependency updates
- Access controls

**Example Answer:**
"I implement security at multiple stages. During CI, I scan code with static analysis tools and dependencies with Snyk. Container images are scanned with Trivy before pushing to registry. I never hardcode secrets—they're managed through CI/CD platform secrets or Vault. Infrastructure uses least privilege IAM policies. I also implement network policies in Kubernetes and use pod security policies. Regular security audits and penetration testing are part of the process."

---

### Behavioral Questions

**"Why do you want to be a DevOps Engineer?"**

**Good Answer:**
"I'm passionate about building reliable systems and automating operational overhead. DevOps appeals to me because it bridges development and operations, improving deployment speed and system reliability. I enjoy solving infrastructure problems at scale and believe that good DevOps practices enable teams to innovate faster while maintaining stability."

---

**"How do you stay updated with DevOps trends?"**

**Good Answer:**
"I follow blogs like Medium's DevOps stories, listen to podcasts like 'Cloud Native Now,' and maintain a GitHub learning repository. I practice with new tools in personal projects, participate in DevOps communities, and regularly review AWS documentation. I also allocate time each week to read about industry trends and emerging tools."

---

### Technical Interview Exercises

**Exercise 1: Write a CI/CD Pipeline**

**Scenario:** "Write a GitHub Actions workflow that builds a Docker image, pushes it to ECR, and deploys to Kubernetes."

**Expected Components:**
- Checkout code
- Run tests
- Build Docker image
- Push to ECR
- Update Kubernetes manifest or trigger deployment
- Handle secrets securely

---

**Exercise 2: Terraform Code Review**

**Scenario:** "Review this Terraform code and identify issues."

**What They're Checking:**
- Hardcoded values (use variables instead)
- Missing resource tags
- Insufficient security (security groups, IAM)
- State management issues
- No data validation

---

**Exercise 3: Troubleshooting Scenario**

**Scenario:** "A Kubernetes pod keeps restarting. How do you debug?"

**Steps to Mention:**
1. `kubectl describe pod` → check events
2. `kubectl logs` → check application logs (before restart)
3. `kubectl logs -p` → check previous log
4. Check resource requests/limits
5. Check liveness/readiness probes
6. Analyze events for OOMKilled, CrashLoopBackOff, etc.

---

### Portfolio Presentation Guide

**In Interviews, Highlight:**

1. **Complexity Managed**
   - "Deployed 15 microservices across 3 environments"
   - "Reduced deployment time from 45 minutes to 5 minutes"
   - "Managed infrastructure for 1M+ users"

2. **Technologies Mastered**
   - Specific versions (Kubernetes 1.28, Terraform 1.5, etc.)
   - Multiple tool options (Jenkins and GitHub Actions)
   - Depth in specific areas (CKA preparation, advanced Terraform modules)

3. **Problems Solved**
   - Operational bottlenecks
   - Security issues
   - Cost optimization
   - Performance improvements

4. **Business Impact**
   - Faster time to market
   - Reduced operational overhead
   - Improved system reliability
   - Cost savings

---

### Salary Negotiation Talking Points

**You Can Say:**
- "I've built production-grade infrastructure on AWS using Terraform"
- "I've implemented complete CI/CD pipelines that reduced deployment time by 60%"
- "I have hands-on experience with Kubernetes, Docker, and container orchestration"
- "I've managed multi-environment deployments with GitOps"
- "I have relevant certifications: AWS Cloud Practitioner, Terraform Associate"

**Typical Offers (India, for Junior):**
- ₹6-10 LPA base
- +₹1-2 LPA performance bonus
- Negotiable based on location and company

---

## Final Notes

### After Job Landing: Continue Learning

**First 6 Months on Job:**
- Master company's specific tools and workflows
- Understand existing infrastructure
- Contribute to improving CI/CD
- Learn from senior engineers
- Document processes

**Next 6-12 Months:**
- Pursue CKA certification
- Learn service mesh (Istio, Linkerd)
- Study SRE principles deeper
- Contribute to open-source DevOps projects
- Consider specializations (SecOps, FinOps, Platform Engineering)

---

### Resources NOT Covered (Next Steps)

- Advanced Kubernetes (Service Mesh, Operators)
- Advanced AWS (organizations, cost optimization)
- Security (DevSecOps, vulnerability management)
- SRE principles and incident management
- FinOps and cost optimization
- MLOps and data pipeline deployment

---

**Good luck with your DevOps journey! The roadmap is aggressive but achievable with consistent effort.**

