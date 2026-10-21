# Voting App DevOps Capstone Closeout Checklist

## 1. Application and containers

- [x] Voting App deployed successfully on the local Kubernetes cluster.
- [x] Vote, result, worker, Redis, and PostgreSQL components are running.
- [x] Application container hardening changes committed.
- [x] Voting page loads successfully.
- [x] A submitted vote is processed and appears on the results dashboard.
- [x] All three voting candidates appear on the voting and results pages.
- [x] Repeat-vote protection tested in the same browser.
- [x] Browser-based repeat-vote protection limitation documented.
- [ ] Capture final application test evidence for the demonstration.

Note: Same-browser repeat-vote protection is not strong identity enforcement.
Clearing browser data or using another browser or device may bypass it.

## 2. Source control and CI/CD

- [x] Changes pushed to the personal GitHub repository.
- [x] GitHub Actions validation passes on main for the latest commits.
- [x] Docker image build workflows previously completed successfully.
- [x] Terraform validation workflow previously completed successfully.
- [x] Terraform plan files excluded through .gitignore.
- [ ] Review the remaining local Helm values change before committing.
- [ ] Confirm the final repository working tree is clean.

Repository:
https://github.com/Emah1/example-voting-app

## 3. Infrastructure as Code

- [x] Terraform configuration initialized and validated previously.
- [x] Terraform formatting and validation completed previously.
- [ ] Review the Terraform README against the actual EKS configuration.
- [ ] Configure AWS CLI credentials safely.
- [ ] Review Terraform configuration and estimated AWS costs.
- [ ] Run a fresh Terraform validation and plan review when ready.
- [ ] Obtain explicit approval before creating any AWS resources.

Safety requirement: Do not run terraform apply or create billable AWS
resources without explicit approval and a cost review.

## 4. Monitoring and observability

- [x] Prometheus installed locally.
- [x] Grafana installed locally.
- [x] Fluent Bit installed locally.
- [x] Loki installed locally.
- [x] Jaeger installed locally.
- [x] VotingAppPodNotReady alert rule loaded and healthy.
- [x] Synthetic alert tested and removed after verification.
- [x] Alert runbook committed and pushed.
- [x] Voting App Grafana dashboard exported to the repository.
- [x] Dashboard JSON validated.
- [x] Dashboard includes Running Pods and Voting App CPU Usage panels.
- [x] Loki readiness endpoint returned ready.
- [x] Loki query returned Voting App container logs.
- [x] Jaeger displayed the voting-app-vote service.
- [x] Jaeger traces found and opened successfully.
- [ ] Capture final monitoring evidence for the demonstration.

Dashboard export:
monitoring/grafana/voting-app-kubernetes-monitoring.json

Monitoring documentation:
monitoring/README.md

Alert runbook:
monitoring/runbooks/voting-app-pod-not-ready.md

## 5. Documentation

- [x] Monitoring guide created and committed.
- [x] Proposed SLOs documented without claiming unmeasured results.
- [x] Capstone closeout checklist created and committed.
- [x] Grafana dashboard JSON committed and pushed.
- [x] Prometheus alert and runbook committed and pushed.
- [ ] Review the Terraform README and final documentation for accuracy.

## 6. Final sign-off

- [ ] Review all remaining Git changes.
- [ ] Ensure no secrets, Terraform state files, or plan files are committed.
- [ ] Run final application and repository checks.
- [ ] Verify the final GitHub Actions status.
- [ ] Prepare the capstone demonstration and explain the architecture.
- [ ] Review outstanding requirements against the official TS Academy brief.

## AWS cost protection

All current local Kubernetes and monitoring work is intended for the
local lab environment. AWS resources must not be provisioned until the
configuration, cost implications, and explicit approval have been reviewed.
