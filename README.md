# argocd-demo

## 1. Install Argocd

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## 2. Forward Port to access argoCD server

```sh
kubectl port-forward -n argocd svc/argocd-server 8443:443
```

## 3. Get Admin Password

```sh
kubectl get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
