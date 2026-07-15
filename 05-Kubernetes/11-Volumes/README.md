Kubernetes - Volumes
 
Objective
 
Learn how Kubernetes Volumes provide persistent or shared storage for containers running inside a Pod.
 
---
 
What is a Volume?
 
A Kubernetes Volume is a storage mechanism that allows containers in a Pod to store and access data.
 
Unlike a container's filesystem, a Volume survives container restarts within the same Pod.
 
---
 
Why do we need Volumes?
 
Containers are ephemeral. If a container crashes or restarts, the data stored inside its writable layer is lost.
 
Volumes help preserve application data and allow multiple containers in the same Pod to share files.
 
---
 
Types of Volumes
 
emptyDir
 
- Created when the Pod starts.
- Deleted when the Pod is deleted.
- Used for temporary storage and sharing data between containers.
 
hostPath
 
- Mounts a directory from the worker node.
- Mainly used for testing or single-node environments like Minikube.
- Not recommended for production applications.
 
Persistent Volume (PV)
 
- Cluster-wide storage resource.
- Managed by the administrator.
- Independent of Pods.
 
Persistent Volume Claim (PVC)
 
- A request for storage by an application.
- Pods use PVC instead of directly accessing a PV.
 
---
 
Lab Tasks
 
- Create a Pod using emptyDir.
- Share data between two containers.
- Create a Pod using hostPath.
- Verify mounted directories.
- Understand PV and PVC concepts.
 
---
 
Files
 
- pod-emptydir.yaml
- pod-hostpath.yaml
- commands.md
 
---
 
Screenshots
 
1. emptyDir Pod Created
 
2. Verify Mounted Directory
 
3. Shared Data Between Containers
 
4. hostPath Volume Mounted
 
5. Volume Description
 
---
 
Key Learnings
 
- Volumes store application data.
- emptyDir exists only while the Pod exists.
- hostPath mounts a directory from the Kubernetes node.
- Multiple containers can share the same Volume.
- Production applications typically use Persistent Volumes and Persistent Volume Claims.
 
---
 
Real-World Use Case
 
Applications such as databases, logging systems, CI/CD tools, and monitoring platforms require persistent storage. Kubernetes Volumes ensure application data remains available beyond individual container restarts.
 
---
 
Cleanup
 
kubectl delete -f pod-emptydir.yaml
 
kubectl delete -f pod-hostpath.yaml
