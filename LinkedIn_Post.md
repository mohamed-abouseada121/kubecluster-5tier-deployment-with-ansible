# 🚀 Just Finished: End-to-End GitOps Project with K8s, Jenkins & ArgoCD!

I'm excited to share my latest DevOps project where I built a complete **CI/CD pipeline** adopting the **GitOps methodology**.

Instead of the traditional push-based deployments, I implemented a robust Pull-based architecture ensuring that "Git is the Single Source of Truth".

## 🛠️ Technical Stack & Highlights:

🔹 **Infrastructure:** 3-Node Kubernetes Cluster bootstrapped with **kubeadm** on AWS EC2.
🔹 **Automation:** Used **Ansible** to provision nodes, install ArgoCD, and set up the Monitoring Stack (No manual SSH!).
🔹 **Continuous Integration (CI):** **Jenkins** pipeline that builds multi-stage Docker images (Non-Root/Secure) and pushes to **AWS ECR**.
🔹 **Continuous Delivery (CD):** **ArgoCD** runs inside the cluster, detects changes in the GitOps repo, and auto-syncs the application state. Zero `kubectl` usage for updates!
🔹 **Security:** Implemented **NetworkPolicies** to isolate pods and enforced **Rootless Containers** for best practices.
🔹 **Observability:** Deployed **Prometheus & Grafana** stacks via Helm for real-time monitoring of Node/Pod health.

## 💡 Why GitOps?
Moving deployment logic out of Jenkins and into ArgoCD made the process more stable, visible, and secure. If the cluster drifts, ArgoCD fixes it automatically.

Check out the full documentation and code in the repository below! 👇

#DevOps #Kubernetes #GitOps #ArgoCD #Jenkins #AWS #Ansible #Docker #CI_CD #Engineering
