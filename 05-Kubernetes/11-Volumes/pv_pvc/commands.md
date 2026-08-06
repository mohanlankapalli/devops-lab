# Kubernetes PV & PVC Commands

## Create Persistent Volume

```bash
kubectl apply -f pv.yaml
```

---

## Create Persistent Volume Claim

```bash
kubectl apply -f pvc.yaml
```

---

## Verify Persistent Volume

```bash
kubectl get pv
```

---

## Verify Persistent Volume Claim

```bash
kubectl get pvc
```

---

## Detailed PV Information

```bash
kubectl describe pv
```

---

## Detailed PVC Information

```bash
kubectl describe pvc
```

---

## Create Pod Using PVC

```bash
kubectl apply -f pod.yaml
```

---

## Verify Pod

```bash
kubectl get pods
```

---

## Verify Mounted Volume

```bash
kubectl describe pod <pod-name>
```

---

## Enter Pod

```bash
kubectl exec -it <pod-name> -- sh
```

---

## Create File

```bash
echo "Persistent Storage" > /data/test.txt
```

---

## Verify File

```bash
cat /data/test.txt
```

---

## Delete Pod

```bash
kubectl delete pod <pod-name>
```

---

## Recreate Pod

```bash
kubectl apply -f pod.yaml
```

---

## Verify Data Persistence

```bash
cat /data/test.txt
```

---

## Delete PVC

```bash
kubectl delete pvc <pvc-name>
```

---

## Delete PV

```bash
kubectl delete pv <pv-name>
```

---

## Delete All Resources

```bash
kubectl delete -f .
```