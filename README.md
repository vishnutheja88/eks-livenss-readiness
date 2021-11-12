# eks-livenss-readiness
eks livenss and readiness probe examples
liveness probe:
kubectl apply -f ~/environment/healthchecks/liveness-app.yaml
kubectl get pod liveness-app
kubectl describe pod liveness-app
kill the process:
kubectl exec -it liveness-app -- /bin/kill -s SIGUSR1 1
kubectl get pod liveness-app
kubectl logs liveness-app
kubectl logs liveness-app --previous
********************************
readiness probe:
kubectl apply -f ~/environment/healthchecks/readiness-deployment.yaml
kubectl get pods -l app=readiness-deployment
kubectl describe deployment readiness-deployment | grep Replicas:
kubectl describe pods rediness-deployment-6cd488cc4d-d9vn9 -- rm /tmp/healthy
kubectl get pods -l app=readiness-deployment
 above pod ready will be 0/1 status
 it will not send the traffic to the rs/deployment
kubectl describe deployment readiness-deployment | grep Replicas:
kubectl exec -it <YOUR-READINESS-POD-NAME> -- touch /tmp/healthy
kubectl get pods -l app=readiness-deployment
