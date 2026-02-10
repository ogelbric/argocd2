# ArgoCD (Take2) - Using supervisor services
Evironment: vCenter 9.0.1 with Foundational Loadbalancer


## (1) Enable the creation of vCenter namespaces

![Version](https://github.com/ogelbric/argocd2/blob/main/namespaceenablement.png)


## (2) Get ArgoCD from the support Broadcom site and load it into the supervisor services

![Version](https://github.com/ogelbric/argocd2/blob/main/SupArgoCD2.png)

![Version](https://github.com/ogelbric/argocd2/blob/main/SupArgoCD.png)

The outcome is this: 

![Version](https://github.com/ogelbric/argocd2/blob/main/supOutcome1.png)

## (3) Create namesoaces for the install

namespace1000.yaml

```
apiVersion: v1
kind: Namespace
metadata:
  name: namespace1000 # Replace with your desired namespace name
  labels:
    # Optional labels
    environment: production
```
namespaceargocd.yaml

```
apiVersion: v1
kind: Namespace
metadata:
  name: namespaceargocd # Replace with your desired namespace name
  labels:
    # Optional labels
    environment: production
```

```
kubectl apply -f ./namespace1000.yaml
kubectl apply -f ./namespaceargocd.yaml
```

![Version](https://github.com/ogelbric/argocd2/blob/main/Outcome2.png)


