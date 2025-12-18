# The 2025 DevOps Acceleration Protocol: Modified Roadmap

This roadmap is a modification of the original "DevOps-Roadmap-for-Indian-Freshers.pdf", updated with critical adjustments to prioritize employability and address common interview failure points. It serves as a strategic guide from a Principal DevOps perspective, engineered to transform a fresher into a production-ready Junior DevOps Engineer within 8-12 weeks.

## Context: Why This Matters

Entry-level DevOps roles in India command salaries ranging from ₹4 LPA to ₹9 LPA, with top-tier product firms and remote startups offering compensation packages exceeding ₹12-15 LPA for exceptional freshers who demonstrate "production-ready" capabilities. However, recruitment data reveals a critical paradox: while the volume of "certified" freshers is high, there is a distinct shortage of candidates who possess the practical debugging skills necessary for real-world operations.

This roadmap prioritizes that missing practical depth. It is engineered to bypass academic fluff in favor of high-impact, interview-centric skills—Linux internals, cloud networking, container orchestration, and infrastructure automation. The objective is not merely to "learn tools," but to cultivate the engineering maturity, troubleshooting intuition, and architectural understanding required to survive technical interviews and thrive from Day 1 in a production environment.

## The Two-Track Ecosystem: Understanding Your Path

Before beginning this journey, understand that India's IT ecosystem operates on two distinct recruitment tracks:

### Track A: Service-Based Giants (TCS, Infosys, Wipro, Accenture, Cognizant)

These organizations do not hire for specific "DevOps" roles at the fresher level. Instead, they hire for "System Engineer" or "Digital Specialist" profiles through mass recruitment drives like TCS NQT or Infosys InfyTQ.

- **The Primary Filter:** Aptitude—Quantitative ability, Logical Reasoning, and Verbal skills. A candidate with world-class Kubernetes skills will be rejected if they fail the initial aptitude screening.
- **The DevOps Entry Path:** Once hired, freshers are allocated to projects. Those with prior certification (AWS, Terraform) or demonstrated skills are fast-tracked into Cloud/DevOps centers of excellence.
- **Implication for This Roadmap:** You must allocate time for aptitude preparation. Ignoring this closes the door on 60% of the available job market.

### Track B: Product-Based Companies and Startups (Razorpay, Unicorns, Global Tech Giants)

This sector hires directly for "Junior DevOps Engineer" or "SRE Intern" roles.

- **The Primary Filter:** Technical Competence. Interviews focus heavily on Linux troubleshooting, coding proficiency (Python/Go), and system design concepts.
- **The DevOps Entry Path:** Candidates are expected to contribute to production systems immediately. Proof of work—GitHub repositories, blogs, and live projects—is the currency of credibility.
- **Implication for This Roadmap:** This track emphasizes building a portfolio. A "3-Tier Web Architecture" project is a non-negotiable asset.

## The Principal Engineer's Mindset: Productivity Over Tools

A recurring theme in Principal-level advice is the rejection of "tool collecting." Freshers often list 20 tools on their resume but cannot explain how they work together or the problem each solves. This roadmap focuses on the *capabilities* that tools enable:

1. **Infrastructure Provisioning (Terraform)** – replacing manual clicking
2. **Configuration Management (Ansible/Scripts)** – replacing manual installation
3. **Continuous Integration (Jenkins/GitHub Actions)** – replacing manual testing
4. **Containerization (Docker)** – replacing dependency hell
5. **Orchestration (Kubernetes)** – replacing manual scaling

The roadmap is structured to build these capabilities sequentially, ensuring you understand the problem before learning the tool that solves it.

---

## Corrected Flow: Optimized for Employability

### Weeks 1–2: Foundational Skills

This phase establishes the bedrock upon which all DevOps work rests. The cloud is essentially "Linux at scale." A Junior Engineer who cannot navigate a terminal or debug a crashed process is a liability.

#### Linux Operations: Focus on Practical Commands

The first transformation requires abandoning the Graphical User Interface (GUI). In production environments, servers are headless and accessed remotely via SSH. Begin by installing a Linux distribution (Ubuntu Server or CentOS) on a virtual machine using VirtualBox, or use Windows Subsystem for Linux (WSL2)—though a full VM is preferred for kernel-level isolation.

**Process Management:** Understanding the difference between process states and signals is fundamental.

- **Commands:** `ps`, `top`, `htop`, `kill`, `pkill`
- **Deep Dive:** Process IDs (PIDs) and Signals. `SIGTERM` (15) allows a process to shut down gracefully—it has time to clean up database connections and file handles. `SIGKILL` (9) is the "nuclear option" that terminates it instantly without cleanup. Interviewers frequently ask this difference to test your production maturity.
- **Load Average:** Understanding the "load average" numbers in `top` (1 min, 5 min, 15 min). A load average higher than the number of CPU cores indicates a bottleneck where processes are queuing for CPU time.

**Example:** If your server has 4 CPU cores and the load average is 8, processes are backing up and responses will be slow.

**File Permissions and Ownership:** Security starts at the OS level.

- **Commands:** `chmod`, `chown`, `chgrp`
- **The Octal System:** Mastering this is non-negotiable. r=4 (read), w=2 (write), x=1 (execute). A permission of 755 (rwx-rx-rx) is standard for executable scripts; 600 (rw-------) is mandatory for SSH keys because only the owner should read private keys.
- **The "Why":** Applying 777 (rwxrwxrwx) grants write access to the world, allowing any user to inject malicious code into a script. This is an instant red flag in interviews.

**Text Processing:** Logs are the primary source of truth in production. A junior engineer must extract specific error patterns from gigabytes of log data without opening files in text editors (which would crash the terminal).

