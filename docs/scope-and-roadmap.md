# Scope and roadmap

## Current scope

- A compact Go HTTP application that demonstrates workload replicas and load
  balancing.
- Local Kind cluster configuration and Kubernetes manifests for pods,
  ReplicaSets, Deployments, Services, and upgrade/rollback learning.
- A progressive documentation sequence for Kubernetes fundamentals.
- Optional Portainer and Kubernetes Dashboard artifacts for local exploration.

## Explicitly out of scope

- Production hosting, cloud clusters, public endpoints, or operational support.
- Applying manifests outside a consciously created, disposable local lab.
- Publishing container images, managing registry credentials, or storing
  secrets.

## Roadmap review points

1. Revalidate the local Kind, Docker, kubectl, and Go prerequisites before a
   live demonstration.
2. If production-grade Kubernetes becomes a portfolio goal, define a separate
   environment, security model, observability plan, and release process first.
3. Add advanced topics only through separately scoped issues that preserve the
   progressive learning sequence.
