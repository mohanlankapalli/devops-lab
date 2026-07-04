# Troubleshooting Log

## Issue Template

### Date

### Issue

### Error

### Root Cause

### Investigation Commands

### Resolution

### Prevention

---

# Issue 001

## Issue

kubectl connection refused

## Error

```
The connection to the server 127.0.0.1:<port> was refused
```

## Root Cause

Docker Desktop restarted.

Minikube updated Windows kubeconfig.

WSL kubeconfig still contained the old API server port.

## Investigation

```bash
minikube status

kubectl config view --minify

diff ~/.kube/config /mnt/c/Users/mohan/.kube/config

grep server ~/.kube/config
```

## Resolution

```bash
cp /mnt/c/Users/mohan/.kube/config ~/.kube/config

sed -i 's#C:\\Users\\mohan#/mnt/c/Users/mohan#g' ~/.kube/config

sed -i 's#\\#/#g' ~/.kube/config
```

## Permanent Fix

- Shared kubeconfig
- fix-kubeconfig.sh
- mkstart alias