- **Commands:** `grep`, `awk`, `sed`, `tail`, `head`, `less`
- **Piping Example:** `cat access.log | grep "500" | awk '{print $1}' | sort | uniq -c` to find which IP addresses are causing 500 errors. This specific command chain is a "LeetCode for Ops" style question often asked in interviews.
- **Redirection:** Understanding `>` (overwrite), `>>` (append), and `2>` (redirect errors). This is essential for cron jobs and automated scripts.

#### Git Basics: This is a Critical Skill

You will be asked about Git in every interview. Be prepared to answer:

- `git pull` vs. `git fetch` – Pull does a fetch + merge. Fetch retrieves remote changes without modifying your working directory.
- `rebase` vs. `merge` – Merge creates a merge commit, preserving history. Rebase rewrites history to create a linear timeline. When to use each?
- How to resolve merge conflicts – Understanding the conflict markers (`<<<<`, `====`, `>>>>`) and how to decide what code to keep.
- Git branching strategies – GitFlow, trunk-based development, feature branches.
- The pull request (PR) workflow – How code review ensures quality before merging.
- Commit hygiene – Writing atomic, meaningful commit messages. Bad: "fixed stuff". Good: "Fix: Resolve race condition in database connection pool".

#### Bash Scripting: The Glue of Automation

Before Python or Terraform, there was Bash. It remains the quickest way to automate server tasks.

- **Basics:** Shebang (`#!/bin/bash`), Variables, Loops (`for`, `while`), Conditionals (`if/else`)
- **Lab Assignment:** Write a script that checks disk usage. If usage exceeds 80%, the script should zip log files in `/var/log` and move them to a backup folder. This touches on file manipulation, conditionals, and system monitoring.
- **Why This Matters:** This script mimics real-world log rotation, a fundamental operational task.

**Week 1-2 Success Criteria:**

| Skill | Proof |
|-------|-------|
| Virtualization | Ubuntu Server running in VirtualBox/WSL2 |
| Navigation | Comfortable moving, copying, and deleting files via CLI |
| Permissions | Can explain `drwxr-xr-x` and change it to `700` |
| Process Control | Can identify a high-CPU process and kill it safely |
| Scripting | A working "System Health Check" bash script pushed to GitHub |

---

### Week 3: Networking and Debugging

Networking is often the most feared topic, but understanding how computers communicate is essential. Cloud computing is essentially networking. A VPC (Virtual Private Cloud) is a software-defined network. Without understanding IP addressing, ports, and protocols, you cannot configure Security Groups or debug connection timeouts.

#### Core Networking Concepts

This section strips away academic OSI model layers that don't apply to daily DevOps work and focuses on Layers 3, 4, and 7—the ones you'll actually use.

**IP Addressing and Subnetting (Layer 3):**

- **IPv4 Structure:** `192.168.1.5` is broken into octets. Each octet ranges from 0-255. Understanding the structure is foundational.
- **CIDR Notation:** This is critical for AWS. `10.0.0.0/16` represents a network with 65,536 IPs. `10.0.1.0/24` represents a subnet within it with 256 IPs. A fresher must know that a `/24` gives 256 IPs (with 2 reserved: network and broadcast).
- **Private vs Public IPs:** Understanding RFC 1918 private ranges (10.x.x.x, 172.16.x.x–172.31.x.x, 192.168.x.x) and why they are not routable on the public internet. This is critical for designing secure cloud architectures.

**Ports and Transports (Layer 4):**

- **TCP vs UDP:** TCP is reliable (three-way handshake, acknowledgments); UDP is fast (fire-and-forget). Databases and Web use TCP; DNS and Streaming often use UDP.
- **Standard Ports—Memorize These:** 
  - 22: SSH (Secure Shell)
  - 80: HTTP (Web)
  - 443: HTTPS (Secure Web)
  - 3306: MySQL
  - 5432: PostgreSQL
  - 53: DNS
- **Troubleshooting Logic:** If an application isn't working, the first question is "Is the port open and listening?" Tools like `netstat -tulpn` (on the server) and `telnet` or `nc` (from the client) are the stethoscopes for this diagnosis.

**DNS: The Phonebook (Layer 7):**

DNS resolution failures cause a disproportionate number of outages—there's even a saying in ops: "It's always DNS."

- **Common Record Types:** A (Address), CNAME (Alias), MX (Mail), TXT (Text, used for verification).
- **Tools:** `nslookup` and `dig`. You should be able to query a domain and explain the output (TTL, Answer Section, Authority Section).
- **Debugging Example:** If `ping example.com` fails but `ping 93.184.216.34` succeeds, the issue is DNS resolution. Run `dig example.com` to see what DNS is returning.

#### SSH: The Keys to the Kingdom

SSH is the standard method for managing Linux servers securely.

- **Key-Based Authentication:** Passwords are insecure and scalability nightmares. The roadmap requires setting up SSH Key Pairs using `ssh-keygen`. The public key goes to the server (`~/.ssh/authorized_keys`); the private key stays on your laptop.
- **Security Concept:** "Something you have (key)" vs "Something you know (password)." Keys are cryptographically stronger.
- **Lab:** Configure two VMs. Set up passwordless SSH login from VM A to VM B using key-based authentication. This mimics the setup used by automation tools like Ansible.

**Week 3 Success Criteria:**

| Skill | Proof |
|-------|-------|
| CIDR Calculation | Calculate how many IPs are in a `/24` and a `/16` |
| Port Memorization | Recall the standard ports for SSH, HTTP, MySQL, PostgreSQL, DNS |
| SSH Setup | Passwordless login from one machine to another using key pairs |
| DNS Debugging | Use `dig` to troubleshoot a DNS query |

---

### Weeks 4–5: Core AWS – The Manual Path First

Translating local Linux knowledge to the Amazon Web Services (AWS) cloud. AWS holds dominant market share. While Azure and GCP are relevant, AWS is the "lingua franca" of cloud interviews in India.

