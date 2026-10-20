# Runbook: Voting App Pod Not Ready

## Alert
VotingAppPodNotReady

## 1. Identify unhealthy pods
kubectl get pods -n default -o wide
kubectl get deployments -n default
kubectl get events -n default --sort-by=.lastTimestamp | tail -20

## 2. Inspect the affected pod
kubectl describe pod <pod-name> -n default
kubectl logs <pod-name> -n default --all-containers --tail=100

## 3. Check application rollouts
kubectl rollout status deployment/voting-lab-vote -n default --timeout=60s
kubectl rollout status deployment/voting-lab-result -n default --timeout=60s
kubectl rollout status deployment/voting-lab-worker -n default --timeout=60s

## 4. Recovery
Identify the cause before changing resources. Check image errors, readiness probes, application logs, and Redis/PostgreSQL connectivity. Apply the smallest corrective change and verify pod readiness and voting functionality.

Do not delete pods, persistent volumes, databases, or namespaces as an initial response.

## 5. Close the alert
Confirm the pod is Ready, the alert clears, and the cause and resolution are documented.
