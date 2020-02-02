# vscode-as-a-service

This project helps to provide[vscode on remote server](https://github.com/cdr/code-server) on kubernetes.

This project can provide for many user.

## Requirement
Set up [kubernetes](https://github.com/kubernetes/kubernetes) cluster and install [ESC](https://github.com/koba1t/ESC).

## Install
Apply container template resource.
```
kubectl apply -f config/esc/template.yaml
```

And, apply users resource.

```
kubectl apply -f config/esc/user1.yaml
kubectl apply -f config/esc/user2.yaml
kubectl apply -f config/esc/user3.yaml
```

