# argocd-demo

## 1. Install Argocd

```sh
kubectl create namespace argocd
kubectl apply -n argocd -k "https://github.com/argoproj/argo-cd/manifests/crds?ref=v2.4.9"

```

## 2. Forward Port to access argoCD server

```sh
kubectl port-forward -n argocd svc/argocd-server 8443:443
```

## 3. Get Admin Password

```sh
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```
