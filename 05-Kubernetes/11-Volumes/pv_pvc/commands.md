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

## Create Deployment Using PVC

```bash
kubectl apply -f pv-pvc.yaml
```

---

## Verify Deployment

```bash
kubectl get deploy
```

---

## Verify Pods

```bash
kubectl get pods -l app=myapp
```

---

## Verify Mounted Volume

```bash
kubectl describe pod <pod-name>
```

---

## Enter Container in the Pod

```bash
kubectl exec -it <pod-name> -c cont1 -- sh
```

---

## Create File in Mounted Volume

```bash
echo "Persistent Storage" > /temp/dev/test.txt
```

---

## Verify File

```bash
cat /temp/dev/test.txt
```

---

## Delete Deployment

```bash
kubectl delete deployment myapp
```

---

## Recreate Deployment

```bash
kubectl apply -f pv-pvc.yaml
```

---

## Verify Data Persistence

```bash
cat /temp/dev/test.txt
```

---

## Delete PVC

```bash
kubectl delete pvc pvc-1
```

---

## Delete PV

```bash
kubectl delete pv pv-1
```

---

## Delete All Resources

```bash
kubectl delete -f .
```