# k8sall
A simple script to run any shell command for all kubectl contexts

## Motivation
When dealing with multiple kubernetes clusters/contexts, some commands need to be run for all clusters. Switching contexts and running commands can be tedious if there are many clusters in the kubeconfig.

There is a comprehensive kubectl plugin [kubectl-foreach](https://github.com/ahmetb/kubectl-foreach), to run `kubectl` commands in multiple clusters with filters, but that does not cater for other commands such as `flux`, `helm` etc.

## Prerequistes
- kubectl
- [kubectx](https://github.com/ahmetb/kubectx)
Kubectx is used to switch contexts since `kubectl config use-context` can have issues if there are old unreachable contexts in the kubeconfig

## How to Run

```
./k8sall kubectl get nodes

Going to run: kubectl get pods   in  cluster-01
Are you sure? [y/N] y
.
.
.
Going to run: flux suspend kustomization myapp   in  cluster-02
Are you sure? [y/N]
```

```
./k8sall flux suspend kustomization myapp

Going to run: flux suspend kustomization myapp   in  cluster-01
Are you sure? [y/N] y
.
.
.
Going to run: flux suspend kustomization myapp   in  cluster-02
Are you sure? [y/N]
```
