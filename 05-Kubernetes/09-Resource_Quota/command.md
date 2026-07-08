# Kubernetes ResourceQuota Commands

## Create Namespace

```bash
kubectl create namespace dev
```

## Create ResourceQuota

```bash
kubectl apply -f resourcequota.yaml
```

## View ResourceQuota

```bash
kubectl get resourcequota -n dev
```

## Describe ResourceQuota

```bash
kubectl describe resourcequota dev-quota -n dev
```

## Create Pod

```bash
kubectl apply -f pod.yaml
```

## View Pods

```bash
kubectl get pods -n dev
```

## Describe Pod

```bash
kubectl describe pod rq-pod -n dev
```

## Delete Pod

```bash
kubectl delete pod rq-pod -n dev
```

## Delete ResourceQuota

```bash
kubectl delete resourcequota dev-quota -n dev
```

## Delete Namespace

```bash
kubectl delete namespace dev
```
