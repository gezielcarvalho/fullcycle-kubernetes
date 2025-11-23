# Full Cycle Kubernetes Learning Repository

A comprehensive hands-on repository for learning Kubernetes fundamentals, featuring a Go-based web application with practical examples of pods, deployments, services, and replica sets.

## 📋 Overview

This repository contains a complete learning path for Kubernetes, including:

- A simple Go web server application
- Kubernetes manifests for various deployment scenarios
- Documentation covering essential Kubernetes concepts
- Multi-node cluster configuration using Kind (Kubernetes in Docker)

## 🚀 Quick Start

### Prerequisites

- Docker installed
- Kind (Kubernetes in Docker) installed
- kubectl CLI tool installed
- Go 1.23.3+ (for local development)

### Running the Application

1. **Build the Docker image:**

```bash
cd app
docker build -t gezielcarvalho/hello-go:latest .
```

2. **Create a Kind cluster:**

```bash
kind create cluster --config=k8s/kind-config.yaml --name fullcycle
```

3. **Deploy Portainer UI (recommended first):**

```bash
kubectl apply -f k8s/portainer.yaml

# Wait for Portainer to be ready
kubectl wait --for=condition=ready pod -l app=portainer -n portainer --timeout=90s

# Access Portainer
kubectl port-forward -n portainer svc/portainer 9000:9000
# Open http://localhost:9000 in your browser
```

4. **Deploy the Go application:**

5. **Deploy the Go application:**

```bash
# Using Deployment (recommended)
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

# Or using Pod directly
kubectl apply -f k8s/pod-config.yaml

# Or using ReplicaSet
kubectl apply -f k8s/replicaset.yaml
```

5. **Access the application:**

```bash
kubectl port-forward service/goserver-service 8080:8080
# Visit http://localhost:8080
```

