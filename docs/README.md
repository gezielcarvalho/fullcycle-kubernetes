# Project documentation

This folder is the current-state entry point for the Full Cycle Kubernetes
showcase. It combines a portfolio-ready overview with the retained hands-on
learning path. GitHub Issues and the personal portfolio Project track active
work; these documents preserve the durable context.

## Current-state documents

| Document | Purpose |
| --- | --- |
| [Charter](charter.md) | Purpose, audience, and success measures. |
| [Scope and roadmap](scope-and-roadmap.md) | Local-lab boundaries and review points. |
| [Architecture](architecture.md) | Go application, Kind cluster, and Kubernetes resources. |
| [Delivery and quality](delivery-and-quality.md) | Change and validation expectations. |
| [Operations](operations.md) | Local Kind/WSL operation and safety boundaries. |
| [Risks and decisions](risks-and-decisions.md) | Active risks and decision log. |
| [ADRs](adr/README.md) | Architecture decision record process. |

## Learning path and references

Read the retained learning sequence in order:

1. [Kind](01-kind.md)
2. [kubectl](02-kubectl.md)
3. [Creating a cluster](03-creating-cluster.md)
4. [Creating multi-node clusters](04-creating-multi-node-clusters.md)
5. [Pods](05-pods.md)
6. [ReplicaSets](06-replicaset.md)
7. [Upgrading applications](07-upgrading-apps.md)
8. [Deployments](08-deployment.md)
9. [Reverting a deployment](09-reverting-deployment.md)
10. [Services](10-services.md)

The root [README](../README.md) remains the detailed technical guide. The
cheatsheet image and all manifests are retained learning artifacts, not a
production runbook or evidence of a supported cluster.
