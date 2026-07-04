# Commands

## Create

kubectl apply -f daemonset.yaml

## Verify DaemonSet

kubectl get ds

## Verify Pods

kubectl get pods -o wide

## Describe

kubectl describe ds nginx-daemonset

## Delete

kubectl delete -f daemonset.yaml