# 🚀 16-Week DevOps Mastership: Indian Market Protocol (2026)

This repository tracks my progression through a **Strategic DevOps Roadmap** tailored for the Indian Junior Market. It transitions from manual "ClickOps" to fully automated, secure, and observable cloud architectures.

## 🏗️ The North Star: End-to-End Secure 3-Tier Deployment

The centerpiece of this repository is a production-grade 3-Tier Web Application deployment that demonstrates mastery over the full technology stack.

### **Architecture Overview**

* **Networking:** Custom VPC with Public/Private subnet isolation across multiple Availability Zones.
* **Security:** Traffic filtered through Security Groups (Stateful) and NACLs (Stateless), with secrets managed via AWS Secrets Manager.
* **Compute:** Dockerized React (Frontend) and Node.js/Java (Backend) services.
* **CI/CD:** Multi-stage GitHub Actions/Jenkins pipelines for automated testing, security scanning (Trivy), and deployment.
* **Infrastructure:** Provisioned entirely via Terraform (IaC) with remote state locking using S3 and DynamoDB.

---

## 📅 Roadmap Execution Protocol

### **Phase 1: The Iron Foundation (Weeks 1-4)**

* **Linux Internals:** Mastery of the boot process (GRUB/Systemd), permissions, and process signals (SIGTERM vs SIGKILL).
* **Networking:** Practical L4/L7 troubleshooting using `telnet`, `nc`, and `curl`.
* **Automation:** Scripting the "Holy Trinity" (grep, awk, sed) for log parsing.

### **Phase 2: Cloud & IaC Pillar (Weeks 5-8)**

* **AWS Mastery:** Manual architecture of VPCs, NAT Gateways, and Bastion Hosts before automation.
* **Containerization:** Implementation of Multi-Stage Docker builds to reduce image size by up to 80%.
* **Terraform:** Transitioning to Declarative IaC with modularized code.

### **Phase 3: The Automation Engine (Weeks 9-12)**

* **CI/CD Strategy:** Building Jenkins Pipeline-as-Code (Groovy) and modern GitHub Actions workflows.
* **Config Management:** Agentless configuration and server hardening using Ansible Playbooks.

### **Phase 4: Orchestration & Observability (Weeks 13-16)**

* **Kubernetes:** Deploying stateless/stateful applications with Pods, Deployments, and Services.
* **Observability:** Implementing the "Three Pillars" (Metrics, Logs, Traces) using Prometheus and Grafana.

---

## 🛠️ Tech Stack & Interview Differentiators

| Category | Tooling Focus | Why it matters in India? |
| --- | --- | --- |
| **Cloud** | AWS (EC2, S3, VPC, IAM) | Dominant market share for junior roles. |
| **CI/CD** | Jenkins + GitHub Actions | Jenkins for enterprise legacy; GHA for startups. |
| **Build** | Apache Maven | Essential for Indian service companies (Java ecosystem). |
| **IaC** | Terraform | Standard for Platform Engineering roles. |

---

## 📂 Project Structure

* `📂 Phase-1-Linux-Foundations/`: Shell scripts and system health monitors.
* `📂 Phase-2-Terraform-AWS/`: VPC and EC2 modules.
* `📂 Phase-3-Docker-K8s/`: Dockerfiles and K8s manifests.
* `📂 Phase-4-CICD-Pipelines/`: Jenkinsfiles and YAML workflows.

---
