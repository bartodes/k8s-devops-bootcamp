# k8s_devops_bootcamp

## Instructions

### Install Argo CD

```sh
# Create namespace
kubectl create namespace argocd
# Install Argo in your Cluster
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
# Forward the Argo server to port 8080
kubectl port-forward svc/argocd-server -n argocd 8080:443
# Print password for admin user
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```

### Deploy Applications to Argo

```sh
cd k8s-devops-bootcamp
kubectl apply -f application.yaml
```