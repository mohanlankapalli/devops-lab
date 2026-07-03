# Kubernetes StatefulSet

## Objective

Learn how StatefulSets manage stateful applications by providing:

- Stable Pod names
- Stable network identity
- Persistent storage
- Ordered Pod creation and deletion

---

## What is a StatefulSet?

A StatefulSet is a Kubernetes workload resource used to deploy applications that require persistent identity and storage.

Unlike Deployments, Pods created by StatefulSets have predictable names and maintain their identity even after restarts.

Example applications:

- MySQL
- PostgreSQL
- MongoDB
- Cassandra
- Kafka
- Elasticsearch

---

## Why StatefulSet?

Deployment Pods are interchangeable.

Example:

```
nginx-abc123
nginx-def456
nginx-xyz789
```

If one Pod is deleted, Kubernetes creates a new Pod with a different name.

StatefulSet Pods always keep the same identity.

Example:

```
mysql-0
mysql-1
mysql-2
```

If mysql-1 restarts, it comes back as:

```
mysql-1
```

not

```
mysql-asdf123
```

---

## Features

- Stable Pod Names
- Stable DNS Names
- Ordered Deployment
- Ordered Scaling
- Ordered Termination
- Persistent Volumes

---

## Hands-on Steps

1. Create StatefulSet YAML
2. Apply StatefulSet
3. Verify StatefulSet
4. Verify Pods
5. Scale StatefulSet
6. Delete a Pod
7. Observe Pod recreation

---

## Commands Used

See commands.md

---

## Output

Add screenshots:

- StatefulSet created
- Pods
- Scaling
- Pod recreation

---

## Interview Questions

### Why not use Deployment for databases?

Because database Pods need:

- Stable hostname
- Stable storage
- Ordered startup

Deployment does not guarantee these.

---

### Difference between Deployment and StatefulSet

| Deployment | StatefulSet |
|------------|-------------|
| Stateless | Stateful |
| Random Pod Names | Stable Pod Names |
| Shared Storage | Dedicated Storage |
| Parallel Creation | Ordered Creation |

---

## Key Learnings

- StatefulSet is used for stateful applications.
- Every Pod has a unique identity.
- Pod names never change.
- Stateful applications require persistent storage.