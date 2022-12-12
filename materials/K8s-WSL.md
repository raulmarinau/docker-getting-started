# K8s WSL

## Installation instructions
https://kubernetes.io/blog/2020/05/21/wsl-docker-kubernetes-on-the-windows-desktop/

## Requirements
WSL2 - Ubuntu
Docker (for Windows) with wsl2 backend

## Steps adjusted for KinD

### Do NOT update sudoers (you might forget password)

### Check kubectl version for client version

Browse https://github.com/kubernetes-sigs/kind/releases and find suitable release to download
In tutorial v0.7.0 is listed which will be outdated by Docker Desktop

### Dashboard

Follow https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md
If you fail to generate token

## Minikube

Harder to install in WSL2, not worth dealing with systemd.
