

# Deploying nginx on Kubernetes

This guide demonstrates how to deploy nginx on Kubernetes using Deployments, Services, Ingress, tolerations, resource limits, and Horizontal Pod Autoscaler (HPA).

## Prerequisites

- Kubernetes cluster up and running
- `kubectl` command-line tool installed and configured
- Make sure node is having tolerations. else it pods will be in pending state.

## Steps

### 1. Apply Deployment for nginx

Apply the nginx Deployment YAML to create nginx pods with specified resource limits and tolerations:

```
kubectl apply -f ./deployment/deployment.yaml
```

### 2. Create a Service for nginx

Create a Service to expose nginx within the Kubernetes cluster:

```
kubectl apply -f ./service/service.yaml
```

### 3. Configure Ingress for nginx

Create an Ingress resource to route traffic to nginx using a specified domain or IP address:

```
kubectl apply -f ./ingress/ingress.yaml
```

### 4. Set up Horizontal Pod Autoscaler (HPA)

Configure HPA to automatically scale nginx pods based on CPU utilization:

```
kubectl apply -f ./hpa/hpa.yaml
```

## Verification

Ensure everything is set up correctly by checking the following resources:

```
# Check Deployment
kubectl get deployments

# Check Service
kubectl get services

# Check Ingress
kubectl get ingress

# Check HPA
kubectl get hpa
```

## Cleanup

To delete nginx deployment, service, ingress, and HPA:

```
kubectl delete deployment nginx-deployment
kubectl delete service nginx-service
kubectl delete ingress nginx-ingress
kubectl delete hpa nginx-hpa
```