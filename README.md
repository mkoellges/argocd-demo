# argocd-demo

## 1. Install Argocd

```bash
kubectl create namespace argocd
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm install -n argocd argo-cd argo-cd/argo-cd -f values.yaml --version 5.52.0
```

## 2. Forward Port to access argoCD server

```bash
kubectl port-forward -n argocd svc/argo-cd-argocd-server 8443:443
```

## 3. Get Admin Password

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```

## 4. Update Argocd Version via helm

First check helm versions

```bash
 helm search repo argo-cd 
```

Update ArgoCD to the appropriate version:

```bash
helm upgrade argo-cd argo-cd/argo-cd \
 --version 5.52.0 \
 -f values.yaml \
 --wait \
 --namespace argocd
```
