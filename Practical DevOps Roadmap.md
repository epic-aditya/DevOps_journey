# **The Indian Fresher’s Definitive Handbook: A Practical, Execution-Ready DevOps Roadmap (2025-2026)**

## **Executive Summary: The Evolution of DevOps in the Indian Market**

The paradigm of software delivery in India has undergone a seismic shift, transitioning from the siloed operational models of the early 2010s to the integrated, high-velocity DevOps cultures of 2025\. For the Indian student or fresher, this shift represents both a formidable challenge and an unprecedented opportunity. The days when theoretical knowledge of the Software Development Life Cycle (SDLC) or a simple certification could secure an entry-level position at a major service consultancy or a burgeoning product startup are effectively over. The market in 2025, driven by rapid cloud migration and the ubiquity of microservices, demands execution capability from day one.1

Recruiters in major IT hubs—Bengaluru, Hyderabad, Pune, and NCR—report a saturation of "paper tigers": candidates possessing an alphabet soup of certifications but lacking the tactile familiarity with the command line interface (CLI) required to debug a production outage.1 Whether the target is a large-scale service provider managing legacy migrations or a cloud-native unicorn deploying hundreds of times a day, the expectation is that a fresher must be "deployable." This means possessing the ability to navigate a Linux server without a GUI, architect a secure network in AWS, and construct a CI/CD pipeline that not only builds code but intelligently handles failure.3

This report serves as a comprehensive, execution-ready roadmap designed specifically to bridge the gap between academic theory and industry reality. It eschews the passive consumption of video tutorials in favor of active, terminal-based construction. Following a rigorous 14-week progression, this roadmap is structured to transform a novice into a competent Junior DevOps Engineer capable of demonstrating value immediately. The curriculum is practical, aggressive, and rooted in the specific demands of the 2025 Indian job market, focusing on the "Big Eight" domains: Linux, Git, AWS, Docker, Kubernetes, Terraform, CI/CD, and Monitoring.

## ---

**Phase 1: The Linux Foundation (Weeks 1-2)**

### **Topic Name: Linux Systems Administration & Scripting**

The cloud, regardless of the provider—AWS, Azure, or Google Cloud—is fundamentally a fleet of virtualized Linux servers accessed remotely. A DevOps engineer who is uncomfortable in a terminal or reliant on a mouse is functionally useless during a critical incident. The first phase of this roadmap is not merely about memorizing commands; it is about developing a mental model of the operating system that underpins the entire internet infrastructure.4 In the Indian interview context, deep Linux knowledge is often used as a primary filter to separate serious engineers from casual learners.5

### **What to Learn (Actionable Checklist)**

1\. Virtualization and Environmental Setup  
The first step is to sever the dependency on the graphical user interface (GUI). The student must establish a practice environment that mirrors a headless server.

* **Virtual Machines (VMs):** Installing a Type-2 hypervisor like Oracle VirtualBox and deploying an Ubuntu Server ISO. This forces the user to interact solely via the shell.  
* **Windows Subsystem for Linux (WSL2):** For those on Windows, WSL2 provides a robust Linux kernel interface, though a dedicated VM is preferred for true isolation.4  
* **Terminal Emulators:** Moving beyond the default command prompt to tools like Windows Terminal, iTerm2, or Terminator to manage multiple shell sessions efficiently.

2\. The File System Hierarchy Standard (FHS)  
Understanding where files live is crucial for troubleshooting.

* **/etc:** The brain of the system where configuration files reside. Changing files here alters system behavior.  
* **/var/log:** The first destination during debugging. Understanding the rotation and structure of log files is mandatory.  
* **/bin vs /usr/bin:** Distinguishing between essential user binaries and system binaries.  
* **/proc:** The pseudo-filesystem that provides a window into the kernel state. Reading /proc/cpuinfo or /proc/meminfo is often required to gauge hardware health programmatically.

3\. User, Group, and Permission Management  
Security in Linux is defined by ownership and permission bits.

* **The Octal System:** Mastery of the numeric representation of permissions (Read=4, Write=2, Execute=1).  
* **User Management:** Creating users (useradd), assigning them to groups (usermod), and understanding the implications of the sudoers file.  
* **Security Implications:** One must be able to explain, in an interview setting, why permissions like 777 (read/write/execute for everyone) are catastrophic for security, whereas 400 or 600 are strictly required for SSH keys.4

4\. Process Management and Signals  
DevOps engineers often need to terminate runaway processes or restart stuck services.

* **Process Lifecycle:** Understanding PID (Process ID) and PPID (Parent Process ID).  
* **Signals:** Differentiating between a graceful termination request (SIGTERM \- 15\) which allows a process to save data/close connections, and a forceful kill (SIGKILL \- 9\) which instantly removes the process from the CPU scheduler. Relying solely on kill \-9 is a mark of inexperience.4  
* **Background Jobs:** Managing jobs using &, bg, fg, and jobs.

