# Kubernetes Poll Application

A simple web poll application deployed using Kubernetes and Traefik.

## Components
- **Poll**: Flask app (collects votes, pushes to Redis)
- **Redis**: Vote queue
- **Worker**: Java app (moves votes to PostgreSQL)
- **PostgreSQL**: Stores votes
- **Result**: Node.js app (displays results)

## Access:
- *Poll*: poll.dop.io:30021
- *Result*: result.dop.io:30021
- *Traefik Dashboard*: localhost:30042

### Load Balancer
- **Traefik**: Acts as a reverse proxy and load balancer, exposing ports 80 and 8080 within the Kubernetes cluster, and ports 30021 and 30042 on the host.

### Databases
- **Redis**: Non-replicated, exposed on port 6379.
- **PostgreSQL**: Non-replicated, persistent storage, exposed on port 5432.

### Services
- **Poll**: Flask application, exposed on port 80, routed via Traefik.
- **Worker**: Java application, not exposed via Traefik.
- **Result**: Node.js application, exposed on port 80, routed via Traefik.

### Monitoring
- **cAdvisor**: Monitors container performance, exposed on port 8080.

## Auteur

- **HICHEM GOUIA** - (https://github.com/iamhmh)