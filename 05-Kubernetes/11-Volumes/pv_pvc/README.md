# Kubernetes Persistent Volume (PV) & Persistent Volume Claim (PVC)

## 📌 Objective

Learn how Persistent Volumes (PV) and Persistent Volume Claims (PVC) provide persistent storage for Kubernetes applications.

---

## What is a Persistent Volume (PV)?

A Persistent Volume (PV) is a cluster resource that provides persistent storage independent of Pods.

Unlike `emptyDir` and `hostPath`, a PV is not tied to a Pod's lifecycle and can continue to exist even after Pods are deleted.

The storage backing a PV can be:

- AWS EBS
- Azure Disk
- Google Persistent Disk
- NFS
- Ceph
- Local Storage

---

## What is a Persistent Volume Claim (PVC)?

A Persistent Volume Claim (PVC) is a request for storage.

Instead of directly using a PV, Pods request storage through a PVC.

If a suitable PV is available, Kubernetes automatically binds the PVC to the PV.

---

## Architecture

```
                  Application
                       │
                       ▼
                    Pod
                       │
                 volumeMount
                       │
                       ▼
                    PVC (Request)
                       │
            Kubernetes binds
                       │
                       ▼
                 PV (Storage)
                       │
         AWS EBS / Azure Disk / NFS
```

---

## Lifecycle

1. Administrator creates a PV.
2. Developer creates a PVC.
3. Kubernetes binds the PVC to a matching PV.
4. Pod mounts the PVC.
5. Application stores data in the PV.
6. Even if the Pod is deleted, the data remains.
7. A new Pod using the same PVC can access the existing data.

---

## Characteristics

- Persistent storage
- Independent of Pod lifecycle
- Can survive Pod recreation
- Can survive node failures (depending on storage backend)
- Can be shared (depending on access mode)
- Suitable for databases and application data

---

## Access Modes

### ReadWriteOnce (RWO)

One node can mount the volume as read-write.

### ReadOnlyMany (ROX)

Multiple nodes can mount the volume as read-only.

### ReadWriteMany (RWX)

Multiple nodes can mount the volume as read-write.

---

## Reclaim Policies

### Delete

Deletes the storage after the PVC is deleted.

### Retain

Keeps the storage even after the PVC is deleted.

### Recycle (Deprecated)

Previously erased data and made the PV reusable.

---

## Real-world Use Cases

- MySQL Database
- PostgreSQL
- MongoDB
- Jenkins Home Directory
- SonarQube
- Nexus Repository
- WordPress
- User uploads
- Application data

---

## Difference Between Volumes

| Feature | emptyDir | hostPath | PV/PVC |
|----------|-----------|----------|--------|
| Temporary | ✅ | ❌ | ❌ |
| Pod Independent | ❌ | ✅ (Same Node) | ✅ |
| Node Independent | ❌ | ❌ | ✅ |
| Production Ready | ❌ | Limited | ✅ |
| Cloud Storage | ❌ | ❌ | ✅ |

---

## Learning Outcome

After completing this lab, I understood:

- What a Persistent Volume is
- What a Persistent Volume Claim is
- PV-PVC Binding
- Pod lifecycle vs Storage lifecycle
- Difference between emptyDir, hostPath and PV/PVC
- Real-world production use cases