**Critical Philosophy:** Before using Terraform or Infrastructure-as-Code, you will manually provision a VPC, EC2, and RDS. This manual process teaches you what automation later replaces. You must understand the problem before learning the tool that solves it.

#### Identity and Access Management (IAM)

Security is Day 0 in the cloud.

- **The Root Account Danger:** The account created with an email address (when you sign up for AWS) is the Root user. It has unlimited power and no limits on damage. The first rule of AWS: Create an Admin IAM User and enable Multi-Factor Authentication (MFA). Lock away the Root credentials in a vault—you should almost never use them.
- **Users, Groups, Roles:**
  - **Users:** Represent humans (e.g., your email).
  - **Groups:** Collections of users (e.g., "Developers" group with common permissions).
  - **Roles:** Identities for services. If an EC2 instance needs to write to an S3 bucket, it assumes a Role. It does *not* save hardcoded credentials in the code. This is a crucial security pattern.
- **Policies:** JSON documents defining permissions. The "Principle of Least Privilege" dictates granting only the minimum permissions necessary for the task. Example: A junior developer needs S3 read access, not S3 full access.

#### Elastic Compute Cloud (EC2)

EC2 is the cloud equivalent of the virtual machines you created in Phase 1.

- **Instance Types:** Understanding the difference between `t3.micro` (General Purpose, Burstable) and `c5.large` (Compute Optimized). For freshers, the `t2.micro` or `t3.micro` falls under the Free Tier.
- **Burstable Instances:** The "t" family (t3, t2) accumulates CPU credits when idle. When the app needs a burst of CPU, it consumes credits. Once credits are depleted, performance tanks. Be aware of this during load testing.
- **Security Groups:** A stateful firewall at the instance level. 
  - **Classic Interview Question:** "If I open port 80 in the Inbound rules, do I need to open it in Outbound?" 
  - **Answer:** No, because Security Groups are stateful; return traffic is automatically allowed.
- **Key Pairs:** The `.pem` file downloaded upon creation is the private key. Losing it means losing access to the instance forever. Download it immediately and keep it safe.

#### Virtual Private Cloud (VPC) – The Deep Dive

This is the most technically challenging and highest-value topic for a fresher. Most candidates use the "Default VPC." Building a custom VPC from scratch demonstrates seniority.

**Architecture Components:**

- **CIDR Block:** The IP range for the entire VPC (e.g., `10.0.0.0/16` gives you 65,536 addresses).
- **Subnets:** Logical partitions of the VPC. A VPC can span multiple Availability Zones (AZs).
  - **Public Subnet:** Has a direct route to the Internet Gateway. Used for Load Balancers, Bastion Hosts (jump boxes).
  - **Private Subnet:** No direct route to the internet. Used for Databases, Application Servers. Instances here cannot be reached from the internet.
- **Internet Gateway (IGW):** The gateway enabling instances to communicate with the internet.
- **Route Tables:** Rules controlling traffic flow between subnets and the internet. For example, a route table for a public subnet might say: "Destination 0.0.0.0/0 (all traffic) → Internet Gateway."
- **NAT Gateway:** Allows instances in the Private Subnet to initiate outbound traffic (e.g., for software updates, API calls) without accepting inbound connections. This is a critical security pattern.

**The "Hard Way" Lab (Week 4-5 Capstone):**

Manually create a VPC following these steps:

1. Create a VPC with CIDR block `10.0.0.0/16`
2. Create a Public Subnet (`10.0.1.0/24`) and a Private Subnet (`10.0.2.0/24`)
3. Create an Internet Gateway and attach it to the VPC
4. Create Route Tables:
   - Public Route Table: Add a route `0.0.0.0/0 → IGW` (all traffic to internet)
   - Private Route Table: Add a NAT Gateway for outbound internet access
5. Launch an EC2 instance in the Private subnet and prove you can:
   - Access the instance via a Bastion Host (jump box) in the Public Subnet
   - Access the internet from the private instance (via NAT)
   - Confirm the internet cannot initiate a connection to the private instance

**Why This Matters:** When you describe this in an interview, you signal deep understanding of cloud architecture. Later, you'll automate this entire setup with Terraform (Week 8).

#### Storage (S3) and Database (RDS)

- **S3 (Simple Storage Service):** Object storage for files (images, logs, backups). Understand "Buckets" (like directories) and "Objects" (like files). Highlighting the capability to host static websites (HTML/JS/CSS) directly from S3 is a great portfolio point.
- **RDS (Relational Database Service):** Managed SQL (MySQL, PostgreSQL). The key value proposition is that AWS manages patching and backups—you don't.
  - **Multi-AZ Deployment:** For High Availability. If the primary database fails, AWS automatically fails over to a standby in a different Availability Zone. This concept is central to "Reliability" in DevOps.

**Week 4-5 Lab Deliverables:**

| Milestone | Proof |
|-----------|-------|
| Secure IAM | Root account secured with MFA. Admin user created with appropriate policies. |
| Custom VPC | VPC with Public/Private subnets, IGW, NAT Gateway, and Route Tables configured manually (no CloudFormation/Terraform). |
| Web Server | EC2 launched in Public subnet. Nginx installed. Custom index.html visible via Public IP. |
| Database | RDS MySQL instance launched in Private subnet. Connection from Web Server confirmed. |
| Documentation | Diagram showing traffic flow. Screenshots of Security Group configurations. |

---

### Week 6: Docker – Containerization

Objective: Master the modern unit of deployment. "It works on my machine" is the oldest problem in software. Containers solve this by packaging code with its environment.

**Concept: Containers vs Virtual Machines**

