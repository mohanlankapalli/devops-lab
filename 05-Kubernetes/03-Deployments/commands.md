# Deployment Commands

kubectl apply -f deployment.yaml

kubectl get deployments

kubectl get rs

kubectl get pods

kubectl describe deployment nginx-deployment

kubectl scale deployment nginx-deployment --replicas=5

kubectl rollout status deployment/nginx-deployment

kubectl rollout history deployment/nginx-deployment