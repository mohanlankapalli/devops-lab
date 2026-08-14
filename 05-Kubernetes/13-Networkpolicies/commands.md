# Kubernetes NetworkPolicy Commands

## Create a namespace for testing

```bash
kubectl create namespace netpol-demo
```

## Deploy sample applications

```bash
kubectl run web --image=nginx --namespace netpol-demo
kubectl run client --image=busybox:1.36 --namespace netpol-demo --restart=Never -- sleep 3600
```

## Label the pods

```bash
kubectl label pod web app=web --namespace netpol-demo
kubectl label pod client app=client --namespace netpol-demo
```

## View the pods

```bash
kubectl get pods -n netpol-demo -o wide
```

## Apply a default deny policy

```bash
kubectl apply -f denyall.yaml
```

## Verify the NetworkPolicy

```bash
kubectl get networkpolicy -n default
kubectl describe networkpolicy deny-all -n default
```

## Test connectivity from the client pod

```bash
kubectl exec -it client -n netpol-demo -- /bin/sh
wget -qO- http://web.netpol-demo.svc.cluster.local
```

If the deny-all policy is active, the request should fail because no traffic is allowed.

## Allow only traffic from the client to the web pod

Create a policy like this:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-web-from-client
  namespace: netpol-demo
spec:
  podSelector:
    matchLabels:
      app: web
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: client
      ports:
        - protocol: TCP
          port: 80
```

Apply it:

```bash
kubectl apply -f - <<EOF
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-web-from-client
  namespace: netpol-demo
spec:
  podSelector:
    matchLabels:
      app: web
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: client
      ports:
        - protocol: TCP
          port: 80
EOF
```

## Test connectivity again

```bash
kubectl exec -it client -n netpol-demo -- /bin/sh
wget -qO- http://web.netpol-demo.svc.cluster.local
```

## View all NetworkPolicies

```bash
kubectl get networkpolicy --all-namespaces
```

## Delete the namespace after testing

```bash
kubectl delete namespace netpol-demo
```

## Delete the default deny policy

```bash
kubectl delete networkpolicy deny-all -n default
```
