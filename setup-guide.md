# 🚀 Complete Infrastructure Setup & Configuration Guide (Ansible-Automated)
**Target OS:** Ubuntu 26.04 LTS (On-Premise)  
**Architecture:** Automated High Availability (HA) Load Balancing, Multi-Node Kubernetes (RKE2), Single-Node Stateful Services (MinIO, Redis, ELK, Public PostgreSQL) & DevSecOps Stack

---

## 🔑 Centralized Access & System Credentials Matrix

| System / Service | Access Endpoint / Port | Username / Role | Password / Token | Description |
| :--- | :--- | :--- | :--- | :--- |
| **Linux Nodes (SSH)** | All Server IPs (Port 22) | `ubuntu` | Key / Sudo Password | Base OS SSH Access |
| **HAProxy Stats** | `http://192.168.1.10:8443/` | `admin` | `StatsAdminPass2026!` | Load Balancer Monitoring |
| **Keepalived VRRP** | VIP `192.168.1.10` | N/A | Auth Pass: `HighAvailabilityPass2026` | High Availability VIP Auth |
| **PostgreSQL 18** | `192.168.1.41:5432` (Public) | `postgres` | `PgSuperSecurePass2026!` | DB Admin User (Listen `*`) |
| **MinIO Console** | `http://192.168.1.51:9001` | `minioadmin` | `MinioSuperSecurePass2026!` | S3 Object Storage Console |
| **MinIO API** | `http://192.168.1.51:9000` | `minioadmin` | `MinioSuperSecurePass2026!` | S3 API Service Endpoint |
| **Redis Server** | `192.168.1.61:6379` | default user | `RedisSuperSecurePass2026!` | In-Memory Cache Key-Value Store |
| **Elasticsearch API**| `https://192.168.1.71:9200` | `elastic` | `ElasticSuperSecurePass2026!` | Log Search Engine API |
| **Kibana UI** | `http://192.168.1.71:5601` | `elastic` | `ElasticSuperSecurePass2026!` | Log Dashboard Interface |
| **Rancher UI** | `https://rancher.internal.domain` | `admin` | `AdminSuperSecurePassword2026!` | K8s Management Console |
| **ArgoCD UI** | `https://argocd.internal.domain` | `admin` | Auto-generated / Retrievable | GitOps CD Pipeline Platform |
| **Grafana UI** | `https://grafana.internal.domain` | `admin` | `GrafanaSuperSecurePass2026!` | Metrics & Monitoring Dashboard |
| **HashiCorp Vault** | `https://vault.internal.domain` | Root Token | Vault Unseal & Root Auth Setup | Distributed Secret Management |

---

## 📁 Ansible Project Structure

```text
ansible/
├── inventory/
│   └── hosts.ini
├── site.yml
└── roles/
    ├── common_os_base/
    ├── haproxy_keepalived/
    ├── k8s_install/
    ├── k8s_resource_setup/
    ├── postgres/
    ├── minio/
    ├── redis/
    └── elk/