- **Virtual Machines:** Virtualize hardware (CPU, RAM, Disk). Heavy, slow to boot (minutes). Each VM runs a full OS.
- **Containers:** Virtualize the OS. Lightweight, instant boot (seconds). Multiple containers share the host kernel but have isolated user spaces (namespaces, cgroups).

**The Dockerfile: The Recipe**

A Dockerfile is a set of instructions to build an image.

```dockerfile
FROM python:3.9-alpine          # Base image
WORKDIR /app                    # Set working directory
COPY requirements.txt .         # Copy dependency file
RUN pip install -r requirements.txt  # Install dependencies
COPY . .                        # Copy application code
CMD ["python", "app.py"]        # Command to start the app
```

**Key Commands:**

- `docker build -t myapp:latest .` – Builds an image from the Dockerfile
- `docker run -p 5000:5000 myapp:latest` – Runs a container from the image
- `docker ps` – Lists running containers
- `docker logs <container_id>` – Views container logs
- `docker exec -it <container_id> bash` – Executes a command inside a running container

**Networking: How Containers Talk**

Understanding container networking is crucial.

- **Bridge Network (default):** Containers on the same bridge network can communicate via container names.
- **Host Network:** Container uses the host's network stack.
- `docker-compose` – A tool for orchestrating multi-container applications. Instead of running multiple `docker run` commands, you define them in a YAML file.

**Lab Assignment: Containerize a Flask Application**

1. Write a simple Flask app that connects to a Redis cache and a PostgreSQL database
2. Create a Dockerfile for the Flask app
3. Use `docker-compose` to spin up three containers: Flask app, Redis, and PostgreSQL
4. Test that the app works by accessing `localhost:5000`
5. Push the image to Docker Hub or AWS ECR

**Why This Matters:** By Week 6, you've packaged a real application with its dependencies. In Week 7, this image will be deployed via CI/CD. In Week 9, it will be orchestrated in Kubernetes.

**Week 6 Success Criteria:**

| Skill | Proof |
|-------|-------|
| Dockerfile | Write a Dockerfile for a Python/Node.js app |
| Building & Running | Build an image and run it as a container |
| Docker Compose | Multi-container setup (app, database, cache) via docker-compose.yml |
| Registry | Push image to Docker Hub or AWS ECR |

---

### Week 7: Continuous Integration (CI) – The Pipeline Begins

Objective: Automate the build and test process. CI ensures that every commit is tested before merging, catching bugs early.

**Concept: The Pipeline**

Source Code (Git) → Build (Docker) → Test (Unit Tests) → Scan (Code Quality) → Push to Registry

**GitHub Actions: The Modern Choice**

GitHub Actions is cloud-native, integrated with your repository, and free for public repos. Perfect for a portfolio.

**Lab: Create a CI Pipeline**

1. Create a Python app with a simple test:
   ```python
   def add(a, b):
       return a + b
   
   def test_add():
       assert add(2, 3) == 5
   ```

2. Create a `.github/workflows/ci.yml` file:
   ```yaml
   name: CI Pipeline
   
   on:
     push:
       branches: [main]
   
   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         - name: Set up Python
           uses: actions/setup-python@v4
           with:
             python-version: '3.9'
         - name: Install dependencies
           run: |
             pip install -r requirements.txt
             pip install pytest
         - name: Run tests
           run: pytest
         - name: Build Docker image
           run: docker build -t myapp:latest .
         - name: Push to Docker Hub
           run: docker push myapp:latest
   ```

3. Push to GitHub and watch the pipeline run automatically.

**Why This Matters:** This pipeline ensures that every commit is tested before merging. If tests fail, the build fails, and bad code never reaches production.

**Week 7 Success Criteria:**

| Milestone | Proof |
|-----------|-------|
| Workflow File | `.github/workflows/ci.yml` in your repository |
| Test Execution | Tests run automatically on every push |
| Docker Build | Image built and pushed to a registry |
| Pipeline Pass | Green checkmark on your commit showing pipeline success |

---

### Week 8: Terraform – Infrastructure as Code (IaC)

Objective: Automate infrastructure provisioning. Terraform allows you to define your AWS resources (VPC, EC2, RDS) in code and deploy them with a single command.

**Declarative vs Imperative:**

- **Declarative:** "I want 3 servers with these configurations." Terraform figures out how to achieve the desired state.
- **Imperative:** "Create server 1, then server 2, then server 3." You specify each step.

Terraform is declarative. You describe the end state, and it handles the "how."

**The State File (terraform.tfstate):**

Terraform maintains a state file that tracks the mapping between your code and real AWS resources. This file is critical—losing it means Terraform doesn't know what it created, leading to duplicate resources.

**Basic Workflow:**

1. `terraform init` – Initialize the working directory (downloads providers)
2. `terraform plan` – Preview what will be created/modified/destroyed
3. `terraform apply` – Execute the plan
4. `terraform destroy` – Clean up all resources

**Lab: Translate the Manual VPC to Terraform**

Recreate the manual VPC from Week 4 using Terraform:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
  tags = { Name = "main-vpc" }
}

resource "aws_subnet" "public" {
  vpc_id            = aws_vpc.main.id
  cidr_block        = "10.0.1.0/24"
  availability_zone = "us-east-1a"
  tags = { Name = "public-subnet" }
}

resource "aws_internet_gateway" "main" {
  vpc_id = aws_vpc.main.id
  tags = { Name = "main-igw" }
}

