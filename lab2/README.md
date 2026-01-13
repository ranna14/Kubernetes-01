# Pods and Services

This is a lab practice for creating and interacting with Kubernetes Pods and Services. The lab demonstrates **ClusterIP** and **NodePort** services, accessing services from within and outside the cluster, and basic pod customization.

---

  - Create Pods
  - Access Pods and Customize
  - Create a ClusterIP Service
  - Access the ClusterIP Service
  - Create a NodePort Service
  - Access NodePort Service

---
### 1. Create Pods

Create two Nginx Pods using the `pods.yaml` file
Apply configuration
```
kubectl apply -f pods.yaml
kubectl get pods
```

### 2. Access Pods and Customize
Login to each pod and customize the index.html
```
kubectl exec -it web-app01 -- bash
kubectl exec -it web-app02 -- bash
```

### 3. Create a ClusterIP Service
Create clusterip-service-yaml
Apply it
```
kubectl apply -f clusterip-service.yaml
kubectl get svc
```

### 4. Access the ClusterIP Service
From a new pod
```
kubectl run ubuntu --image=ubuntu -it --rm -- /bin/bash
apt update && apt install -y curl
curl my-clusterip-service.default.svc.cluster.local
curl my-clusterip-service
exit
```

### 5. Create a NodePort Service
Create nodeport-service.yaml
Apply it 
```
kubectl apply -f nodeport-service.yaml
```

### 7. Access NodePort Service
```
http://<node-ip>:30007
```

---

## Observations

ClusterIP service is only accessible from inside the cluster.

NodePort service exposes the app on all nodes in the cluster at the specified port.

Each pod can be individually customized, and services can load balance traffic across multiple pods.


