Install:
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

View pods:
```
k get pods -n argocd
```

Get secrets:
```
k get secrets -n argocd
```

Get yaml output of the secret called: argocd-initial-admin-secret
```
k get secret argocd-initial-admin-secret -n argocd -o yaml
```

Use echo | base64 in the password field:
```
echo aS3ZkaTbU1XS3ZkaTg2S3ZkaT== | base64 -d
```

Portforward argocd-server to access:
```
k port-forward -n argocd svc/argocd-server 3443:443
```

Use 'admin' and the password to access Argo CD
