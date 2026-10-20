# Voting App Service-Level Objectives

## Scope
These are proposed initial objectives for the local capstone environment. They are targets, not measured performance claims.

## Availability
- Objective: at least 99.5% successful availability over a rolling 30-day period.
- Measurement: successful HTTP requests divided by all valid requests to the vote and result services.
- Exclusions: planned maintenance and explicitly documented test outages.

## Latency
- Objective: 95% of vote and result HTTP requests complete within 500 ms over a rolling 30-day period.
- Measurement: HTTP request duration metrics, where instrumentation exposes them.

## Voting correctness
- Objective: every accepted vote is persisted and reflected in the results without being counted more than once per permitted voter.
- Validation: submit test votes, inspect the result page, and test repeat-vote protection.

## Alerting
- Alert: VotingAppPodNotReady.
- Trigger: a matching Voting App pod remains not ready for five minutes.
- Response: follow monitoring/runbooks/voting-app-pod-not-ready.md.

## Limitations
The current local environment does not yet provide a verified 30-day measurement window. Do not claim these objectives have been achieved until metrics have been collected and reviewed. Browser-based repeat-vote protection is not equivalent to strong identity-based vote enforcement.
