# Kubernetes - Network Policies

## Objective

Learn how Kubernetes Network Policies control traffic between pods and namespaces.

---

## What is a Network Policy?

A Network Policy is a Kubernetes resource that defines rules for allowing or denying network traffic to and from pods.

By default, Kubernetes allows all pod-to-pod communication inside the cluster. Network Policies add security by restricting traffic based on pod labels, namespaces, and ports.

They are enforced by the cluster's CNI plugin, such as Calico, Cilium, or Weave.

---

## Why do we use Network Policies?

Network Policies are used to:

- secure workloads by default
- isolate application tiers
- allow only required communication
- block unnecessary traffic between services
- reduce attack surface in a multi-tenant cluster

---

## Lab Tasks

- Understand the purpose of Network Policies.
- Apply a default deny policy.
- Verify that traffic is blocked.
- Allow only selected traffic between pods.
- Understand ingress and egress rules.
- Practice using labels and selectors.

---

## Files

- `denyall.yaml`
- `commands.md`

---

## Screenshots

### 1. Default Deny Policy

![Deny All Policy](screenshots/01-deny-all-policy.png)

### 2. Traffic Blocked

![Traffic Blocked](screenshots/02-traffic-blocked.png)

### 3. Allowed Traffic After Policy

![Allowed Traffic](screenshots/03-allowed-traffic.png)

---

## Key Learnings

- A Network Policy is applied to pods using a `podSelector`.
- `policyTypes` can include `Ingress` and `Egress`.
- `podSelector` and `namespaceSelector` help define allowed sources.
- Rules are based on labels, not IP addresses only.
- Network Policies are important for microservice security and zero-trust design.
- A `deny-all` policy blocks all ingress and egress unless rules are explicitly added.

---

## Real-World Use Case

In a production cluster, the frontend application may be allowed to talk to the backend API, but the backend should not be able to reach the database unless explicitly permitted. Network Policies help enforce this least-privilege communication model.

---

## Cleanup

```bash
kubectl delete networkpolicy deny-all -n default
```
