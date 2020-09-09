# vscode-as-a-service

This project helps to provide[vscode on remote server](https://github.com/cdr/code-server) on kubernetes.

This project can provide for many user.

## Requirement
Set up [kubernetes](https://github.com/kubernetes/kubernetes) cluster and install [ESC](https://github.com/koba1t/ESC).

## Install
First, Create Namespace.
```
kubectl apply -f config/namespace.yaml
```

Apply container template and proxy resource.
```
kubectl apply -f config/esc/template.yaml
kubectl apply -f config/esc/esc-proxy.yaml
```

And setup config for `config/ingress/` resources.\
Describe is [here](https://github.com/kubernetes/ingress-nginx/tree/master/docs/examples/auth/oauth-external-auth)

Edit `config/ingress/external-auth-ingress.yaml`.Change `< YOUR_DOMAIN_NAME_HERE >` to your domain.\
And set `ssl-secret` to SSL secret for your domain.\
(I'm using [cert-manager](https://github.com/jetstack/cert-manager))

Edit `config/ingress/oauth2-proxy.yaml` to set `OAUTH2_PROXY_CLIENT_ID`,`OAUTH2_PROXY_CLIENT_SECRET` for github oauth and generate `OAUTH2_PROXY_COOKIE_SECRET` and set it.

```
kubectl apply -f config/ingress/external-auth-ingress.yaml
kubectl apply -f config/ingress/oauth2-proxy.yaml
```