5\. Text Processing and Stream Redirection  
Log analysis is a daily task. One cannot open a 5GB log file in Notepad.

* **The Filter Pipeline:** Combining grep (search), awk (column manipulation), sed (stream editing), sort, and uniq to extract meaningful insights from massive text streams.  
* **Redirection:** Understanding standard input (stdin, 0), standard output (stdout, 1), and standard error (stderr, 2), and how to route them using \>, \>\>, and 2\>&1.

6\. Shell Scripting (Bash)  
Automation begins with Bash.

* **Shebang:** The significance of \#\!/bin/bash.  
* **Control Structures:** If-Else conditions for decision making and For/While loops for iteration.  
* **Exit Codes:** Every command returns a status code ($?). A code of 0 means success; anything else indicates failure. Building robust scripts requires checking these codes at every step.6

### **Practical Tasks (Terminal-based)**

**Task 1.1: The Secure Directory Structure**

* **Goal:** Enforce strict permission boundaries.  
* **Execution:**  
  1. Navigate to the /tmp directory.  
  2. Create a nested directory structure: project/logs, project/conf, and project/bin.  
  3. Create a dummy user named devops\_intern.  
  4. Change the ownership of the entire project directory to devops\_intern using chown \-R.  
  5. Set the permissions such that only the owner has full read/write/execute access, the group has read-only access, and others have absolutely no access. This corresponds to 740\.  
  6. **Verification:** Switch to a different user (e.g., guest or your main user) and attempt to cd into the directory or ls its contents. The system must return Permission denied.

**Task 1.2: The Zombie Process Hunt**

* **Goal:** Manage background processes and signals.  
* **Execution:**  
  1. Start a long-running dummy process in the background: sleep 1000 &.  
  2. Use ps aux | grep sleep to locate the Process ID (PID) of the command.  
  3. Attempt to stop the process gracefully using kill \-15 \<PID\>. Observe if it terminates.  
  4. Launch the process again. This time, simulate a hung process by ignoring the standard termination (conceptually) and force kill it using kill \-9 \<PID\>.  
  5. **Interview Insight:** Be prepared to explain that SIGKILL prevents the process from cleaning up resources like open file descriptors or database connections.4

**Task 1.3: SSH Key generation and transfer**

* **Goal:** Passwordless authentication, a prerequisite for automation tools like Ansible.  
* **Execution:**  
  1. On your local machine or VM, generate an RSA key pair: ssh-keygen \-t rsa \-b 4096\.  
  2. Inspect the created files: id\_rsa (Private \- keep secret) and id\_rsa.pub (Public \- shareable).  
  3. Check the permissions of id\_rsa. If it is not read-only for the user (400 or 600), the SSH client will refuse to use it.  
  4. (Optional) If you have a second VM, use ssh-copy-id to transfer the public key and log in without a password.

### **Mini/Short Project (GitHub-ready)**

**Project Title: Automated System Health Monitor**

**Context:** In a production environment, you cannot manually check if a server is running out of disk space. You need an automated agent. This project builds a primitive version of such an agent using Bash.4

**Requirements:**

1. **Resource Checking:** The script must use commands like df \-h (Disk Free), free \-m (Memory), and top or uptime (CPU Load) to gather metrics.  
2. **Logic Thresholds:** Define variables for thresholds (e.g., DISK\_THRESHOLD=80). Use if statements to check if current usage exceeds these limits.  
3. **Alerting Mechanism:** If a threshold is breached, the script must send a notification. Integrate with a communication platform like Slack or Discord using their Incoming Webhook API. Use curl to send a JSON payload with the alert message.  
4. **Automation:** The script is useless if run manually. Add an entry to the crontab to execute this script every 5 minutes (\*/5 \* \* \* \*).

**Deliverables:**

* A GitHub repository named bash-system-monitor.  
* The script file monitor.sh with extensive comments explaining the logic.  
* A README.md file detailing how to generate the webhook URL and how to install the cron job.

## ---

**Phase 2: Version Control & Collaboration (Week 3\)**

### **Topic Name: Advanced Git & GitHub Workflows**

Git is the single source of truth for modern DevOps. It is the mechanism by which Infrastructure as Code is managed, application code is deployed, and collaboration occurs. In the Indian market, interviewers often skip basic commands like git push and focus on scenario-based questions involving conflict resolution, branching strategies, and history manipulation to filter out candidates who have only worked on solo projects.4

### **What to Learn (Actionable Checklist)**

**1\. The Git Architecture**

* **The Three States:** Understanding the transition of files from the Working Directory to the Staging Area (Index) and finally to the Local Repository (Commit).  
* **Head & Pointers:** Understanding that HEAD is simply a pointer to the current branch reference.

**2\. Branching Strategies**

