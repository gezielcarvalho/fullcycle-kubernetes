# Architecture

## Component view

```text
Developer workstation (local Kind / Docker / kubectl)
  |
  v
Kind Kubernetes cluster
  |
  +-- Deployment / ReplicaSet / Pod examples
  |      |
  |      v
  |   Go HTTP application
  |
  +-- ClusterIP Service -> workload replicas
  |
  +-- Optional local management UIs: Portainer / Kubernetes Dashboard
```

The Go application is intentionally small: it responds with a greeting and
hostname so workload replication and service routing are observable. The
manifests teach alternative workload primitives; they are examples rather than
a combined production topology.

## Boundary

The Kind configuration targets a local, disposable learning cluster. Portainer
and the Kubernetes Dashboard include powerful administrative access patterns
appropriate only for that constrained lab. The repository does not define a
cloud account, ingress, TLS, registry, secret-management, monitoring, or
production support model.
