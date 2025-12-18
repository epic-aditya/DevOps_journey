https://github.com/milanm/DevOps-Roadmap?tab=readme-ov-file#learning-resources-for-devops-engineers-mostly-free
### **Phase 1: The Linux Foundation (Weeks 1-2)**

Goal: Stop using the mouse. Become comfortable in the black screen (Terminal).

Theory: The Cloud is just Linux servers accessed remotely.

#### **Checklist: Concepts to Master**

- [ ] **Virtualization:** Install Ubuntu Server on VirtualBox or use WSL2. Do not use the GUI.
    
- [ ] **Navigation:** `ls`, `cd`, `pwd`, `mkdir`, `rm`, `cp`, `mv`.
    
- [ ] **Permissions (Crucial):** Understand `chmod` & `chown`.
    
    - _Task:_ Explain why `777` is bad and `700` is good for SSH keys.
        
- [ ] **Process Management:** `top`, `ps`, `kill`.
    
    - _Task:_ Differentiate between `SIGTERM` (15) and `SIGKILL` (9).
        
- [ ] **Text Processing:** `grep`, `awk`, `cat`, `tail`.
    
    - _Task:_ Extract specific error codes from a log file.
        
- [ ] **Git Basics:** `pull`, `fetch`, `merge` vs `rebase`.
    

#### **🛠️ Practical Lab: The "System Health" Script**

Write a Bash script that runs automatically (cron job) to check server health.

1. **Script Logic:** Check Disk Usage. If usage > 80%, send an alert.
    
2. **Upgrade:** Instead of just printing to screen, make it send a message to a Discord/Slack webhook.
    
3. **Deliverable:** Push this script to a new GitHub repository.
    

---

### **Phase 2: Networking & Debugging (Week 3)**

Goal: Understand how computers talk to each other.

Theory: If you can't ping it, you can't deploy to it.

#### **Checklist: Concepts to Master**

- [ ] **IP Addressing:** Understand IPv4 and CIDR.
    
    - _Task:_ Calculate how many IPs are in a `/24` (256) vs a `/16` (65,536).
        
- [ ] **Ports:** Memorize the "Big 5": SSH (22), HTTP (80), HTTPS (443), MySQL (3306), DNS (53).
    
- [ ] **DNS:** Understand A Records and CNAME. Use `dig` or `nslookup` to trace a URL.
    
- [ ] **SSH Keys:** Public vs. Private keys. Why passwords are bad.
    

#### **🛠️ Practical Lab: Passwordless Entry**

1. **Setup:** Launch two simple Linux VMs (or containers).
    
2. **Action:** Generate an SSH key pair (`ssh-keygen`) on VM 1.
    
3. **Config:** Copy the _Public Key_ to VM 2's `authorized_keys` file.
    
4. **Test:** SSH from VM 1 to VM 2 without typing a password.
    

---

### **Phase 3: Core AWS - The Manual Way (Weeks 4-5)**

Goal: Build the infrastructure manually so you understand what automation solves later.

Theory: AWS is just a data center you rent via API.

#### **Checklist: Concepts to Master**

- [ ] **IAM (Security):** Create an Admin user with MFA. Stop using Root account.
    
- [ ] **EC2 (Compute):** Launch a `t2.micro` instance. SSH into it.
    
    - _Task:_ Understand Security Groups (Stateful firewalls).
        
- [ ] **VPC (Networking):** The hardest part. Understand Public vs. Private Subnets, Internet Gateways, and Route Tables.
    
- [ ] **S3 & RDS:** Create a storage bucket and a MySQL database instance.
    

#### **🛠️ Practical Lab: The Custom VPC**

_Do not use the Default VPC. Build this from scratch:_

1. Create a VPC (`10.0.0.0/16`).
    
2. Create **1 Public Subnet** and **1 Private Subnet**.
    
3. Attach an **Internet Gateway** to the Public Subnet.
    
4. Launch a Web Server (EC2) in the Public Subnet.
    
5. Launch a Database (RDS) in the Private Subnet.
    
6. **Verify:** The Web Server should be able to talk to the DB, but the DB cannot be reached directly from the internet.
    

---

### **Phase 4: Containers & CI/CD (Weeks 6-7)**

**Goal:** "It works on my machine" is not an excuse. Package code and automate testing.

#### **Checklist: Concepts to Master**

- [ ] **Docker:** Image vs. Container.
    
- [ ] **Dockerfile:** `FROM`, `RUN`, `COPY`, `CMD`.
    
- [ ] **Docker Compose:** Running multiple containers (App + DB) with one command.
    
- [ ] **CI/CD:** The pipeline: Code → Build → Test → Push.
    

#### **🛠️ Practical Lab: The Python Pipeline**

1. **App:** Write a tiny Python app (even just "Hello World").
    
2. **Docker:** Write a `Dockerfile` to package it.
    
3. **Automation:** Create a `.github/workflows/ci.yml` file in your repo.
    
4. **Pipeline Steps:**
    
    - Checkout code.
        
    - Lint code (Quality check).
        
    - Build Docker Image.
        
    - Push to Docker Hub.
        

---

### **Phase 5: Automation & Orchestration (Weeks 8-9)**

**Goal:** Stop clicking buttons. Infrastructure as Code (IaC).

#### **Checklist: Concepts to Master**

- [ ] **Terraform:** Declarative vs. Imperative.
    
    - _Task:_ Understand the `.tfstate` file (The Holy Grail).
        
- [ ] **Kubernetes (K8s):** Pods, Deployments, Services.
    
    - _Note:_ You don't need to master K8s deeply yet, just the concepts.
        

#### **🛠️ Practical Lab: Automate the Cloud**

1. **Terraform:** Write a Terraform script to recreate the **exact VPC setup** you built manually in Week 4.
    
2. **Kubernetes:** Install **Minikube**. Deploy your Python app (from Week 6) into Minikube using a `deployment.yaml`.
    

---

### **Phase 6: The Capstone & Job Hunt (Weeks 10-12)**

**Goal:** Synthesize everything into one project that gets you hired.

#### **🛠️ The Capstone Project: 3-Tier Web Architecture**

_This is the single most important thing in the roadmap._

1. **Infrastructure:** Use Terraform to create a VPC with Public/Private subnets.
    
2. **Database:** RDS MySQL in the Private Subnet.
    
3. **App:** Dockerized Python/Node application deployed on EC2 (or ECS).
    
4. **Networking:** Application Load Balancer (ALB) in Public Subnet routing traffic to the App.
    
5. **Automation:** GitHub Actions pipeline that updates the app automatically when you push code.
    
6. **Documentation:** A Diagram and "How-To" in your README.
    

#### **Job Hunt Checklist**

- [ ] **Resume:** Add keywords: _Terraform, CI/CD, AWS, Linux, Docker_. Link your GitHub Capstone.
    
- [ ] **Aptitude:** If targeting TCS/Infosys, spend 30 mins/day on Quant/Logic.
    
- [ ] **Scenario Prep:** Be ready to answer: "The server is slow, how do you debug?" (Answer: Scope -> Metrics -> Logs -> DB -> Network).
    

---

### **Summary of Your Flexible Workflow**

- **Monday-Wednesday:** Read the concepts, watch tutorials, and understand the "Why."
    
- **Thursday-Friday:** **Build the Lab.** Don't just read about it. If the Lab isn't working, you aren't done.
    
- **Weekend:** Review what broke. Update your Resume/GitHub with what you built.
    

Next Step for You:

Would you like me to generate the bash script code for the Week 1 Lab or the Terraform code for the Week 8 Lab so you can inspect the syntax?