* **Git Flow:** A strict branching model with master, develop, feature/\*, release/\*, and hotfix/\* branches. Common in legacy enterprise environments.  
* **Trunk Based Development:** A modern approach favored by high-velocity DevOps teams where developers merge into a single main branch frequently, often using feature flags.  
* **Feature Branch Workflow:** Creating a specific branch for every ticket/issue, which is then merged via Pull Request.

**3\. Advanced History Manipulation**

* **Reset vs. Revert:** git reset moves the branch pointer backward, potentially erasing history (dangerous on shared branches). git revert creates a *new* commit that is the inverse of a previous one, preserving history (safe for shared branches).9  
* **Merge vs. Rebase:** git merge preserves the history of when branches diverged and converged, creating a "merge bubble." git rebase rewrites history to make it linear, as if the changes happened sequentially. Rebase is preferred for cleaner logs but requires caution.10  
* **Cherry-Pick:** The ability to select a specific commit from one branch and apply it to another (e.g., applying a hotfix from main to a release branch).

**4\. Collaboration Etiquette**

* **Pull Requests (PRs):** The standard mechanism for code review.  
* **Merge Conflicts:** The inevitability of two people changing the same line of code. Resolving these manually is a core skill.  
* **.gitignore:** Ensuring sensitive data (API keys, build artifacts, node\_modules) is never committed.

### **Practical Tasks (Terminal-based)**

**Task 2.1: The Merge Conflict Simulator**

* **Goal:** Become comfortable resolving code conflicts manually.  
* **Execution:**  
  1. Initialize a repo and create app.py on the main branch with the content print("Hello World"). Commit it.  
  2. Create a new branch feature-login. Change the line to print("Login Page Logic"). Commit.  
  3. Switch back to main. Change the same line to print("Dashboard Logic"). Commit.  
  4. Attempt to merge feature-login into main (git merge feature-login).  
  5. Git will pause and report a CONFLICT.  
  6. Open the file in an editor (Vim/Nano/VS Code). Locate the conflict markers (\<\<\<\<\<\<\< HEAD, \=======, \>\>\>\>\>\>\>).  
  7. Decide which code to keep (or combine them). Delete the markers.  
  8. Add the file and complete the commit.10

**Task 2.2: The "Oops" Recovery**

* **Goal:** Learn to undo mistakes without panic.  
* **Execution:**  
  1. Create a file, add content, and commit it.  
  2. Realize this was a mistake. Use git reset \--soft HEAD\~1. Verify that the commit is gone but the file changes remain in the staging area.  
  3. Commit again.  
  4. Now use git reset \--hard HEAD\~1. Verify that both the commit and the file changes are completely destroyed.  
  5. **Insight:** This distinction is critical when managing local development versus pushing to remote servers.

### **Mini/Short Project (GitHub-ready)**

**Project Title: Simulated Team Collaboration Repo**

**Context:** Simulate a multi-developer environment to demonstrate workflow proficiency.

**Requirements:**

1. **Repo Setup:** Create a repository with a comprehensive README.md and a .gitignore file specific to a language (e.g., Python or Node).  
2. **Branching:** Create two distinct branches: feature/frontend and feature/backend.  
3. **Development:** Make unique commits in both branches.  
4. **Pull Request:** Push both branches to GitHub. Open a Pull Request (PR) for each against main.  
5. **Simulation:** In the GitHub UI, merge one PR. Then, try to merge the second PR. If there is a conflict, resolve it within the GitHub UI or locally.  
6. **Visualization:** Take a screenshot of the "Network Graph" (Insights tab) on GitHub showing the divergence and convergence of branches.

**Deliverables:**

* The GitHub repository link.  
* The screenshot embedded in the README demonstrating the branching history.

## ---

**Phase 3: Core AWS Infrastructure (Weeks 4-5)**

### **Topic Name: Networking & Compute (The Manual Way)**

Before automating infrastructure with code, one must understand the physical and logical layout of the cloud. AWS is the dominant player in the Indian market.1 The focus of this phase is on the Virtual Private Cloud (VPC). Networking is often the weakest area for freshers, yet it is the most common source of failure in production environments.

### **What to Learn (Actionable Checklist)**

**1\. Identity & Access Management (IAM)**

* **Root Account:** Why it should be locked away and never used for daily tasks.  
* **Users, Groups, Roles:** Understanding the relationship between these entities.  
* **Policies:** JSON documents that define permissions. The Principle of Least Privilege (giving a user only what they need) is a key interview topic.  
* **MFA:** Multi-Factor Authentication as a non-negotiable security standard.4

**2\. Virtual Private Cloud (VPC) \- The Network Layer**

