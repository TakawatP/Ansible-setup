# DevOps & Infrastructure Engineer Skills

## Executive Summary
วิศวกรสาย DevOps และ Infrastructure ที่มีความเชี่ยวชาญสูงในการบริหารจัดการระบบ **On-Premise Infrastructure** บน **Ubuntu 26.04** รองรับระบบ Polyglot Application Stacks ด้วยการวางรากฐาน **Containerization, CI/CD, GitOps, Kubernetes Cluster Management** รวมถึงการตั้งค่า **High Availability (HA) Load Balancing**, **Automated Security Scanning**, **Secret Management** และ **Observability**

---

## 🛠 Tech Stack & Core Competencies

### 1. Infrastructure & OS Layer
- **Operating System:** Ubuntu 26.04 LTS (Bare-metal / Virtualization)
- **High Availability & Network:** HAProxy (Active/Passive or Active/Active HA Setup), NGINX Ingress Controller (via Helm)
- **Configuration Management & Automation:** Ansible (Automated Provisioning & System Configurations)

### 2. Containerization & Orchestration
- **Container Platform:** Docker, Kubernetes (K8s)
- **Cluster Management:** Rancher
- **Package Management:** Helm

### 3. CI/CD & GitOps
- **Version Control Systems (VCS):** Gitea, GitHub, GitLab
- **CI/CD Pipeline Engine:** Jenkins (Shared Libraries, Automated Workflows)
- **GitOps Deployment:** ArgoCD (Declarative Continuous Delivery for Kubernetes)
- **Container Registry:** GitHub Container Registry (GHCR)

### 4. Security, Compliance & Secret Management
- **Secret Management:** HashiCorp Vault
- **Static Application Security Testing (SAST):** SonarQube
- **Container & Vulnerability Scanning:** Trivy
- **Dependency Audit:** OWASP Dependency-Check (Jenkins Plugin integration)

### 5. Middleware, Storage & Databases (Stateful Services)
- **Relational Database:** PostgreSQL (PostgreSQL 18+)
- **In-Memory Cache & Key-Value Store:** Redis
- **Object Storage:** MinIO (S3 Compatible Storage)
- **Log Management & Analytics:** ELK Stack (Elasticsearch, Logstash, Kibana)

### 6. Observability & Monitoring
- **Metrics & Dashboards:** Grafana, Prometheus/Exporter ecosystem

---

## 💡 Recommended Backup & Disaster Recovery Strategies (To be implemented)

เพื่อเติมเต็มระบบ On-Premise Infrastructure ให้สมบูรณ์และรองรับ Disaster Recovery ตามที่คุณขอคำแนะนำเพิ่มเติม มีแนวทางแนะนำดังนี้ครับ:

### A. Kubernetes Cluster & Persistent Volumes
- **Velero:** ใช้สำหรับการสำรองข้อมูล Kubernetes State (CRDs, Configurations) และ Persistent Volumes (PVs) ไปยัง MinIO หรือ S3-compatible storage

### B. Database & Storage Backups
- **PostgreSQL:**
  - **pgBackRest / Barman:** ทำ Automated Point-in-Time Recovery (PITR) และ Full/Incremental Backups
  - **pg_dump / pg_restore:** สำหรับ Logical Backups ประจำวัน (Automation ผ่าน Ansible/Cron)
- **MinIO:**
  - **MinIO Client (`mc mirror` / `mc admin replicate`):** ทำ Active-Passive Replication ไปยัง Backup Server / Storage node อื่น
- **Redis:**
  - **RDB (Snapshots) + AOF (Append Only File):** ตั้งค่าการ Persist ข้อมูลลง Disk พร้อมทำ Cron Job ซิงค์ไฟล์ RDB ไปยัง Backup Server

---

## 📄 Proposed `skills.md` File Structure

```text
.
├── skills.md