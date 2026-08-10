# Helm Commands

## Check Helm Version

```bash
helm version
```

---

## Get Helm Help

```bash
helm help
```

---

# Chart Creation

## Create a New Helm Chart

```bash
helm create myapp
```

This creates:

```text
myapp/
├── Chart.yaml
├── values.yaml
├── charts/
├── templates/
└── .helmignore
```

---

## Enter the Chart Directory

```bash
cd myapp
```

---

## List Chart Files

```bash
ls
```

---

# Chart Validation

## Lint the Chart

```bash
helm lint myapp
```

Checks the chart for common problems.

---

## Render Templates Locally

```bash
helm template myapp
```

This renders the Helm templates into Kubernetes YAML without installing anything.

---

## Render Using a Specific Values File

```bash
helm template myapp -f values.yaml
```

---

# Helm Repository

## Add a Helm Repository

Example:

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```

---

## List Helm Repositories

```bash
helm repo list
```

---

## Update Repository Information

```bash
helm repo update
```

---

## Search Charts in a Repository

```bash
helm search repo nginx
```

---

# Install

## Install a Chart

```bash
helm install myapp ./myapp
```

`myapp` is the release name.

---

## Check Releases

```bash
helm list
```

---

## List Releases in All Namespaces

```bash
helm list -A
```

---

## Install into a Specific Namespace

```bash
helm install myapp ./myapp -n dev --create-namespace
```

---

# Inspect Release

## Get Release Status

```bash
helm status myapp
```

---

## Get Release History

```bash
helm history myapp
```

---

## Get Release Values

```bash
helm get values myapp
```

---

## Get All Release Information

```bash
helm get all myapp
```

---

## Get Release Manifest

```bash
helm get manifest myapp
```

---

# Upgrade

## Upgrade a Release

```bash
helm upgrade myapp ./myapp
```

---

## Upgrade with Custom Values

```bash
helm upgrade myapp ./myapp -f values.yaml
```

---

## Install or Upgrade

```bash
helm upgrade --install myapp ./myapp
```

This is useful when you don't know whether the release already exists.

---

# Rollback

## View Release History

```bash
helm history myapp
```

---

## Roll Back to a Previous Revision

```bash
helm rollback myapp 1
```

---

## Verify Rollback

```bash
helm status myapp
```

---

## Check History Again

```bash
helm history myapp
```

---

# Kubernetes Verification

## Check Pods

```bash
kubectl get pods
```

---

## Check Deployments

```bash
kubectl get deployments
```

---

## Check Services

```bash
kubectl get svc
```

---

## Check All Resources

```bash
kubectl get all
```

---

# Uninstall

## Uninstall a Release

```bash
helm uninstall myapp
```

---

## Verify Release Was Removed

```bash
helm list
```

---

## Verify Kubernetes Resources

```bash
kubectl get all
```

---

# Useful Helm Commands

## Show Chart Information

```bash
helm show chart ./myapp
```

---

## Show Chart Values

```bash
helm show values ./myapp
```

---

## Show Chart README

```bash
helm show readme ./myapp
```

---

## Package a Chart

```bash
helm package ./myapp
```

This creates a `.tgz` Helm chart package.

---

## Verify Helm Releases in All Namespaces

```bash
helm list -A
```

---

# Basic Practice Flow

```bash
helm create myapp

helm lint ./myapp

helm template myapp ./myapp

helm install myapp ./myapp

helm list

helm status myapp

helm history myapp

helm upgrade myapp ./myapp

helm history myapp

helm rollback myapp 1

helm status myapp

helm uninstall myapp
```

---

# Cleanup

```bash
helm uninstall myapp
```

Then verify:

```bash
kubectl get all
```