* **CIDR Blocks:** Classless Inter-Domain Routing. You must be able to calculate IP ranges. For example, knowing that /16 gives 65,536 IPs and /24 gives 256 IPs.  
* **Subnets:** The logic behind Public Subnets (direct internet access) vs. Private Subnets (no direct access).  
* **Gateways:** Internet Gateway (IGW) for public traffic. NAT Gateway for allowing private instances to update without being exposed to inbound connections.  
* **Route Tables:** The "GPS" of the VPC, directing traffic between subnets and gateways.

**3\. Elastic Compute Cloud (EC2)**

* **Instance Types:** Understanding the naming convention (e.g., t2.micro: t=family, 2=generation, micro=size).  
* **Security Groups:** These act as stateful firewalls at the instance level. "Stateful" means if you allow a request out, the response is automatically allowed back in.  
* **NACLs:** Network Access Control Lists, which are stateless firewalls at the subnet level.  
* **Storage:** EBS (Elastic Block Store) for persistent data vs. Instance Store for ephemeral data.4

### **Practical Tasks (Terminal-based)**

**Task 3.1: The Custom Network Build**

* **Goal:** Build a production-grade network from scratch (No "Default VPC").  
* **Execution:**  
  1. Create a VPC with CIDR 10.0.0.0/16.  
  2. Create a **Public Subnet** (10.0.1.0/24) and a **Private Subnet** (10.0.2.0/24).  
  3. Create an Internet Gateway (IGW) and attach it to the VPC.  
  4. Create a Public Route Table. Add a route 0.0.0.0/0 pointing to the IGW. Associate this table with the Public Subnet.  
  5. **Verification:** Launch an EC2 instance (Ubuntu) in the Public Subnet. Ensure "Auto-assign Public IP" is enabled. SSH into it. If you can connect, your networking is correct.

**Task 3.2: The Bastion Host Pattern**

* **Goal:** Securely access private resources.  
* **Execution:**  
  1. Launch a second EC2 instance (Database placeholder) in the **Private Subnet**. Do *not* assign a Public IP.  
  2. Attempt to SSH into this private instance directly from your laptop. It will fail (timeout).  
  3. SSH into the Public instance (Bastion Host) first.  
  4. From the Bastion Host, SSH into the Private instance using its Private IP (ssh \-i key.pem ubuntu@10.0.2.x).  
  5. **Insight:** This "Jump Server" pattern is standard in secure corporate environments to minimize the attack surface.4

### **Mini/Short Project (GitHub-ready)**

**Project Title: AWS Architecture Documentation**

**Context:** Since this phase is manual ClickOps, the artifact is documentation. Clear documentation is a highly valued soft skill.

**Requirements:**

1. **Diagramming:** Use a tool like Draw.io or Lucidchart to create a visual representation of the network built in Task 3.1 & 3.2.  
2. **Detailing:** Clearly label the VPC CIDR, Subnet CIDRs, Route Tables, IGW, and the flow of traffic (SSH paths).  
3. **Guide:** Write a AWS\_SETUP.md file. It should be a step-by-step "Runbook" that would allow another engineer to recreate your setup manually.

**Deliverables:**

* A GitHub repository containing the .md file and the architecture diagram (exported as PNG).

## ---

**Phase 4: Containerization (Weeks 6-7)**

### **Topic Name: Docker & Container Optimization**

Docker resolves the "it works on my machine" dilemma. However, in 2025, simply writing a Dockerfile is insufficient. Candidates must understand image optimization, security scanning, and networking. The ability to distinguish between "Images" (read-only templates) and "Containers" (runnable instances) is fundamental.4

### **What to Learn (Actionable Checklist)**

**1\. Docker Fundamentals**

* **The Docker Engine:** Daemon, REST API, and CLI.  
* **Image Layers:** Understanding that images are built in layers. Changing a line of code at the top of a Dockerfile invalidates the cache for all subsequent layers.  
* **Commands:** FROM, RUN, COPY, ADD, WORKDIR, CMD vs ENTRYPOINT, EXPOSE.

**2\. Optimization Techniques**

* **Multi-Stage Builds:** The gold standard for production images. Using a heavy image (like Maven or GCC) to build the artifact, and then copying only the binary/JAR to a tiny runtime image (like Alpine or Distroless). This can reduce image size from 800MB to 50MB.12  
* **Layer Caching:** Organizing the Dockerfile to maximize cache hits (e.g., copying package.json and running npm install *before* copying the rest of the source code).

**3\. Networking & Storage**

* **Networks:** Bridge (default), Host (performance), and Overlay (swarm/k8s).  
* **Volumes:** Bind Mounts (linking host files) vs. Docker Volumes (managed storage). Understanding data persistence is key.

**4\. Orchestration (Local)**

* **Docker Compose:** Defining multi-container applications (e.g., App \+ Database) in a single YAML file to streamline local development.4

### **Practical Tasks (Terminal-based)**

**Task 4.1: The Optimization Challenge**

