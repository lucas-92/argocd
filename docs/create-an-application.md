## Create a token in GitHub and paste in the Argo CD UI

Create a classic token in: github/settings/developer-settings;

Paste in the password field of Argo CD ui /settings/repositories and mark the "Skip server verification" field;

Paste the https repo url and finish with connect button;

## Cloning the private-app repo and make a new branch:
```
git clone git@github.com:bernardolsp/descomplicando-gitops-no-kubernetes-argocd.git
cd descomplicando-gitops-no-kubernetes-argocd
git remote remove origin
git remote add origin git@github.com:lucas-92/descomplicando-gitops-no-kubernetes-argocd.git
git push -u origin main
git checkout -b "feat/day2"
```

## The yaml file of Application

First we will create a new directory to organize our project, because we are working with an one [repo](https://github.com/lucas-92/descomplicando-gitops-no-kubernetes-argocd):
```
mkdir applications
cd applications/
vim giropops-senhas.yaml
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
  automated: {}
```
## Applying and checking

Apply:
```
k apply -f applications/giropops-senhas.yaml
```

We can check our Application in the Argo CD UI/Applications
