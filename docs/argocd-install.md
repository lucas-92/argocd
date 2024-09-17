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

