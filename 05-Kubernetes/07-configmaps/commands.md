# Kubernetes ConfigMap Commands

## Create a ConfigMap

```bash
kubectl create configmap app-config \
  --from-literal=APP_NAME=myapp \
  --from-literal=ENV=dev
```

## View ConfigMaps

```bash
kubectl get configmap
```

## Describe a ConfigMap

```bash
kubectl describe configmap app-config
```

## Create a Pod using ConfigMap as Environment Variables

```bash
kubectl apply -f pod-env.yaml
```

## Verify Pod

```bash
kubectl get pods
```

## View Environment Variables

```bash
kubectl exec nginx-env -- env | grep -E "APP_NAME|ENV"
```

## Create a Pod using ConfigMap as a Volume

```bash
kubectl apply -f pod-volume.yaml
```

## List Mounted Files

```bash
kubectl exec nginx-volume -- ls /etc/config
```

## Read Mounted Configuration

```bash
kubectl exec nginx-volume -- cat /etc/config/APP_NAME

kubectl exec nginx-volume -- cat /etc/config/ENV
```

## Delete Resources

```bash
kubectl delete pod nginx-env
kubectl delete pod nginx-volume
kubectl delete configmap app-config
```
