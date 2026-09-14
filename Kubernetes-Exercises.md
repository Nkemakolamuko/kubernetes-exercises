# Kubernetes Exercises

At the end of each exercise, make sure you can answer:

1. What Kubernetes concepts did you use?
2. Why is this resource or configuration needed?
3. What would happen if you removed it?


## Project 01 — **Create Your First Pod**

### What you will learn

- Pods
- YAML manifests
- kubectl
- Pod lifecycle

### Tasks

Create a Pod called: `web-po` using: `nginx:alpine`

### Requirements

1. Create the Pod using YAML.
2. Apply the manifest.
3. Verify that the Pod is running.
4. Inspect the Pod.
5. View its logs.
6. Delete the Pod.
7. Verify its removal.

---

## Project 02 — **Deployment with Three Replicas**

### What you will learn

- Deployments
- ReplicaSets
- Desired state
- Replica management

### Tasks

Create a Deployment called: `web-app` using: `nginx:alpine` with **3 replicas**.

### Requirements

1. Create the Deployment using YAML.
2. Configure 3 replicas.
3. Verify that 3 Pods are running.
4. Delete one Pod.
5. Observe what Kubernetes does.
6. Verify that the desired number of replicas is restored.

---

## Project 03 — **Expose a Deployment with a Service**

### What you will learn

- Services
- Selectors
- Endpoints
- Stable application access

### Tasks

Expose the `web-app` Deployment with a ClusterIP Service.

### Requirements

1. Create a Service for `web-app`.
2. Match the correct Pod labels with the Service selector.
3. Expose the Nginx HTTP port.
4. Verify the Service.
5. Verify that the Service has endpoints.
6. Test access to the application through the Service.

---

## Project 04 — **Expose an Application with NodePort**

### What you will learn

- NodePort
- External access
- Service types

### Tasks

Expose the `web-app` Deployment using a NodePort Service.

### Requirements

1. Create the NodePort Service.
2. Configure the correct target port.
3. Verify the assigned NodePort.
4. Access the application from outside the cluster using the
    
    appropriate address.
    
5. Verify that traffic reaches the Pods.

---

## Project 05 — **Configure an Application with a ConfigMap**

### What you will learn

- ConfigMaps
- Externalized configuration
- Environment variables

### Tasks

Create a ConfigMap containing:

```
APP_ENV=development
APP_NAME=training-app
```

Configure a workload to consume both values as environment variables.

### Requirements

1. Create the ConfigMap.
2. Reference it from the workload.
3. Deploy the workload.
4. Verify both values from inside the container.

---

## Project 06 — **Configure an Application with a Secret**

### What you will learn

- Secrets
- Sensitive configuration
- Environment variables from Secrets

### Tasks

Create a Secret containing a database username and password.

Configure a PostgreSQL-based workload to consume the credentials.

### Requirements

1. Create the Secret.
2. Store the username and password.
3. Reference the Secret from the workload.
4. Do not hard-code the password directly in the Deployment.
5. Verify that the application receives the credentials.

---

## Project 07 — **Resource Requests and Limits**

### What you will learn

- CPU requests
- Memory requests
- CPU limits
- Memory limits
- Scheduling resources

### Tasks

Create a Deployment called:

```
web-app
```

using Nginx with **3 replicas**.

Each container must have:

```
CPU request: 100m
Memory request: 128Mi

CPU limit: 500m
Memory limit: 256Mi
```

### Requirements

1. Create the Deployment.
2. Verify all 3 Pods are running.
3. Inspect one Pod.
4. Confirm the requests and limits exactly match the requirements.

---

## Project 08 — **Readiness and Liveness Probes**

### What you will learn

- Readiness probes
- Liveness probes
- Pod health
- Traffic readiness

### Tasks

Configure an Nginx Deployment with both readiness and liveness probes.

### Requirements

1. Configure an HTTP readiness probe.
2. Configure an HTTP liveness probe.
3. Deploy the application.
4. Verify both probes become successful.
5. Introduce a condition that causes one probe to fail.
6. Observe Kubernetes behavior.

---

## Project 09 — **Persistent Storage with a PVC**

### What you will learn

- PersistentVolumeClaims
- Persistent storage
- Pod recreation

### Tasks

Deploy PostgreSQL with persistent storage.

### Requirements

1. Create a PersistentVolumeClaim.
2. Configure PostgreSQL to use the claim.
3. Create test database data.
4. Delete the PostgreSQL Pod.
5. Verify Kubernetes recreates the Pod.
6. Verify the data remains available.

---

## Project 10 — **Deploy a Backend and PostgreSQL**

### What you will learn

- Multiple workloads
- Services
- Secrets
- ConfigMaps
- Persistent storage
- Service discovery

### Tasks

Deploy one backend application and one PostgreSQL database.

Use one of the trainer-provided backend application projects.

### Requirements

1. Create a workload for the backend.
2. Create a workload for PostgreSQL.
3. Create a Service for PostgreSQL.
4. Use a Secret for database credentials.
5. Use a ConfigMap for non-sensitive configuration.
6. Use persistent storage for PostgreSQL.
7. Configure the backend to connect through the PostgreSQL Service.
8. Verify the connection.

---

## Project 11 — Perform a Rolling Update

### What you will learn

- Rolling updates
- Deployment strategy
- ReplicaSets
- Application availability

### Tasks

Deploy Nginx and then update it to another valid Nginx image tag.

### Requirements

