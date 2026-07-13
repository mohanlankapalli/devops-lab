Kubernetes - RBAC (Role-Based Access Control)
 
Objective
 
Learn how Kubernetes controls access to cluster resources using RBAC.
 
---
 
What is RBAC?
 
RBAC (Role-Based Access Control) is the Kubernetes authorization mechanism used to control who can perform what actions on which resources.
 
RBAC helps secure the cluster by granting only the required permissions to users, groups, or service accounts.
 
---
 
Why do we use RBAC?
 
Without RBAC, any user with cluster access could modify or delete critical resources.
 
RBAC follows the Principle of Least Privilege by allowing users to perform only the actions they require.
 
---
 
Lab Tasks
 
- Create a Namespace.
- Create a ServiceAccount.
- Create a Role.
- Create a RoleBinding.
- Verify access permissions.
- Understand Role vs ClusterRole.
- Understand RoleBinding vs ClusterRoleBinding.
 
---
 
Files
 
- serviceaccount.yaml
- role.yaml
- rolebinding.yaml
- commands.md
 
---
 
Screenshots
 
1. ServiceAccount Created
 
2. Role Created
 
3. RoleBinding Created
 
4. Verify Permissions
 
5. kubectl auth can-i Output
 
---
 
Key Learnings
 
- RBAC controls authorization.
- Roles provide permissions inside a namespace.
- ClusterRoles provide cluster-wide permissions.
- RoleBindings assign Roles to users or ServiceAccounts.
- RBAC improves Kubernetes security.
 
---
 
Real-World Use Case
 
In production, developers usually receive access only to their application's namespace. They cannot modify system resources or other teams' namespaces. RBAC ensures secure access and prevents accidental changes.
 
---
 
Cleanup
 
kubectl delete rolebinding dev-rolebinding -n dev
kubectl delete role dev-role -n dev
kubectl delete serviceaccount dev-sa -n dev