* **Goal:** drastically reduce image size.  
* **Execution:**  
  1. Create a simple Node.js or Python application.  
  2. Write a "Naive" Dockerfile using a standard base image (e.g., FROM node:18). Build it and check the size (docker images). It will likely be \>800MB.  
  3. Refactor using **Multi-Stage Builds**.  
     * **Stage 1 (Builder):** FROM node:18 AS builder. Install dependencies and build.  
     * **Stage 2 (Runner):** FROM node:18-alpine. Copy only the node\_modules and source code from the builder stage.  
  4. Build again. The size should drop to \<200MB.  
  5. **Interview Insight:** Be ready to explain *why* smaller images matter (faster deployments, smaller attack surface, lower storage costs).12

**Task 4.2: Docker Compose Orchestration**

* **Goal:** Spin up a stack with dependencies.  
* **Execution:**  
  1. Create docker-compose.yml.  
  2. **Service 1 (App):** Uses the Dockerfile from Task 4.1. Maps port 5000:5000.  
  3. **Service 2 (DB):** Use a redis:alpine image.  
  4. **Networking:** In the App code, connect to Redis using the hostname redis (service name), not localhost.  
  5. Run docker-compose up \-d. Verify the app can increment a counter in Redis.

### **Mini/Short Project (GitHub-ready)**

**Project Title: Containerized Python Flask App with Redis**

**Context:** A simple 2-tier application demonstrating connectivity between containers.

**Requirements:**

1. **Application:** A Python Flask app that connects to a Redis instance. Every time the root URL (/) is hit, it increments a "Visit Counter" in Redis and displays it.  
2. **Infrastructure:** A Dockerfile implementing multi-stage builds. A docker-compose.yml to launch both Flask and Redis.  
3. **Environment Variables:** Do not hardcode the Redis host/port. Inject them via ENV variables in the Dockerfile/Compose file.

**Deliverables:**

* Repo with app.py, requirements.txt, Dockerfile, docker-compose.yml.  
* A screenshot in README.md showing the browser with the text "Number of visits: X".

## ---

**Phase 5: Orchestration (Weeks 8-9)**

### **Topic Name: Kubernetes (K8s)**

If Docker is the shipping container, Kubernetes is the crane and the cargo ship. It is the operating system of the cloud. This phase has the steepest learning curve. Focus on the core objects used by application developers and DevOps engineers. Do not get bogged down in cluster administration (setting up K8s from scratch) initially; focus on *using* the cluster.4

### **What to Learn (Actionable Checklist)**

**1\. Architecture**

* **Control Plane:** The brain. Includes the API Server (frontend), Scheduler (decides where pods go), Controller Manager (brain), and Etcd (memory/storage).  
* **Worker Nodes:** The muscle. Includes Kubelet (agent), Kube-proxy (network), and Container Runtime (Docker/Containerd).

**2\. Core Objects (The Primitives)**

* **Pod:** The smallest deployable unit. Usually one container per pod, but can have sidecars.  
* **ReplicaSet:** Ensures a specified number of pod copies are running.  
* **Deployment:** The standard way to manage stateless apps. Handles rolling updates and rollbacks.14  
* **Service:** The networking abstraction. ClusterIP (internal), NodePort (external via node IP), LoadBalancer (cloud native).  
* **Ingress:** An HTTP/HTTPS router that sits in front of services, handling domains and paths.15  
* **ConfigMaps & Secrets:** Decoupling configuration from the container image.

**3\. Deployment Strategies**

* **Rolling Update:** The default. Replaces pods gradually (e.g., 1 by 1\) to ensure zero downtime.  
* **Recreate:** Kills all old pods, then starts new ones. Simpler, but causes downtime.17

**4\. Debugging**

* **CrashLoopBackOff:** The container is starting and dying repeatedly. Often due to config errors or missing dependencies.19  
* **ImagePullBackOff:** The node cannot fetch the image (typo, auth error, or network).

### **Practical Tasks (Terminal-based)**

**Task 5.1: The Minikube Setup**

* **Goal:** Create a local playground.  
* **Execution:**  
  1. Install Minikube and Kubectl.4  
  2. Start the cluster: minikube start \--driver=docker.  
  3. Verify: kubectl get nodes.

**Task 5.2: Imperative vs. Declarative**

* **Goal:** Understand YAML manifests.  
* **Execution:**  
  1. Run a pod imperatively: kubectl run nginx \--image=nginx. Delete it.  
  2. Create a file nginx-deployment.yaml. Define a Deployment with 3 replicas.  
  3. Apply it: kubectl apply \-f nginx-deployment.yaml.  
  4. Kill a pod manually: kubectl delete pod \<pod-name\>.  
  5. Observe the magic: kubectl get pods \-w. Kubernetes will instantly start a new pod to maintain the desired state of 3 replicas.

**Task 5.3: The Broken Deployment (Debugging Drill)**

