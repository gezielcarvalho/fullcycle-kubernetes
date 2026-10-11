# Operations

## Current operating posture

This is a local, disposable Kind/WSL learning lab. Follow the root README and
learning sequence only after confirming Docker, Kind, kubectl, and the target
context. Prefer port-forwarding for local access.

## Safety boundary

No production cluster or cloud environment is approved. Do not apply manifests
to a shared or unknown context, publish images, expose services publicly, or
reuse learning credentials. Portainer and the Kubernetes Dashboard can provide
broad administrative access and must remain limited to a deliberate local lab.

## Before any environment is approved

Identify the owner, cluster and namespace policy, image registry, least-
privilege access, secret management, network/TLS model, resource quotas,
monitoring/logging, backups where applicable, and rollback/release gates.
Record the decision in an ADR and an approved issue before executing it.

## Cleanup and support boundary

The local cluster is disposable; follow a reviewed, explicit cleanup plan for
the named lab cluster when it is no longer needed. There is no production
on-call or incident commitment. Capture reproducible local issues in GitHub
with context, commands, expected/actual result, and safe diagnostics.
