# Chaos Engineering

Simple repo to demo Kubernetes, Linkerd, and Kubedoom.

## TODO
- Add a presentation

## Useful Commands

Start a Kubernetes Cluster in Kind:
```shell
$ brew install kind
$ kind create cluster
```

Install Linkerd:
```shell
$ linkerd install | kubectl apply -f -
```

Install Linkerd Viz:
```shell
$ linkerd viz install | kubectl apply -f -
```

Install Buoyant Cloud:
```shell
$ kubectl apply -f https://buoyant.cloud/agent/<snipped>
```

Deploy the Chaos Server:
```shell
$ kubectl apply -k deploy/chaos-server
```

Deploy the Chaos Client:
```shell
$ kubectl apply -k deploy/chaos-client
```

View Client Status:
```shell
$ watch -n 1 kubectl logs -n chaos-client deploy/chaos-client --tail 1
```

View Client Status in JSON with JQ formatting:
```shell
$ watch 'kubectl logs -n chaos-client deploy/chaos-client --tail 1 | jq'
```

Deploy the Chaos Server Authroization:
```shell
$ kubectl apply -k deploy/chaos-server-authorization
```

Deploy the Chaos Server Service Profile:
```shell
$ kubectl apply -k deploy/chaos-server-profile
```

View Effective Success Rate:
```shell
$ linkerd viz routes deploy/chaos-client -n chaos-client --to service/chaos-server --to-namespace chaos-server -o wide
```

Deploy Kubedoom:
```shell
$ kubectl apply -k deploy/kubedoom
```

Port-Forward Kubedoom
```
$ kubectl port-forward -n kubedoom deploy/kubedoom 5900:5900
```

## VNC Tips:
* Use Tiger VNC: http://tigervnc.bphinz.com/nightly/
* connect to `127.0.0.1`
* password is `idbehold`

## Doom Tips:
* `iddqd` God Mode
* `idfa` All Weapons, etc
