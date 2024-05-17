## Containers -> Pods -> Services -> Service Mesh
### Containers
- **lxc** (Linux Containers)
	- Performance Isolation
- **Docker**
	- Packaging
- **Kubernetes**
	- Container cluster management (deployment/scaling)
### Pods
- Unit of Deployment composed of containers sharing a single
	- Pod IP address, mapped to the node IP via [[Networks#NAT (Network Address Translation)|NAT]]
	- Pod network namespace
## Microservice Application
- Backed by a cluster of **Pods**, often replicas
- Identified by a name and VIP (Virtual IP) via Kubernetes DNS
- Properties:
	- protocols
	- ports
	- DNS name
	- VIPs (Virtual IPs)
- Kubernetes DNS implemented as service mapping to DNS server pods
### Service Mesh
- Infrastructure layer for facilitating service-to-service communications
	- Policy-based communication
- Example: **Istio**, **Consul**, **NGINX**, and **Linkerd**
---
## Reverse Proxy
- Sits in front of backend applications to route client requests.
- Mediates
	- load balancing
	- health checks/observability
	- TLS termination
	- HTTP2 proxying
- Examples:
	- **HAProxy**
	- **Envoy**
## gRPC Proxy
- stateless reverse proxy for gRPC ingress/egress of a etcd core cluster
## Sidecar Proxy
- Reverse proxy for microservices. Routes requests to/from other microservices, constituting a Service Mesh.
	- Deployed together with (same host/**Pod**) application
	- Transparent to application
	- Unaware of application services topology
- Mediates (in addition to **Reverse Proxy** functionality)
	- dynamic service discovery
	- gRPC proxying
## East-West Traffic
- Network traffic among devices within the same data center
## North-South Traffic
- Network traffic across the boundaries of a data center
---
## ReST (Representational State Transfer)
- Architectural Constraints
	- Client-Server
		- Separation of Concerns
	- Statelessness
		- No session information retained by receiver
	- Cacheability
	- Layered System
	- Uniform Interface
		- Resource representations (HTML, XML, and JSON)
		- All resources reachable through links contained in other resources
---
# Tools
### Envoy
- Ingress/Egress in a service mesh (service/sidecar proxy) & as API Gateway
## Istio
- Service mesh for Kubernetes
	- **Envoy proxy**: typically sidecar for microservice applications
	- Data plane: all Envoy proxies acting as sidecars
	- Control plane: Manages data plane
- Enables:
	- circuit breaking
	- fault injection
	- Envoy proxy communication policies
## etcd
- strongly consistent, distributed key-value store
- Mediates
	- service discovery
	- shared configuration
	- scheduler coordination
## Protobuf (Protocol Buffer)
- Allows definition of structured data for communication protocols
- cross-language & cross-project
- Uses binary format
- Much faster than a series of HTTP requests
- Used by: **Envoy Proxy** and Google Cloud
## gRPC
- RPC using Protobufs