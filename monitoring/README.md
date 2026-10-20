# Voting App Monitoring

## Components
- Prometheus: metrics and alert-rule evaluation
- Grafana: dashboards and visualization
- Fluent Bit: container log collection
- Loki: log storage and queries
- Jaeger: distributed tracing

## Prometheus
Access locally by forwarding the service:
kubectl port-forward -n monitoring service/prometheus-server 9090:80

Check alert rules:
curl -s http://localhost:9090/api/v1/rules

The VotingAppPodNotReady alert monitors readiness for Voting App pods in the default namespace. It fires when a matching pod remains not ready for five minutes.

## Grafana
Forward the service:
kubectl port-forward -n monitoring service/grafana 3000:80

Open http://localhost:3000 and select the Voting App Kubernetes Monitoring dashboard.

## Loki queries
All default-namespace logs:
{namespace="default"}

Vote service logs:
{namespace="default"} | json | kubernetes_labels_app="voting-lab-vote"

Result service logs:
{namespace="default"} | json | kubernetes_labels_app="voting-lab-result"

Worker service logs:
{namespace="default"} | json | kubernetes_labels_app="voting-lab-worker"

## Jaeger
Forward the service:
kubectl port-forward -n monitoring service/jaeger 16686:16686

Open http://localhost:16686 and inspect available voting-app traces.

## Troubleshooting
kubectl get pods -n monitoring
kubectl get pods -n default
kubectl get events -n monitoring --sort-by=.lastTimestamp
kubectl get events -n default --sort-by=.lastTimestamp

See [the pod readiness runbook](runbooks/voting-app-pod-not-ready.md) for incident response.
