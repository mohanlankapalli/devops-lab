# Kubernetes Namespace Commands

## View namespaces

```bash
kubectl get ns
```

## Create a namespace

```bash
kubectl create namespace dev
```

## Deploy Nginx in the dev namespace

```bash
kubectl create deployment nginx --image=nginx -n dev
```

## View all resources in the dev namespace

```bash
kubectl get all -n dev
```

## View pods in the default namespace

```bash
kubectl get pods
```

## View pods in the dev namespace

```bash
kubectl get pods -n dev
```

## Set the current namespace to dev

```bash
kubectl config set-context --current --namespace=dev
```

## Verify the current namespace

```bash
kubectl config view --minify
```

## Restore the default namespace

```bash
kubectl config set-context --current --namespace=default
```

## Delete the namespace

```bash
kubectl delete namespace dev
```