# ... more resources ...
```

**Why This Matters:** This demonstrates Infrastructure as Code—a core DevOps competency. You can version control your infrastructure, review changes via pull requests, and reproduce the entire setup with a single `terraform apply`.

**Week 8 Success Criteria:**

| Skill | Proof |
|-------|-------|
| Terraform Basics | Can write basic resource definitions |
| State Management | Understand what terraform.tfstate is and why it's important |
| Plan & Apply | Run `terraform plan` and `terraform apply` successfully |
| Destroy & Recreate | Destroy resources and recreate them with `terraform apply` |
| Version Control | Terraform code pushed to GitHub with clear commit messages |

---

### Week 9: Kubernetes (Conceptual) – The Orchestrator

Objective: Understand how Kubernetes manages containers at scale. While conceptual understanding is sufficient for junior roles, hands-on experience with Minikube sets you apart.

**Architecture:**

- **Control Plane:** The brain (API Server, Scheduler, etcd). Makes decisions about pod placement, scaling, etc.
- **Nodes:** Worker machines running containers. The Control Plane tells them what to run.

**Key Kubernetes Objects:**

- **Pod:** The smallest unit. Usually one container per pod, but multiple containers can share a pod (sidecars).
- **Deployment:** Manages the lifecycle of Pods. "I want 3 replicas of this app." If one crashes, the Deployment automatically starts a new one (self-healing).
- **Service:** Provides networking. A stable IP/DNS name to access a set of Pods. Without Services, accessing Pods directly would be problematic (Pods are ephemeral).

**Lab: Deploy a Containerized App to Minikube**

1. Install Minikube (local Kubernetes cluster)
2. Start Minikube: `minikube start`
3. Write deployment.yaml:
   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: flask-app
   spec:
     replicas: 3
     selector:
       matchLabels:
         app: flask-app
     template:
       metadata:
         labels:
           app: flask-app
       spec:
         containers:
         - name: flask
           image: myapp:latest
           ports:
           - containerPort: 5000
   ---
   apiVersion: v1
   kind: Service
   metadata:
     name: flask-service
   spec:
     selector:
       app: flask-app
     ports:
     - port: 80
       targetPort: 5000
     type: LoadBalancer
   ```

4. Deploy: `kubectl apply -f deployment.yaml`
5. Access the app: `minikube service flask-service`

**Why This Matters:** Kubernetes is the industry standard for container orchestration. Junior roles may not require deep Kubernetes expertise, but demonstrating conceptual understanding and hands-on experience is a significant differentiator.

**Week 9 Success Criteria:**

| Milestone | Proof |
|-----------|-------|
| Minikube Installation | Minikube cluster running locally |
| Deployment Creation | deployment.yaml file defining replicas and container image |
| Service Exposure | Service created to expose the app |
| Pod Verification | Verify all 3 pods are running: `kubectl get pods` |
| App Access | Access the app via the Service DNS/IP |

---

### Weeks 10–12: Capstone, Resume, and Job Hunt

#### Week 10-11: The Capstone Project – 3-Tier Web Architecture

Objective: Synthesize all skills into a single, demonstrable portfolio asset. When an interviewer asks, "What have you built?", this project is the answer. It covers Networking, Compute, Database, Security, Automation, and CI/CD in one cohesive narrative.

**Architecture Overview:**

A standard production architecture consists of three layers:

1. **Presentation Tier:** The Web Server (Nginx/React). Publicly accessible on the internet.
2. **Application Tier:** The Logic (Python Flask/Node.js). Processes requests and interacts with the database. Not directly accessible from the internet.
3. **Data Tier:** The Database (RDS MySQL/PostgreSQL). Stores data. Only accessible from the Application Tier.

**Step-by-Step Implementation:**

**Phase 1: Network Design**

Use Terraform to provision a VPC with the following structure:

- VPC CIDR: `10.0.0.0/16`
- 2 Public Subnets across 2 Availability Zones (for redundancy): `10.0.1.0/24` (us-east-1a), `10.0.3.0/24` (us-east-1b)
- 2 Private Subnets across 2 Availability Zones: `10.0.2.0/24` (us-east-1a), `10.0.4.0/24` (us-east-1b)
- Internet Gateway for public subnets
- NAT Gateways in each public subnet for private subnet internet access
- Route Tables configured appropriately

**Phase 2: Security Layers**

Create Security Groups with explicit rules (not "allow all"):

- **Web SG:** Allow Port 80/443 from `0.0.0.0/0` (the entire internet). Allow egress to App SG on port 5000.
- **App SG:** Allow port 5000 only from Web SG (not from the internet). Allow egress to DB SG on port 3306.
- **DB SG:** Allow port 3306 only from App SG. This is called "Security Group chaining"—each tier can only talk to the next tier.

**Phase 3: Application Deployment**

- Write a Python Flask application:
  ```python
  from flask import Flask
  import mysql.connector
  
  app = Flask(__name__)
  
  @app.route('/')
  def todo_list():
      conn = mysql.connector.connect(
          host=os.getenv('DB_HOST'),
          user=os.getenv('DB_USER'),
          password=os.getenv('DB_PASSWORD'),
          database=os.getenv('DB_NAME')
      )
      cursor = conn.cursor()
      cursor.execute('SELECT * FROM todos')
      todos = cursor.fetchall()
      return render_template('index.html', todos=todos)
  
  if __name__ == '__main__':
      app.run(host='0.0.0.0', port=5000)
  ```

- Containerize it with Docker
- Push the image to AWS ECR (Elastic Container Registry)
- Deploy containers to EC2 instances in the Private Subnets

**Phase 4: Load Balancing**

Deploy an Application Load Balancer (ALB) in the Public Subnets:

- Listener: Port 80
- Target Group: EC2 instances running the Flask app in the Private Subnets
- Health Checks: ALB periodically checks if targets are healthy. If a target is unhealthy, traffic is routed away from it.

Users access the ALB DNS name (e.g., `myapp-alb-123456.us-east-1.elb.amazonaws.com`), not the EC2 instances directly.

**Phase 5: Automation via CI/CD**

Create a GitHub Actions pipeline:

