# DevOps Capstone Closeout Checklist

## Application and containers
- [x] Voting App runs locally using Kubernetes.
- [x] Vote, result, worker, Redis, and PostgreSQL components deployed.
- [x] Application container hardening changes committed.
- [ ] Verify voting and results end-to-end after the latest changes.
- [ ] Confirm repeat-vote protection and document its limitations.

## CI/CD and source control
- [x] GitHub Actions image build workflows repaired.
- [x] Changes merged and pushed to the personal GitHub repository.
- [ ] Confirm latest GitHub Actions checks pass on main.
- [ ] Review outstanding .gitignore and Helm values changes before committing.

## Infrastructure as Code
- [x] Terraform configuration initialized and validated previously.
- [ ] Review Terraform README against the actual EKS configuration.
- [ ] Run a fresh Terraform validation and plan review when AWS credentials and configuration are ready.
- [ ] Do not apply AWS resources without explicit approval and a cost review.

## Observability
- [x] Prometheus, Grafana, Fluent Bit, Loki, and Jaeger installed locally.
- [x] Prometheus VotingAppPodNotReady rule loaded and healthy.
- [x] Synthetic alert fired and was removed after testing.
- [x] Alert runbook committed and pushed.
- [ ] Export the Voting App Grafana dashboard JSON into the repository.
- [ ] Verify dashboard panels and Loki/Jaeger queries.
- [ ] Capture final evidence for the project demonstration.

## Documentation
- [x] Monitoring guide created.
- [x] Proposed SLOs documented without claiming unmeasured results.
- [x] Closeout checklist created.
- [ ] Review docs and commit the documentation files.

## Final status
This checklist is a working record. Items marked complete reflect previously confirmed work; unchecked items require verification before final submission.
