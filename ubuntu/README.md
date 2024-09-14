# Ubuntu Deployment with Kustomize

## Overview
This project demonstrates how to deploy and manage an **Ubuntu** environment using **Kustomize** for Kubernetes configuration management. The primary goal is to simplify and manage Kubernetes deployment customization, especially when working with various environments (e.g., dev, prod).

## Prerequisites
1. **Kubernetes Cluster**: Ensure that you have a running Kubernetes cluster (local or cloud). In my case, I am using podman kind.
2. **kubectl**: Kubernetes command-line tool installed on your machine.
3. **Kustomize**: Kustomize is integrated into kubectl as of version 1.14+, but you can also install it separately.

## Deployment Instructions

```bash
❯ kustomize build ./overlay/dev/ | k apply -f -
namespace/tools-dev created
deployment.apps/dev-ubuntu-deployment created

❯ k get deploy,pod -n tools-dev
NAME                                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/dev-ubuntu-deployment   1/1     1            1           29s

NAME                                         READY   STATUS    RESTARTS   AGE
pod/dev-ubuntu-deployment-6cffcfdd96-5v6hp   1/1     Running   0          29s

❯ k logs pod/dev-ubuntu-deployment-6cffcfdd96-5v6hp -n tools-dev
Hello World, this is DEV mode
```
