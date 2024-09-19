App of apps is an Application Helm or Kustomizations that deploys a set of applications.

Lets create an App of Apps to deploy two applications: Giropops-senhas and Randomlogger.

Create the directory structure 
```
mkdir app-of-apps
cd app-of-apps/
mkdir templates
```
The yaml files of app-of-apps:
- giropops-app.yaml
  ```
  apiVersion: 
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
  ```