* **Goal:** Fix a CrashLoopBackOff.  
* **Execution:**  
  1. Modify your deployment YAML. Change the command to something invalid, or point to a non-existent image tag.  
  2. Apply the change.  
  3. Observe the status ImagePullBackOff or CrashLoopBackOff.  
  4. Debug: kubectl describe pod \<pod-name\> (Check Events). kubectl logs \<pod-name\> (Check application logs).21

### **Mini/Short Project (GitHub-ready)**

**Project Title: K8s Deployment Manifests with Rolling Update**

**Context:** Define the infrastructure for the Python app from Phase 4 using K8s.

**Requirements:**

1. **Manifests:** Create a folder k8s/ containing:  
   * redis-deployment.yaml (1 replica) & redis-service.yaml (ClusterIP).  
   * app-deployment.yaml (3 replicas) & app-service.yaml (NodePort).  
2. **Configuration:** Inject the Redis hostname into the App deployment using environment variables (value: "redis-service").  
3. **Strategy:** Explicitly define a strategy: RollingUpdate in the app deployment.

**Deliverables:**

* A repo containing the YAML files.  
* A guide on how to apply them to Minikube and access the app via minikube service app-service.

## ---

**Phase 6: Infrastructure as Code (Week 10\)**

### **Topic Name: Terraform**

The era of "ClickOps" (manually clicking in the AWS console) is ending. Terraform allows engineers to define infrastructure as code (IaC), making it versionable, repeatable, and auditable. This is a critical skill for Indian service companies (TCS, Wipro, Infosys) that manage massive cloud estates for global clients.1

### **What to Learn (Actionable Checklist)**

**1\. Core Concepts**

* **Providers:** Plugins that allow Terraform to talk to APIs (AWS, Azure, GitHub).  
* **Resources:** The infrastructure blocks (e.g., aws\_instance, aws\_s3\_bucket).  
* **HCL (HashiCorp Configuration Language):** The syntax used to write Terraform files (.tf).

**2\. State Management**

* **The State File (terraform.tfstate):** The "Holy Grail" that maps your code to real-world resources.  
* **Remote Backend:** Storing the state file in an S3 bucket instead of the local laptop. This is mandatory for team collaboration.22  
* **State Locking:** Using a DynamoDB table to lock the state file, preventing two engineers from applying changes simultaneously and corrupting the state.23

**3\. The Workflow**

* terraform init: Downloads providers.  
* terraform plan: Preview changes (Dry run).  
* terraform apply: Execute changes.  
* terraform destroy: Tear everything down.

### **Practical Tasks (Terminal-based)**

**Task 6.1: Automating the VPC**

