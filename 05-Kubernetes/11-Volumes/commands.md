# Kubernetes Volumes Commands

## Create Pod with emptyDir

```bash
kubectl apply -f pod-emptydir.yaml
```

## View Pod

```bash
kubectl get pods
```

## Describe Pod

```bash
kubectl describe pod pod-emptydir
```

## Open Shell Inside Container

```bash
kubectl exec -it pod-emptydir -- sh
```

## Verify Mounted Directory

```bash
ls /data
```

## Create File Inside Volume

```bash
echo "Hello Kubernetes" > /data/test.txt
```

## Verify File

```bash
cat /data/test.txt
```

## Create Pod Using hostPath

```bash
kubectl apply -f pod-hostpath.yaml
```

## Verify Mounted Directory

```bash
kubectl exec -it pod-hostpath -- sh
```

```bash
ls /host-data
```

## Describe Pod

```bash
kubectl describe pod pod-hostpath
```

## Delete Resources

```bash
kubectl delete -f pod-emptydir.yaml

kubectl delete -f pod-hostpath.yaml
```
