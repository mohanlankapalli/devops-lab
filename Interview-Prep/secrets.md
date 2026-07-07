# Kubernetes Interview Questions - Secrets

## Topic: Kubernetes Secrets

---

# 🟢 Q1. What is a Secret?

**Answer:**

A Secret is a Kubernetes object used to store sensitive information such as passwords, API keys, OAuth tokens, SSH keys, and TLS certificates. Pods can consume Secrets as environment variables or mounted files.

**Follow-up Questions**

* Secret vs ConfigMap?
* Where are Secrets stored?
* Can Secrets store certificates?

---

# 🟢 Q2. Why do we use Secrets instead of ConfigMaps?

**Answer:**

ConfigMaps are meant for non-sensitive configuration like log levels or application settings. Secrets are designed to store sensitive information. Although Secrets are Base64 encoded by default, they can also be protected using Encryption at Rest and RBAC.

**Follow-up Questions**

* Can ConfigMaps store passwords?
* Why shouldn't passwords be stored in ConfigMaps?

---

# 🟢 Q3. How can a Pod consume a Secret?

**Answer:**

A Pod can consume a Secret in two ways:

* As environment variables.
* As mounted files using volumes.

The choice depends on how the application reads its configuration.

---

# 🟢 Q4. Are Kubernetes Secrets encrypted?

**Answer:**

No. By default, Kubernetes Secrets are Base64 encoded, not encrypted. In production, Encryption at Rest should be enabled, and access should be controlled using RBAC.

**Follow-up Questions**

* What is Base64?
* Is Base64 encryption?
* How do you secure Secrets in production?

---

# 🟢 Q5. Where are Secrets stored?

**Answer:**

Secrets are stored in the Kubernetes datastore called etcd. If Encryption at Rest is not enabled, they are only Base64 encoded.

---

# 🟢 Q6. How do you create a Secret?

**Answer:**

A Secret can be created using:

* kubectl create secret
* A YAML manifest
* From files
* From literal values

Example:

kubectl create secret generic db-secret --from-literal=username=admin --from-literal=password=MyP@ssw0rd

---

# 🟡 Q7. Which is better: Environment variables or mounted files?

**Answer:**

Both are valid.

Environment variables are simple and commonly used.

Mounted files are often preferred in production because many applications read configuration files directly, and secrets can be managed separately from environment variables.

---

# 🟡 Q8. What kinds of data should be stored in a Secret?

**Answer:**

Examples include:

* Database passwords
* API keys
* OAuth tokens
* TLS certificates
* SSH keys
* Docker registry credentials

---

# 🔴 Q9. How are Secrets managed in production?

**Answer:**

Production environments typically use:

* Encryption at Rest
* RBAC
* Secret rotation
* External Secret Managers such as HashiCorp Vault, AWS Secrets Manager, or Azure Key Vault
* Least-privilege access

---

# 🔴 Q10. A developer accidentally stores a password in a ConfigMap. What would you do?

**Answer:**

I would:

1. Remove the password from the ConfigMap.
2. Create a Secret.
3. Update the Pod or Deployment to use the Secret.
4. Rotate the exposed password if necessary.
5. Verify RBAC permissions.
6. Review deployment practices to prevent similar mistakes.

---

# Rapid Fire

**What is a Secret?**

Stores sensitive information.

**Is Base64 encryption?**

No.

**Where are Secrets stored?**

etcd.

**Can Secrets be mounted as files?**

Yes.

**Can Secrets be used as environment variables?**

Yes.

**Should passwords be stored in ConfigMaps?**

No.

---

# Production Notes

* Never store passwords in ConfigMaps.
* Enable Encryption at Rest.
* Restrict access using RBAC.
* Rotate Secrets regularly.
* Prefer external Secret Managers for production environments.
* Avoid printing Secret values in application logs.

---

# Common Mistakes

* Thinking Base64 is encryption.
* Storing passwords in ConfigMaps.
* Giving all users permission to read Secrets.
* Hardcoding passwords inside Docker images.
* Forgetting to rotate Secrets after exposure.
