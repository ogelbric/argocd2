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

## (4) Login to Supervisor cluster and argocd namespace

```
kubectl vsphere login --server 192.168.2.201 --vsphere-username administrator@vsphere.local --insecure-skip-tls-verify
Logged in successfully.

You have access to the following contexts:
   192.168.2.201
   namespace1000
   namespaceargocd
   svc-argocd-service-domain-c10
   svc-auto-attach-domain-c10
   svc-cci-ns-domain-c10
   svc-tkg-domain-c10
   svc-velero-domain-c10

kubectl config use-context namespaceargocd
Switched to context "namespaceargocd".
```