> 💡 **Tip**: Use Portainer (http://localhost:9000) to visually monitor your deployments, pods, and services!

## 📁 Project Structure

```
.
├── app/                    # Go application source code
│   ├── Dockerfile          # Container image definition
│   ├── server.go           # Simple HTTP server
│   └── go.mod              # Go module definition
├── k8s/                    # Kubernetes manifests
│   ├── deployment.yaml     # Deployment configuration (6 replicas)
│   ├── service.yaml        # ClusterIP service
│   ├── replicaset.yaml     # ReplicaSet configuration
│   ├── pod-config.yaml     # Single pod configuration
│   ├── kind-config.yaml    # Multi-node cluster setup
│   ├── portainer.yaml      # Portainer UI for cluster management
│   └── kubernetes-dashboard.yaml  # Kubernetes Dashboard setup
└── docs/                   # Learning documentation
    ├── 01-kind.md
    ├── 02-kubectl.md
    ├── 03-creating-cluster.md
    ├── 04-creating-multi-node-clusters.md
    ├── 05-pods.md
    ├── 06-replicaset.md
    ├── 07-upgrading-apps.md
    ├── 08-deployment.md
    ├── 09-reverting-deployment.md
    └── 10-services.md
```

## 🎯 Application Details

The Go application (`app/server.go`) is a simple HTTP server that:

- Listens on port 8000
- Returns a greeting message with the hostname
- Useful for demonstrating load balancing across multiple pods

**Current Configuration:**

- Image: `gezielcarvalho/hello-go:v11`
- Deployment: 6 replicas
- Service: ClusterIP on port 8080
- Resource Limits: 128Mi memory, 500m CPU
- Resource Requests: 64Mi memory, 250m CPU

## 📚 Learning Path

Follow the documentation in order to understand Kubernetes concepts progressively:

1. **Kind** - Setting up local Kubernetes clusters
2. **kubectl** - Command-line tool basics
3. **Creating Clusters** - Basic cluster creation
4. **Multi-Node Clusters** - Advanced cluster configurations
5. **Pods** - Understanding the smallest deployable units
6. **ReplicaSets** - Managing pod replicas
7. **Upgrading Apps** - Rolling updates and versioning
8. **Deployments** - Declarative application management
9. **Reverting Deployments** - Rollback strategies
10. **Services** - Exposing applications

## 🔧 Kubernetes Resources Included

### Pod Configuration

- Single container pod
- Resource requests and limits
- Labels for organization

### ReplicaSet

- 2 replicas configuration
- Selector-based pod management
- Version tracking with annotations

### Deployment

- 6 replicas for high availability
- Rolling update strategy
- Change cause tracking
- Version management (currently v11)

### Service

- Type: ClusterIP
- Port mapping: 8080 → 8000
- Selector-based pod discovery

### Kind Cluster

- 1 control-plane node
- 3 worker nodes
- Multi-node setup for realistic scenarios

### Portainer UI

- Web-based Kubernetes management interface
- NodePort service on port 30777
- Persistent volume for data storage
- Full cluster admin access for learning purposes

### Kubernetes Dashboard (Optional)

- Official Kubernetes web UI
- Can be installed for native cluster visualization
- Alternative to Portainer for cluster management

## 🛠️ Common Commands

```bash
# Check deployment status
kubectl get deployments
kubectl get pods
kubectl get services

# Scale deployment
kubectl scale deployment goserver --replicas=10

# Update deployment image
kubectl set image deployment/goserver goserver=gezielcarvalho/hello-go:v12

# View deployment history
kubectl rollout history deployment/goserver

# Rollback deployment
kubectl rollout undo deployment/goserver

# View pod logs
kubectl logs -l app=goserver

# Delete resources
kubectl delete -f k8s/deployment.yaml
kubectl delete -f k8s/service.yaml

# Portainer UI commands
kubectl get all -n portainer
kubectl port-forward -n portainer svc/portainer 9000:9000
# Access at http://localhost:9000

# Check Portainer pod status
kubectl get pods -n portainer
kubectl logs -n portainer -l app=portainer
```

## 🌟 Key Features Demonstrated

- **High Availability**: Multiple replicas across worker nodes
- **Resource Management**: CPU and memory limits/requests
- **Rolling Updates**: Zero-downtime deployments
- **Service Discovery**: ClusterIP service for internal communication
- **Load Balancing**: Traffic distribution across pods
- **Self-Healing**: Automatic pod replacement on failure
- **Web UI Management**: Portainer for visual cluster management and monitoring

## 📖 Kubernetes Concepts

### Pods

A Pod is the smallest deployable unit in Kubernetes, which can contain one or more containers. Pods share the same network namespace and can communicate with each other using localhost.

### Deployments

A Deployment manages the lifecycle of Pods and provides declarative updates. It enables rolling updates, rollbacks, and scaling for stateless applications.

### ReplicaSets

A ReplicaSet ensures a specified number of Pod replicas are running at any given time. Deployments automatically create and manage ReplicaSets.

### Services

Services provide a stable network endpoint to access a logical set of Pods, enabling service discovery and load balancing.

## 🖥️ Cluster Management UI

This repository includes two options for managing your Kubernetes cluster through a web interface:

### Portainer (Recommended for Beginners) ✅

Portainer provides a user-friendly web interface for managing your Kubernetes cluster. It's perfect for visualizing your infrastructure and learning Kubernetes concepts.

**Installation:**

```bash
kubectl apply -f k8s/portainer.yaml
```

**Access (Port-Forward Method - Recommended for Kind):**

```bash
kubectl port-forward -n portainer svc/portainer 9000:9000
```

Then open: **http://localhost:9000**

**Features:**

- Visual representation of all cluster resources (pods, deployments, services, etc.)
- Real-time monitoring and logs
- Easy deployment management
- Resource usage dashboards
- Persistent data storage (1Gi volume)

**First-time Setup:**

1. Open **http://localhost:9000** (ensure port-forward is running)
2. Create an admin password (minimum 12 characters)
3. Click "Get Started" to connect to the local Kubernetes environment
4. Explore your cluster resources visually!

**What You Can Do with Portainer:**

- 📊 View all deployments, pods, services, and replica sets in a visual dashboard
- 🔍 Inspect individual pods and view their logs in real-time
- 📈 Monitor resource usage (CPU, memory) across your cluster
- 🎛️ Scale deployments up or down with a simple slider
- 🚀 Deploy new applications using forms or YAML
- 🔄 Manage pod lifecycles (restart, delete, etc.)
- 📦 View and manage persistent volumes and claims
- 🌐 Explore service endpoints and networking

> 💡 **Pro Tip**: Keep Portainer open in a browser tab while following the tutorials. It provides instant visual feedback for all kubectl commands you run!

### Kubernetes Dashboard (Official Alternative)

For a more native Kubernetes experience, you can also install the official Kubernetes Dashboard:

```bash
# Install official dashboard
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

# Apply admin user configuration
kubectl apply -f k8s/kubernetes-dashboard.yaml

# Get access token
kubectl -n kubernetes-dashboard create token admin-user

# Start proxy
kubectl proxy

# Access at: http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```

**Comparison:**

| Feature           | Portainer              | Kubernetes Dashboard  |
| ----------------- | ---------------------- | --------------------- |
| Ease of Use       | ⭐⭐⭐⭐⭐             | ⭐⭐⭐                |
| Setup Complexity  | Simple                 | Token-based auth      |
| Access Method     | Port-forward           | Proxy required        |
| Visual Appeal     | Modern, intuitive UI   | Functional, minimal   |
| Best For          | Learning, quick access | Native K8s experience |
| Container Support | Docker + K8s           | Kubernetes only       |

## 💡 Tips for Using Kind with WSL

When using Kind (Kubernetes in Docker) with WSL, keep these tips in mind:

1. **Port Forwarding**: Use `kubectl port-forward` to access services instead of NodePort
2. **Cluster Naming**: Always specify `--name fullcycle` when creating clusters for consistency
3. **Cleanup**: Delete clusters when done with `kind delete cluster --name fullcycle`
4. **Multiple Terminals**: Run port-forward commands in separate terminal windows/tabs
5. **Docker Desktop**: Ensure Docker Desktop is running with WSL2 integration enabled

## 🤝 Contributing

This is a learning repository. Feel free to fork and experiment with different configurations!

## 📝 License

This project is for educational purposes.

---

**Note**: This repository is part of the Full Cycle course material focused on Kubernetes fundamentals.