1. On every push to the `main` branch:
   - Build the Docker image with the latest code
   - Run tests (unit tests, security scans)
   - Push the image to AWS ECR with a new tag (e.g., `myapp:latest`)
   - Trigger an ECS service update (or EC2 deployment) to pull the new image

This achieves "zero-downtime deployment"—users don't experience interruptions when you push new code.

**Phase 6: Database Setup**

- Create an RDS MySQL instance in the Private Subnets
- Create a "todos" table with columns: id, task, completed, created_at
- Initialize with sample data
- Configure backups (daily snapshots) and Multi-AZ failover for high availability

**The "Resume Hook":**

On your resume, describe this project not as a "To-Do App," but as:

> "Architected and deployed a highly available 3-tier infrastructure on AWS using Terraform. Implemented network isolation using VPCs and private subnets, secured communication via Security Group chaining, containerized the application with Docker, and automated zero-downtime deployments via GitHub Actions CI/CD pipeline. Configured RDS Multi-AZ for database reliability and Application Load Balancer for horizontal scalability."

This language signals professional competency to hiring managers.

#### Week 12: Resume, Interview Preparation, and Job Hunt

**Resume Engineering for ATS (Applicant Tracking Systems)**

ATS systems scan resumes for keywords. If keywords aren't there, the resume is rejected before humans see it.

**Must-Have Keywords (in order of importance):**
- Linux, AWS, EC2, S3, VPC, Docker, Kubernetes, Jenkins/GitHub Actions, Terraform, Python, Git, CI/CD, Troubleshooting, RDS, IAM, ECS, Nginx, Bash, Monitoring

**Action Verbs:**
- Use: "Deployed," "Automated," "Architected," "Optimized," "Reduced," "Designed"
- Avoid: "Worked on," "Helped with," "Responsible for"

**Project Links:**
- Hyperlink the GitHub repo for the Capstone Project
- Include links to individual project repos (Health Check Script, CI/CD Pipeline, etc.)

**The "Aptitude" Hurdle (for Service-Based Companies)**

If you're targeting TCS, Infosys, or Wipro, aptitude is the primary gatekeeper.

**Strategy:** Dedicate 30-45 minutes daily to aptitude practice throughout the 12 weeks.

**Key Topics:** 
- Percentages, Ratios
- Time & Work
- Speed & Distance
- Permutations & Combinations
- Data Interpretation (reading graphs and tables)

**Resources:** Websites like IndiaBix and PrepInsta are standard.

**Troubleshooting Scenarios: "War Stories"**

Interviewers will present broken scenarios to test your troubleshooting logic.

**Scenario 1: "A user reports the website is slow. How do you debug?"**

Answer Structure:
1. **Scope:** Is it slow for everyone or just one user? (Isolate the problem)
2. **Metrics:** Check CloudWatch/Grafana. High CPU? High Memory? Disk I/O?
3. **App Layer:** Check logs (`tail -f /var/log/flask.log`). Are there timeouts or errors?
4. **Database:** Is the database locked? Run `SHOW PROCESSLIST;` to check active queries. Is there a slow query?
5. **Network:** Is there latency at the Load Balancer? Check ALB Target Group Health.

**Key Insight:** Mentioning specific tools (`top`, `iostat`, `slow query log`, CloudWatch) proves hands-on experience, not just theoretical knowledge.

**Scenario 2: "The server is out of disk space. What do you do?"**

Answer Structure:
1. **Identification:** `df -h` shows 100% usage on `/`
2. **Localization:** `du -sh /* | sort -hr` to find the largest directories
3. **Common Culprit:** Usually `/var/log` (logs consume disk quickly)
4. **Quick Fix:** Truncate the syslog: `> /var/log/syslog`
5. **The Trap:** "I deleted the file but space wasn't freed."
   - Reason: A running process is still holding the file handle open
   - Fix: `lsof | grep deleted` to find the process, then `systemctl restart nginx` to release it

Knowing this specific detail is a hallmark of a production-ready engineer.

**Scenario 3: "A deployment failed. How do you rollback?"**

Answer Structure:
1. **Assess Impact:** What was deployed? Are users affected?
2. **Rollback Strategy:** Does your CI/CD system have a one-click rollback to the previous version?
3. **For Kubernetes:** `kubectl rollout undo deployment/flask-app`
4. **For ECS:** Update the service to pull the previous Docker image tag
5. **Communication:** Notify stakeholders immediately
6. **Post-Mortem:** Analyze why the deployment failed. What testing did we miss?

**Behavioral Questions (HR Round)**

**Question:** "Tell me about a time you faced a technical challenge."

**Method:** Use the STAR technique (Situation, Task, Action, Result).

- **Situation:** "My Terraform script failed to create the VPC during deployment."
- **Task:** "I needed to fix it quickly to unblock the team."
- **Action:** "I debugged the state file, realized there was a locking issue from a previous failed run. I released the lock and modularized the Terraform code to prevent future conflicts."
- **Result:** "The deployment succeeded, and deployment time was reduced by 50% in future runs."

This demonstrates problem-solving, communication, and continuous improvement—qualities every company values.

---

## Critical Additions for Interview Success

### 1. Python Scripting (Critical – Often Overlooked)

**Why:** Bash is for the OS; Python is for the Cloud. You will get a coding test. It will likely be: "Write a script to parse this JSON" or "List all EC2 instances older than 30 days."

**What to Learn:**

- **boto3 (AWS SDK for Python):** Learn how to authenticate with AWS and interact with AWS services programmatically
  ```python
  import boto3
  
  ec2 = boto3.client('ec2')
  response = ec2.describe_instances()
  for reservation in response['Reservations']:
      for instance in reservation['Instances']:
          print(instance['InstanceId'], instance['State']['Name'])
  ```
