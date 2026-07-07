# Kubernetes Secrets Commands

## Create a Secret

```bash
kubectl create secret generic db-secret \
--from-literal=username=admin \
--from-literal=dbpasswd=db@123
```

## View Secrets

```bash
kubectl get secrets
```

## Describe Secret

```bash
kubectl describe secret db-secret
```

## View Secret YAML

```bash
kubectl get secret db-secret -o yaml
```

## Decode Secret

```bash
echo "<base64-value>" | base64 -d
```

## Create Pod Using Secret as Environment Variables

```bash
kubectl apply -f pod-secret-env.yaml
```

## Verify Environment Variables

```bash
kubectl exec pod-secret-env -- env | grep -E "username|dbpasswd"
```

## Create Pod Using Secret as a Volume

```bash
kubectl apply -f pod-secret-volume.yaml
```

## Verify Mounted Secret Files

```bash
kubectl exec pod-secret-volume -- ls /etc/secret
```

## Read Mounted Secret

```bash
kubectl exec pod-secret-volume -- cat /etc/secret/username

kubectl exec pod-secret-volume -- cat /etc/secret/dbpasswd
```

## Delete Resources

```bash
kubectl delete pod pod-secret-env
kubectl delete pod pod-secret-volume
kubectl delete secret db-secret
```
