# ☸️ Jenkins CI + GitOps CD with ArgoCD on Kubernetes

**A complete End-to-End DevOps Project implementing the GitOps methodology.**

This project builds a production-ready 3-Node Kubernetes Cluster using **kubeadm**, automates Infrastructure setup with **Ansible**, utilizes **Jenkins** for Continuous Integration, and implements **ArgoCD** for Continuous Delivery (GitOps).

---

## 🏗️ Architecture & Stack

| Component | Tool / Technology | Purpose |
| :--- | :--- | :--- |
| **Infrastructure** | AWS EC2 (Ubuntu 22.04) | 1 Master + 2 Worker Nodes |
| **Configuration** | Ansible | Auto-provisioning & K8s bootstrapping |
| **Container Engine** | containerd | CRI Runtime for Kubernetes |
| **Cluster Mgr** | kubeadm | Bootstrapping the K8s Cluster |
| **CI Server** | Jenkins | Build, Test, & Push Docker Images |
| **Image Registry** | AWS ECR | Storing Private Docker Images |
| **CD / GitOps** | ArgoCD | Syncing Manifests from Git to K8s |
| **Monitoring** | Prometheus & Grafana | Cluster & App Observability |

---

## 🚀 CI/CD Workflow (The GitOps Pipeline)

We moved away from "Push-based" deployments (like `kubectl apply` from Jenkins) to a modern **"Pull-based" GitOps** model.

1.  **💻 Develop**: Developer pushes code to the Application Repository.
2.  **⚙️ CI (Jenkins)**:
    *   Builds a **Multi-Stage** Docker Image (Security optimization).
    *   Authenticates with AWS ECR.
    *   Pushes the new image with a unique tag.
    *   **Updates the GitOps Manifest Repo** with the new tag.
3.  **🔄 CD (ArgoCD)**:
    *   Detects the change in the GitOps Repo.
    *   Automatically **Syncs** the state.
    *   Performs a Rolling Update on the Kubernetes Cluster.

---

## 🛡️ Security Implementations

Security is woven into every layer of this project:

*   **Container Security:**
    *   Running as **Non-Root User**.
    *   Using **Multi-Stage Builds** for minimal attack surface.
    *   Minimal Base Images (Distroless/Alpine).
*   **Network Security:**
    *   **K8s NetworkPolicies:** Deny-All by default; ONLY Ingress Controller can talk to Backend Pods.
*   **Secret Management:**
    *   **No hardcoded secrets** in Git.
    *   Jenkins Credentials Store used for CI auth.
    *   K8s Secrets for runtime environment variables.

---

## 📊 Monitoring & Observability

Everything is monitored using a modern stack deployed via **Helm** and **Ansible**:

*   **Prometheus:** Scrapes metrics from Nodes, Pods, and Services.
*   **Grafana:** Visualizes data with pre-configured dashboards:
    *   Node Health (CPU/Memory/Disk).
    *   Pod Performance.
    *   Application Availability (Blackbox / HTTP Checks).

---

## 🛠️ How it runs (Ansible Playbooks)

We use Ansible to avoid manual tasks ("Human Error is the enemy").

*   `install_kubeadm_master.yml`: Bootstraps the Control Plane.
*   `install_kubeadm_workers.yml`: Joins workers to the cluster.
*   `install_argocd.yml`: Deploys ArgoCD & Configures the App Source.
*   `install_monitoring.yml`: Deploys the Prometheus/Grafana Stack.

---

## 🏆 Assessment Criteria Met

*   ✅ **GitOps Pattern:** Fully implemented with ArgoCD auto-sync.
*   ✅ **Infrastructure as Code:** Ansible used for all setup.
*   ✅ **Security First:** Rootless containers & Strict Network Policies.
*   ✅ **Observability:** Complete monitoring stack included.