- Practice common operations: listing EC2 instances, querying S3 buckets, managing RDS databases
- Write at least 2-3 scripts that solve real-world problems:
  - Automated resource cleanup (delete unattached EBS volumes)
  - Cost reporting (calculate monthly spending by resource)
  - Backup automation (create and manage snapshots)
- Understand how to handle API responses and error handling

### 2. The "Why" of the Cloud – Cost Optimization

**Interview Trap:** "Why did you choose this instance type?"

**What You Need to Know:**

- **EC2 Instance Types and Their Use Cases:**
  - `t3` (General Purpose, Burstable): Web apps, small databases
  - `c5` (Compute Optimized): High-CPU workloads, video encoding
  - `r5` (Memory Optimized): Databases, caching layers
  - `i3` (Storage Optimized): NoSQL databases, data warehouses
- **On-Demand vs Spot vs Reserved:**
  - On-Demand: Pay-as-you-go, most flexible but expensive
  - Spot Instances: Up to 90% discount, but AWS can reclaim them (risky for production but good for batch jobs)
  - Reserved Instances: Commit to 1-3 years for 30-70% discount
- **Calculate Total Cost of Ownership (TCO) for a 3-Tier Architecture:**
  - 2x Application Servers (t3.medium): ~$60/month
  - 1x RDS MySQL (db.t3.small, Multi-AZ): ~$100/month
  - 1x Application Load Balancer: ~$20/month + data processing charges
  - 1x NAT Gateway: ~$45/month + data processing charges
  - Total: ~$225-250/month

- **Be ready to justify infrastructure choices based on cost, performance, and reliability trade-offs**

### 3. Soft Skills / Incident Management

**Interview Trap:** "The site is down. What do you do?"

**The Wrong Answer:** "Check CPU."

**The Right Answer:** "Check the status page, notify the team, then debug the issue."

**What to Learn:**

- **Incident Priority Levels:**
  - P1: Complete outage (0% availability)
  - P2: Major degradation (significant user impact)
  - P3: Minor issue (limited impact)

- **Incident Response Workflow:**
  1. **Assess:** Understand the scope and impact
  2. **Communicate:** Notify stakeholders (internal team, status page, customers)
  3. **Investigate:** Debug the root cause
  4. **Remediate:** Fix the issue
  5. **Document:** Create a post-mortem

