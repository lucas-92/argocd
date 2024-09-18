## Create a token in GitHub and paste in the Argo CD UI

Create a classic token in: github/settings/developer-settings;

Paste in the password field of argocd/repositories and mark the "Skip serve verification" field;

Paste the https repo url and finish with connect button;

## The yaml file of application

First we will create a new directory to organize our project, because we are working with an one [repo](https://github.com/lucas-92/descomplicando-gitops-no-kubernetes-argocd):
```
mkdir applications
```

We need three sections base in our file:
- spec.source:
```
source:
  helm: {}
  repoURL: 'https://github.com/lucas-92/descomplicando-gitops-no-kubernetes-argocd'
  targetRevision: feat/day2
  path: giropops-senhas/helm
```
- spec.destination:
```
destination:
  namespace: giropops-senhas
  server: 'https://kubernetes.default.svc'
```
- spec.syncPolicy:
```
syncPolicy:
  automated
```
