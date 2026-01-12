# Creating a Pod with probes, resources and volumes

This lab demonstrates creating a multi-container Kubernetes Pod with shared volumes and resource management.

## What Was Done

1. **Created a Pod named `demo`** with two containers:
   - **Main container (`nginx`)**: Serves a simple HTML page with the message "Hello from demo Pod".
   - **Sidecar container (`busybox`)**: Continuously logs the date and a message every 5 seconds.

2. **Volumes Used**:
   - `emptyDir`: Shared temporary storage between the main and sidecar containers.
   - `NFS`: Persistent storage mounted from an external NFS server.

3. **Resource Management**:
   - Set CPU and memory requests and limits for both containers to control resource usage.

4. **Probes**:
   - **Liveness Probe**: Checks if the main container is alive.
   - **Readiness Probe**: Checks if the main container is ready to serve traffic.

5. **Ports**:
   - Exposed port 80 for the main container to serve HTTP content.

## Commands Used

```bash
# Create the Pod
kubectl apply -f demo-pod.yaml

# Check Pod status
kubectl get pods

# Describe the Pod for details
kubectl describe pod demo

# View logs
kubectl logs demo -c main-container
kubectl logs demo -c sidecar-container

# Test Nginx inside the Pod
kubectl exec -it demo -- curl localhost:80

# Delete the Pod
kubectl delete pod demo