1. Start with a working Deployment.
2. Verify all replicas are healthy.
3. Update the image.
4. Observe the rollout.
5. Verify the new Pods use the new image.
6. Verify the Service remains available.

---

## Project 12 — **Roll Back a Failed Deployment**

### What you will learn

- Deployment revisions
- Rollbacks
- Release recovery

### Tasks

Intentionally update a working Deployment to an invalid image.

### Requirements

1. Start with a working Deployment.
2. Record the working revision.
3. Deploy the invalid image.
4. Observe the failed rollout.
5. Inspect the Deployment and Pods.
6. Roll back to the previous working revision.
7. Verify recovery.

---

## Project 13 — **Scale an Application**

### What you will learn

- Manual scaling
- Replicas
- Workload capacity

### Tasks

Scale:

```
web-app
```

from 3 replicas to 6 replicas.

### Requirements

1. Verify the initial replica count.
2. Increase it to 6.
3. Verify 6 Pods are running.
4. Reduce it back to 3.
5. Verify the final state.

---

## Project 14 — **Horizontal Pod Autoscaling**

### What you will learn

- HPA
- CPU-based autoscaling
- Resource requests
- Scaling behavior

### Tasks

Create an HPA for an application Deployment.

### Requirements

1. Configure CPU requests on the application.
2. Create an HPA.
3. Configure minimum replicas.
4. Configure maximum replicas.
5. Configure a CPU utilization target.
6. Generate enough load to trigger scaling.
7. Observe the replica count.
8. Stop the load and observe the scaling behavior.

---

## Project 15 — **Namespaces**

### What you will learn

- Namespaces
- Resource isolation
- Environment separation

### Tasks

Create:

```
development
production
```

Deploy the same application into both namespaces.

### Requirements

1. Create both namespaces.
2. Deploy the application into `development`.
3. Deploy it into `production`.
4. Verify that resources are separated.
5. List resources independently in each namespace.
6. Delete the development workload without affecting production.

---

## Project 16 — **Ingress**

### What you will learn

- Ingress
- HTTP routing
- Host/path rules
- Service routing

### Tasks

Expose two applications through one Ingress.

Use:

- application A
- application B

### Requirements

1. Deploy both applications.
2. Create a Service for each application.
3. Configure an Ingress.
4. Route one hostname or path to application A.
5. Route another hostname or path to application B.
6. Verify both routes.

> Your cluster must have a working Ingress controller for this exercise.
> 

---

## Project 17 — **Debug a Failed Deployment**

### What you will learn

- Pod status
- Logs
- `describe`
- Events
- Root-cause analysis

### Tasks

Deploy an intentionally broken application workload.

The failure should be caused by one configuration problem such as an

invalid image, incorrect port, incorrect environment variable, missing

ConfigMap, or missing Secret.

### Requirements

1. Identify the failure.
2. Inspect the Deployment.
3. Inspect the Pods.
4. Inspect container logs.
5. Inspect Kubernetes events.
6. Identify the root cause.
7. Fix the configuration.
8. Verify that the workload becomes healthy.

### Verification

Document:

- Symptoms
- Investigation steps
- Root cause
- Fix applied
- Verification

---

## Project 18 — **Security Context**

### What you will learn

- Security contexts
- Non-root execution
- Permissions
- Container security

### Tasks

Run an application container as a non-root user.

### Requirements

1. Configure an appropriate security context.
2. Prevent the container from running as root.
3. Start the workload.
4. Verify the user running inside the container.
5. Verify that the application still works.

---

## Project 19 — **Deploy a Redis-Backed Application**

### What you will learn

- Multiple services
- Redis
- PostgreSQL
- Service discovery
- Configuration management

### Tasks

Deploy an application that communicates with:

- backend
- Redis
- PostgreSQL

Use the one of the **application provided in the ZIP file above for the challenges.**

### Requirements

1. Create workloads for the required services.
2. Create Services for internal communication.
3. Configure Redis connection information.
4. Configure PostgreSQL connection information.
5. Use Secrets for sensitive values.
6. Use ConfigMaps for non-sensitive values.
7. Verify backend-to-Redis communication.
8. Verify backend-to-PostgreSQL communication.

---

## Project 20 — **Production-Style Application Deployment**

### What you will learn

- Kubernetes application architecture
- Configuration
- Secrets
- Storage
- Networking
- Health checks
- Resource management
- Scaling
- Deployment operations

### Tasks

Deploy a complete application environment containing:

- frontend or HTTP-facing service
- backend API
- PostgreSQL
- Redis

Use the one of the **application provided in the ZIP file above for the challenges.**

### Requirements

Your environment must include:

1. Deployments for application workloads.
2. Services for internal communication.
3. External access through an appropriate Service or Ingress.
4. ConfigMaps for non-sensitive configuration.
5. Secrets for sensitive configuration.
6. Persistent storage for PostgreSQL.
7. CPU and memory requests/limits.
8. Readiness and liveness probes.
9. Appropriate replica counts.
10. A rolling-update strategy.
11. An HPA where appropriate.
12. Non-root execution where supported.
13. Separate development and production namespaces.
14. Successful backend-to-database communication.
15. Successful backend-to-Redis communication.

### Verification

- [ ]  The application is accessible.
- [ ]  All required workloads are healthy.
- [ ]  Configuration is externalized.
- [ ]  Database data survives Pod recreation.
- [ ]  Backend has multiple replicas.
- [ ]  Health checks report the expected state.
- [ ]  The application recovers from a backend Pod failure.