* **Goal:** Replicate Phase 3 using code.  
* **Execution:**  
  1. Create main.tf, variables.tf, outputs.tf.  
  2. Define the AWS Provider.  
  3. Write resources for: aws\_vpc, aws\_subnet (Public), aws\_internet\_gateway, and aws\_route\_table.  
  4. Use variables for the CIDR blocks (don't hardcode).  
  5. Run terraform plan and terraform apply.

**Task 6.2: Remote State Lockdown**

* **Goal:** Configure a production-grade backend.  
* **Execution:**  
  1. Manually create an S3 bucket (e.g., my-terraform-state-2025) and a DynamoDB table (Partition key: LockID).  
  2. In your main.tf, add a backend "s3" block pointing to these resources.  
  3. Run terraform init. It will ask to migrate your local state to S3. Say yes.  
  4. **Interview Insight:** This is the standard answer to "How do you manage Terraform state in a team?".25

### **Mini/Short Project (GitHub-ready)**

**Project Title: One-Click AWS Infrastructure**

**Context:** Provision a web server environment instantly.

**Requirements:**

1. **Code:** Terraform scripts to provision a VPC, a public subnet, an Internet Gateway, and an EC2 instance.  
2. **Security:** A Security Group attached to the EC2 instance allowing ports 22 (SSH) and 80 (HTTP).  
3. **Bootstrapping:** Use the user\_data field in the EC2 resource to install Nginx automatically upon startup.  
4. **Output:** The script must output the Public IP of the instance after completion.

**Deliverables:**

* A repo with the .tf files.  
* A screenshot of the terraform apply complete message showing the IP address.

## ---

**Phase 7: CI/CD Pipeline Mastery (Week 11\)**

### **Topic Name: Jenkins & GitHub Actions**

Continuous Integration and Continuous Deployment (CI/CD) is the factory assembly line for code. You need exposure to both the "Old Guard" (Jenkins), which dominates legacy enterprise, and the "New Standard" (GitHub Actions), which is preferred by startups and open-source projects.

### **What to Learn (Actionable Checklist)**

**1\. Jenkins (The Enterprise Standard)**

* **Master-Slave Architecture:** Understanding how the Master schedules jobs and Agents (Slaves) execute them. This is vital for scalability.26  
* **Declarative Pipelines:** Writing Jenkinsfile using the pipeline { agent any stages {... } } syntax.  
* **Plugins:** The ecosystem (Docker plugin, Git plugin).

**2\. GitHub Actions (The Modern Standard)**

* **Workflow YAML:** The structure of .github/workflows.  
* **Runners:** GitHub-hosted runners (Ubuntu/Windows) vs. Self-hosted runners (your own EC2).  
* **Matrix Builds:** Running tests on multiple versions of a language simultaneously (e.g., Node 14, 16, 18).28  
* **Secrets:** Managing credentials (${{ secrets.AWS\_ACCESS\_KEY }}) securely.

### **Practical Tasks (Terminal-based)**

**Task 7.1: The Jenkins Setup**

* **Goal:** Run a local CI server.  
* **Execution:**  
  1. Run Jenkins using Docker: docker run \-p 8080:8080 \-p 50000:50000 jenkins/jenkins:lts.  
  2. Access localhost:8080, unlock using the initial admin password.  
  3. Install "Suggested Plugins".  
  4. Create a "Pipeline" job. Connect it to your GitHub repo.

**Task 7.2: GitHub Actions Matrix**

* **Goal:** Advanced testing patterns.  
* **Execution:**  
  1. In your "Simulated Collaboration Repo" (Phase 2), create .github/workflows/ci.yml.  
  2. Define a strategy: matrix with node-version: \[14.x, 16.x, 18.x\].  
  3. Step: npm install and npm test.  
  4. Push code. Watch 3 jobs start in parallel in the "Actions" tab.

### **Mini/Short Project (GitHub-ready)**

**Project Title: End-to-End CI/CD Pipeline**

**Context:** Automate the "Commit to Deploy" path.

**Requirements:**

1. **Source:** Your Python Flask app from Phase 4\.  
2. **Platform:** GitHub Actions.  
3. **Pipeline Steps:**  
   * **Lint:** Check code quality (e.g., pylint).  
   * **Build:** Build the Docker image.  
   * **Test:** Run a dummy unit test.  
   * **Push:** Log in to Docker Hub and push the image.  
4. **Tagging:** Use the Git Commit SHA (${{ github.sha }}) to tag the Docker image. This ensures every build is unique and traceable.

**Deliverables:**

* The .github/workflows/main.yml file.  
* The "Passing" green badge added to the README.

## ---

**Phase 8: Observability (Week 12\)**

### **Topic Name: Prometheus & Grafana**

"If you can't measure it, you can't manage it." In a DevOps role, once the code is deployed, the job shifts to monitoring. You must understand the "Three Pillars of Observability": Metrics, Logs, and Traces.

### **What to Learn (Actionable Checklist)**

**1\. Concepts**

* **Metrics:** Numerical data over time (e.g., CPU Usage \= 80%).  
* **Logs:** Text records of events (e.g., "Error: Connection Timeout").  
* **Traces:** Tracking a request as it hops between microservices.

**2\. The Stack (Prometheus \+ Grafana)**

* **Prometheus:** A time-series database that *pulls* (scrapes) metrics from targets.  
* **Node Exporter:** A small agent installed on Linux servers that exposes hardware metrics (Disk, RAM, CPU) to Prometheus.30  
* **Grafana:** The visualization layer. It queries Prometheus and turns data into beautiful dashboards.31

### **Practical Tasks (Terminal-based)**

**Task 8.1: The Monitoring Stack**

* **Goal:** Visualize local machine health.  
* **Execution:**  
  1. Create a docker-compose.yml that includes prom/prometheus, grafana/grafana, and prom/node-exporter.  
  2. Configure prometheus.yml to scrape the Node Exporter target (usually port 9100).  
  3. Run docker-compose up.  
  4. Access Grafana (localhost:3000). Add Prometheus as a Data Source.  
  5. Import Dashboard ID 1860 (Node Exporter Full).  
  6. **Result:** You should see live graphs of your computer's CPU and RAM usage.

### **Mini/Short Project (GitHub-ready)**

**Project Title: Infrastructure Monitoring Dashboard**

**Context:** Prove you can set up observability.

**Requirements:**

1. **Setup:** The Docker Compose stack from Task 8.1.  
2. **Customization:** Create a custom Grafana panel that shows "Free Memory" in a Gauge format.  
3. **Alerting (Bonus):** Configure a basic alert in Grafana: "If CPU \> 90% for 5 mins, send email."

**Deliverables:**

* A repository with the compose file and config.  
* Screenshots of the dashboard in the README.

## ---

**Phase 9: The Capstone Project (Weeks 13-14)**

### **Topic Name: The "Resume-Defining" 3-Tier Application**

This project is the convergence of all previous skills. It is the centerpiece of your portfolio. When an interviewer asks, "Tell me about a project you worked on," this is the answer. It simulates a real-world microservices architecture deployed on the cloud.33

### **Architecture Overview**

* **Frontend:** React.js (User Interface).  
* **Backend:** Node.js or Python Flask (API).  
* **Database:** MongoDB or MySQL (Persistent Data).  
* **Infrastructure:** AWS EKS (Kubernetes) or Minikube.  
* **Orchestration:** Kubernetes Deployments and Services.  
* **Automation:** GitHub Actions Pipeline.

### **Execution Steps**

**Step 1: The Application Code**

* Create a simple React app that has a form.  
* Create an API that accepts data from the form and saves it to the Database.  
* Containerize both Frontend and Backend using optimized Dockerfiles (Multi-stage).

**Step 2: Kubernetes Manifests**

* **Database:** Deploy MongoDB using a **StatefulSet** (crucial for DBs) and a **PersistentVolume** (PV) so data survives pod restarts. Create a **Headless Service** for stable network identity.  
* **Backend:** Deploy as a **Deployment**. Use **Secrets** to inject the DB credentials. Expose via **ClusterIP** service (internal only).  
* **Frontend:** Deploy as a **Deployment**. Expose via **LoadBalancer** service (or Ingress) to make it accessible to the world.

**Step 3: Infrastructure (IaC)**

* Use Terraform to provision the AWS EKS cluster (or the EC2 instance hosting Minikube). Do not create the cluster manually in the console.

**Step 4: The CI/CD Pipeline**

* Create a GitHub Actions workflow that triggers on a push to main.  
* **Build:** Create new Docker images for Frontend and Backend.  
* **Tag:** Tag them with the Commit SHA.  
* **Push:** Upload to Docker Hub.  
* **Deploy:** Update the Kubernetes deployment to use the new image tag. (You can use kubectl set image or a GitOps tool like ArgoCD if advanced).

### **Deliverable**

A single GitHub repository DevOps-Capstone-Project with the following structure:

* /terraform: Infrastructure code.  
* /k8s: Kubernetes YAML manifests.  
* /frontend: React code \+ Dockerfile.  
* /backend: API code \+ Dockerfile.  
* .github/workflows: CI/CD pipeline.  
* README.md: **Critical.** A comprehensive guide containing:  
  * Architecture Diagram.  
  * Prerequisites.  
  * One-command setup instructions.  
  * Screenshots of the app running.

## ---

**Phase 10: Career Readiness & Indian Market Strategy**

### **Topic Name: Resume & Interview Prep**

Technical skills alone are insufficient. You must package them effectively.

### **Resume Optimization (ATS Friendly)**

Indian recruiters often use Applicant Tracking Systems (ATS) or keyword searches.

* **Do not list:** "Basic knowledge of C++", "Hard worker", "Fast learner".  
* **Do list (Keywords):** "CI/CD Pipelines", "Infrastructure as Code", "AWS EKS", "Docker Optimization", "State Management", "Incident Response".  
* **Impact Statements:** Instead of "Used Jenkins," write "Reduced deployment time by 40% by implementing a multi-stage Jenkins pipeline with parallel execution.".36

### **The "Experience" Gap Strategy**

Freshers often face the paradox: "Need experience to get a job."  
Solution: Treat your Capstone Project as your experience.

* **Scenario:** When asked, "Tell me about a technical challenge you faced."  
* **Answer:** "While deploying my 3-Tier application on EKS, my backend pods kept entering a CrashLoopBackOff state. I used kubectl logs to debug and realized the backend was trying to connect to the Database before the DB pod was ready. I implemented an initContainer in the backend deployment to check for DB connectivity before the main application container started. This resolved the race condition.".19

### **Comparative Tool Analysis Table for Freshers**

| Tool Category | "Legacy" / Enterprise (Service Based) | Modern / Startup (Product Based) | Roadmap Recommendation |
| :---- | :---- | :---- | :---- |
| **OS** | RHEL / CentOS | Ubuntu / Alpine | **Ubuntu** (Market standard) |
| **CI/CD** | Jenkins | GitHub Actions / GitLab CI | **GitHub Actions** (Low barrier, high value) |
| **Container** | Docker | Docker / Podman | **Docker** (Non-negotiable) |
| **Orchestrator** | OpenShift | Kubernetes (EKS/GKE) | **Kubernetes** (The gold standard) |
| **IaC** | CloudFormation | Terraform / Pulumi | **Terraform** (Cross-cloud) |
| **Monitoring** | Nagios / Splunk | Prometheus / Grafana | **Prometheus \+ Grafana** |

## **Conclusion**

This roadmap is demanding because the market is demanding. The transition from student to DevOps Engineer requires a shift in mindset from "consuming information" to "building systems." The completion of the **Capstone Project**, and the ability to articulate the "why" behind every architectural decision in it, is the primary differentiator between a generic applicant and a hired engineer in the competitive Indian IT landscape. Start at Phase 1, respect the progression, and build with your hands. Good luck.
