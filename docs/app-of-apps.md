App of apps is an Application Helm or Kustomizations that deploys a set of applications.

Lets create an App of Apps to deploy two applications: Giropops-senhas and Randomlogger.

Create the directory structure 
```
mkdir app-of-apps
cd app-of-apps/
mkdir templates
cd templates/
```
The yaml files of app-of-apps:
- giropops-app.yaml
  ```
  apiVersion: argoproj.io/v1alpha1
  kind: Application
  metada:
    name: giropops-senhas
    namespace: argocd
  spec:
    destination:
      namespace: giropops-senhas
      server: https://kubernetes.default.svc
    project: default
    source:
      path: giropops-senhas/helm
      repoURL: https://github.com/lucas-92/descomplicando-gitops-no-kubernetes-argocd.git
      targetRevision: feat/day2
    syncPolicy:
      automated:
        selfHeal: true
      syncOptions:
      - CreateNamespace=true
  ```
- randomlogger-app.yaml
  ```
  apiVersion: argoproj.io/v1alpha1
  kind: Application
  metada:
    name: random-logger
    namespace: argocd
  spec:
    destination:
      namespace: random-logger
      server: https://kubernetes.default.svc
    project: default
    source:
      path: random-logger/helm
      repoURL: https://github.com/lucas-92/descomplicando-gitops-no-kubernetes-argocd.git
      targetRevision: feat/day2
    syncPolicy:
      automated:
        selfHeal: true
      syncOptions:
      - CreateNamespace=true
  ```
- Chart.yaml
  ```
  apiVersion: v2
  name: app-of-apps
  description: A Helm chart for app-of-apps
  version: 0.1.0
  ```
Create the `app-of-apps.yaml` file inside `application/` directory
- app-of-apps.yaml
```
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: app-of-apps
  namespace: argocd
spec:
  destination:
    namespace: argocd
    server: https://kubernetes.default.svc
  project: default
  source:
    path: app-of-apps
    repoURL: https://github.com/lucas-92/descomplicando-gitops-no-kubernetes-argocd.git
    targetRevision: feat/day2
  syncPolicy:
    automated:
      selfHeal: true
    syncOptions:
    - CreateNamespaces=true
```
Committing the changes:
```
git add .
git commit -m "feat: add app of apps"
git push
```
