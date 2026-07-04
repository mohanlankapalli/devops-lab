# DevOps Lab Setup

## Goal

Create a stable DevOps learning environment that can be used for Kubernetes, Helm, Terraform, Ansible, AWS, CI/CD, and future tools without repeated setup.

---

## Lab Architecture

Windows 11
│
├── VS Code (UI)
├── Docker Desktop
│
└── WSL (Ubuntu)
    ├── Git
    ├── kubectl
    ├── k9s
    ├── Helm
    ├── Terraform (Future)
    ├── AWS CLI (Future)
    └── Other DevOps Tools

---

## Installed Tools

| Tool | Status |
|-------|--------|
| Git | ✅ |
| Docker Desktop | ✅ |
| WSL Ubuntu | ✅ |
| kubectl | ✅ |
| Minikube | ✅ |
| k9s | ✅ |
| Helm | ✅ |
| VS Code | ✅ |

---

## Decisions

- WSL Ubuntu is the primary terminal.
- Docker Desktop runs on Windows.
- Kubernetes runs inside Minikube using Docker Driver.
- Git uses SSH authentication.
- VS Code connects to WSL.

---

## Next Tools

- Terraform
- AWS CLI
- kubectx
- kubens
- ArgoCD
- Jenkins