- **Communication Best Practices:**
  - Use clear, non-technical language for stakeholders
  - Provide ETAs for resolution
  - Update customers periodically (don't go silent)

- **Post-Mortem Culture:**
  - Focus on "blameless retrospectives"—the goal is to improve systems, not blame people
  - Document lessons learned
  - Assign follow-up tasks to prevent recurrence

- **On-Call Rotations and Escalation Procedures:**
  - Understand who to call if you're stuck
  - Know when to escalate to senior engineers

---

## Project Filter Optimization: Building Interview-Worthy Projects

### Linux Project: From "Server Health Script" to "Alerting Script"

**Current:** A basic script that checks disk, CPU, and memory usage.

**Upgrade:** Have the script send a message to a Discord Webhook or Slack when disk usage > 80%. This shows you understand integrations and real-world operations.

**Implementation Details:**
- Use the Discord or Slack API to send notifications
- Include configurable thresholds for different metrics
- Add timestamp and hostname to alerts for context
- Document the setup process in your GitHub README
- Bonus: Set up as a cron job to run every 5 minutes with proper logging

```bash
#!/bin/bash
DISK_USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')
if [ $DISK_USAGE -gt 80 ]; then
    curl -X POST -H 'Content-type: application/json' \
        --data "{\"text\":\"Alert: Disk usage is ${DISK_USAGE}% on $(hostname)\"}" \
        $DISCORD_WEBHOOK_URL
fi
```

### Networking Project: From "Broken Server Debug" to "Troubleshooting Guide"

**Current:** Intentionally breaking a server and fixing security groups.

**Upgrade:** Document this in a GitHub README as a "Troubleshooting Guide." Screenshots of the error, the netstat command, the security group fix.

**Implementation Details:**
- Create a step-by-step guide with clear screenshots showing each error state
- Include the exact commands used (`netstat -tuln`, `aws ec2 describe-security-groups`)
- Show before and after security group configurations
- Explain the root cause and why the fix works
- Add a section on common networking issues and how to diagnose them
- Make it a reference guide that others can actually use

### CI/CD Project: From "Pipeline Only" to "Quality-Gated Pipeline"

**Current:** A basic pipeline that builds a Docker image, tests, and pushes to a registry.

**Upgrade:** Add a Linter (pylint, shellcheck) to the pipeline. If the code style is bad, the build fails. This shows you care about quality, not just deployment.

**Implementation Details:**
- Integrate a code linter into your CI pipeline
- Add pre-commit hooks that run linting locally (prevents pushing bad code)
- Set the pipeline to fail if linting fails, before any Docker build
- Include code formatting tools (black for Python, shfmt for Bash)
- Add a README section documenting code style requirements
- Bonus: Add security scanning (bandit for Python) to catch vulnerabilities early

### Project Ideas: One Proof Per Skill

Hiring managers value depth over breadth. Here are templated project ideas:

| Skill | Project | Description |
|-------|---------|-------------|
| Linux | Alerting Server Health Script | Checks disk, CPU, memory. Sends alerts to Discord/Slack when thresholds exceeded. Runs via cron. |
| Networking | Troubleshooting Guide | Document intentionally breaking ports, debugging, and fixing with exact commands and screenshots. |
| AWS | Public Web + Private DB | EC2 for web server, RDS in private subnet. Explain traffic flow and cost implications. |
| Docker | Dockerized Flask App | Multi-layer Dockerfile, .env configuration, persistent volumes, proper logging. |
| CI/CD | Quality-Gated Pipeline | Code linting, tests, security scanning. Pipeline fails if any quality check fails. |
| Terraform | Replaces Manual AWS | Use Terraform to provision the AWS setup from Week 4. Demonstrate clean destruction and recreation. |
| Python + Cloud | AWS Resource Manager | boto3 script to list instances older than 30 days, generate cost reports, or clean up unattached EBS volumes. |
| **CAPSTONE** | **3-Tier Architecture** | Web tier, app tier, database tier. VPC, Security Groups, ALB, RDS, CI/CD automation. **One project to demonstrate all skills.** |

---

## Key Concepts to Master for Interviews

### Git (Underweighted in Original Roadmaps)

You will be asked about Git. Prepare answers for:

- `git pull` vs. `git fetch`: Pull = Fetch + Merge. Fetch retrieves but doesn't merge.
- `rebase` vs. `merge`: Merge preserves history (merge commit). Rebase rewrites history (linear).
- How to resolve merge conflicts: Understand conflict markers and decision-making.
- Git branching strategies: GitFlow, trunk-based development.
- Pull request workflow: How code review ensures quality.
- Commit hygiene: Atomic commits with meaningful messages.

### Basic Application Understanding

You need to understand the application you're deploying. Be ready to answer:

- "What does this app do?" – Understand the core functionality
- "Where does the configuration live?" – Environment variables, config files, etc.
- "What is most likely to break first?" – Database connections, external APIs, file permissions
- Environment variables: How to pass configuration without hardcoding secrets
- Application logs: How to read and interpret logs for debugging
- Separation of concerns: Configuration separate from code (12-factor app methodology)

### Monitoring and Observability

It's not enough to know tool names. Understand the concepts:

- **What metrics matter?** CPU utilization, memory usage, latency (response time), error rates, throughput (requests/second)
- **Difference between logs, metrics, and alerts:**
  - **Logs:** Detailed, time-stamped records of events. Example: `2025-12-18 10:17:00 ERROR: Database connection timeout`
  - **Metrics:** Numeric representation of data measured over time. Example: CPU usage = 75%
  - **Alerts:** Notifications triggered when metrics cross thresholds. Example: "Alert: CPU > 90%"
- **The Monitoring Stack:** Prometheus (metrics collection) + Grafana (visualization) + Alertmanager (alerts). Or managed solutions like CloudWatch (AWS), Datadog, New Relic.

---

## Future Outlook: Beyond the Junior Role

The completion of this roadmap marks the beginning, not the end. The 2025 DevOps landscape is moving toward:

- **DevSecOps:** Integrating security early in the development process (not just at deployment)
- **FinOps:** Optimizing cloud costs, understanding cost drivers, implementing cost controls
- **Platform Engineering:** Building internal developer platforms (IDPs) that provide abstractions over infrastructure

A Junior Engineer who starts today with a strong foundation in Linux, AWS, Containers, and Automation is future-proofed. The demand for engineers who can not only build systems but understand them deeply enough to fix them when they break is insatiable.

**Execute the plan. Build the labs. Break the systems. Fix them.**

---

## Appendix: Summary of Deliverables & Timeline

| Phase | Duration | Core Topic | Key Tools | Primary Deliverable |
|-------|----------|-----------|-----------|-------------------|
| 1 | Weeks 1-2 | Linux & Shell | Bash, Vim, SSH, grep, systemd | Automated System Health Script (GitHub) |
| 2 | Week 3 | Networking | TCP/IP, DNS, SSH Keys | Passwordless SSH Setup Between VMs |
| 3 | Weeks 4-6 | AWS Cloud | IAM, EC2, VPC, S3, RDS | Manually Configured VPC & Web Server |
| 4 | Weeks 7-8 | Containers & Automation | Docker, Docker Compose, GitHub Actions, Terraform | Containerized Flask App + IaC Scripts |
| 5 | Week 9 | Kubernetes | Minikube, kubectl | Deployed App to Local K8s Cluster |
| 6 | Weeks 10-11 | Capstone | All of above | 3-Tier Web Architecture Project |
| 7 | Week 12 | Interview Prep | Resume, Aptitude, Mock Interviews | Job Applications & Interview Success |

---

## Comparative Analysis: Which Track Should You Follow?

| Feature | Service-Based (TCS, Infosys, Wipro) | Product-Based (Startups, SaaS, Tech Giants) |
|---------|-------------------------------------|------------------------------------------|
| **Primary Filter** | Aptitude Tests (Quant, Logic, Reasoning) | Technical Skills (Linux, Coding, Systems) |
| **Resume Focus** | Academic Score, Certifications | GitHub Portfolio, Live Projects, Blogs |
| **Starting Salary** | ₹3.5–5.5 LPA | ₹6.0–12.0+ LPA |
| **Role Allocation** | Random / Business Needs | Specific DevOps/SRE Role |
| **Interview Focus** | Communication, Basic Coding | Troubleshooting, System Design, War Stories |
| **Career Growth** | Slow initially, high stability | Rapid growth, high learning curve |
| **Your Path** | Pass aptitude → HR round → Allocated to DevOps later | Portfolio + Technical interview → Hired directly into DevOps |

**Recommendation:** Build for both. Focus 80% on technical skills (for product companies) and 20% on aptitude (for service-based companies). The technical skills will never hurt you in either track.

---

## Closing Thoughts

This roadmap is not theoretical. Every skill, project, and scenario has been tested against real job interviews and production environments. Freshers who follow this disciplined path consistently land offers in the ₹6-12 LPA range and prove themselves within the first 90 days.

The roadmap requires commitment: 12 weeks of focused learning, building, breaking, and fixing. But at the end, you will have a portfolio that speaks for itself, a technical foundation that compounds over years, and the troubleshooting intuition that separates junior engineers from "I just click buttons" folks.

The demand for DevOps engineers in India is insatiable. The supply of *good* ones is scarce. Be the latter.
