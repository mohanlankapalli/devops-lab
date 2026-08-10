# Kubernetes Lab

## Kubernetes Architecture

```text
Kubernetes Cluster
│
├── Control Plane
│   ├── API Server
│   ├── etcd
│   ├── Scheduler
│   ├── Controller Manager
│   └── Cloud Controller Manager (optional)
│
├── Worker Nodes
│   ├── Node 1
│   │   ├── kubelet
│   │   ├── kube-proxy
│   │   ├── Container Runtime
│   │   └── Pods
│   │
│   └── Node 2
│       └── ...
│
└── Namespaces
    ├── default
    ├── kube-system
    ├── kube-public
    ├── kube-node-lease
    └── custom-namespace
        │
        ├── Workloads
        │   ├── Deployment
        │   │   └── ReplicaSet
        │   │       └── Pod
        │   │           └── Container(s)
        │   ├── StatefulSet
        │   ├── DaemonSet
        │   ├── Job
        │   └── CronJob
        │
        ├── Networking
        │   ├── Service
        │   ├── Ingress
        │   ├── NetworkPolicy
        │   └── EndpointSlice
        │
        ├── Storage
        │   ├── PersistentVolume (PV)
        │   ├── PersistentVolumeClaim (PVC)
        │   ├── StorageClass
        │   └── VolumeSnapshot
        │
        ├── Configuration
        │   ├── ConfigMap
        │   └── Secret
        │
        ├── Security
        │   ├── ServiceAccount
        │   ├── Role
        │   ├── ClusterRole
        │   ├── RoleBinding
        │   └── ClusterRoleBinding
        │
        ├── Scaling
        │   ├── HorizontalPodAutoscaler (HPA)
        │   └── VerticalPodAutoscaler (VPA)
        │
        └── Resource Management
            ├── ResourceQuota
            ├── LimitRange
            └── PriorityClass
```

## Lab Structure

- 03-Deployments
- 04-StatefulSets
- 05-Daemonset
- 06-Namespaces
- 07-configmaps
- 08-secretes
- 09-Resource_Quota
- 10-RBAC
- 11-Volumes
