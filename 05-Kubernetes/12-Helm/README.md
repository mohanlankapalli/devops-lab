# Helm Charts

## Objective

Learn how Helm works as a package manager for Kubernetes and how to create, configure, install, upgrade, rollback, and uninstall Helm releases.

---

## What is Helm?

Helm is a package manager for Kubernetes.

It packages Kubernetes resource manifests into a reusable unit called a **Helm Chart**.

Instead of maintaining many separate YAML files manually, Helm allows us to create templates and provide configuration through `values.yaml`.

### Without Helm

```text
deployment.yaml
service.yaml
configmap.yaml
secret.yaml
ingress.yaml
```

Every environment may require different values.

### With Helm

```text
Helm Chart
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    └── configmap.yaml
```

---

## Helm Architecture

```text
                  Helm Chart
                      │
          ┌───────────┴───────────┐
          │                       │
      templates/              values.yaml
          │                       │
          └───────────┬───────────┘
                      │
                  Helm Engine
                      │
                      ▼
              Kubernetes API
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
       Deployment   Service    ConfigMap
```

---

## What is a Helm Chart?

A Helm Chart is a collection of files that describes a Kubernetes application.

A basic chart contains:

```text
myapp/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    └── service.yaml
```

---

## Important Files

### Chart.yaml

Contains metadata about the chart.

Example:

```yaml
apiVersion: v2
name: myapp
description: A simple Kubernetes application
type: application
version: 0.1.0
appVersion: "1.0"
```

---

### values.yaml

Contains configurable values used by templates.

Example:

```yaml
replicaCount: 2

image:
  repository: nginx
  tag: latest

service:
  type: ClusterIP
  port: 80
```

---

### templates/

Contains Kubernetes manifests with Helm template expressions.

Example:

```yaml
spec:
  replicas: {{ .Values.replicaCount }}
```

The value comes from:

```yaml
replicaCount: 2
```

in `values.yaml`.

---

## Helm Release

When a chart is installed into Kubernetes, Helm creates a **release**.

```text
Chart
  │
  ▼
helm install
  │
  ▼
Release
  │
  ▼
Kubernetes Resources
```

One chart can be installed multiple times with different release names.

Example:

```text
myapp-dev
myapp-test
myapp-prod
```

---

## Helm Template Flow

```text
values.yaml
     │
     ▼
templates/*.yaml
     │
     ▼
Helm renders templates
     │
     ▼
Kubernetes manifests
     │
     ▼
Kubernetes API
```

---

## Helm Upgrade

Helm allows an existing release to be updated.

```text
Old values
    │
    ▼
helm upgrade
    │
    ▼
Updated Kubernetes resources
```

For example:

```yaml
replicaCount: 2
```

can be changed to:

```yaml
replicaCount: 4
```

and the release can be upgraded.

---

## Helm Rollback

If an upgrade causes a problem, Helm maintains release revisions.

```text
Revision 1
    ↓
Revision 2
    ↓
Revision 3
```

If Revision 3 has a problem:

```text
helm rollback <release> 2
```

Helm can return the release to Revision 2.

---

## Helm Repository

A Helm repository stores Helm charts so users can discover and install them.

```text
Helm Client
     │
     ▼
Helm Repository
     │
     ▼
Chart
     │
     ▼
Kubernetes
```

---

## Helm vs Kubernetes YAML

| Kubernetes YAML | Helm |
|---|---|
| Static manifests | Templates |
| Manual value changes | `values.yaml` |
| Reuse requires copying/editing | Reusable chart |
| No built-in release history | Release revisions |
| Manual rollback | Helm rollback |
| Multiple YAML files | Packaged as a chart |

---

## Real-world Use Cases

Helm is commonly useful when teams need to:

- Deploy the same application to multiple environments.
- Reuse Kubernetes manifests.
- Change configuration without rewriting manifests.
- Manage application versions.
- Upgrade applications.
- Roll back failed releases.
- Package applications for distribution.

Example:

```text
Same application

Development
    ↓
values-dev.yaml

Testing
    ↓
values-test.yaml

Production
    ↓
values-prod.yaml
```

The same Helm chart can be reused with different values.

---

## Learning Outcome

After completing this practice, I understand:

- What Helm is
- What a Helm Chart is
- Chart.yaml
- values.yaml
- templates/
- Helm releases
- Helm repositories
- Install
- Upgrade
- Rollback
- Uninstall
- How Helm reduces repetitive Kubernetes YAML