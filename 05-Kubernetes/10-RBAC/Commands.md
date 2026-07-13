Kubernetes RBAC Commands
 
Create Namespace
 
kubectl create namespace dev
 
Create ServiceAccount
 
kubectl apply -f serviceaccount.yaml
 
View ServiceAccounts
 
kubectl get serviceaccount -n dev
 
Create Role
 
kubectl apply -f role.yaml
 
View Roles
 
kubectl get roles -n dev
 
Describe Role
 
kubectl describe role dev-role -n dev
 
Create RoleBinding
 
kubectl apply -f rolebinding.yaml
 
View RoleBindings
 
kubectl get rolebindings -n dev
 
Verify Permissions
 
kubectl auth can-i get pods --as=system:serviceaccount:dev:dev-sa -n dev
 
Verify All Permissions
 
kubectl auth can-i --list --as=system:serviceaccount:dev:dev-sa -n dev
 
Delete Resources
 
kubectl delete rolebinding dev-rolebinding -n dev
 
kubectl delete role dev-role -n dev
 
kubectl delete serviceaccount dev-sa -n dev
