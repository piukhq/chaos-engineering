# Chaos Engineering

Simple repo to demo Kubernetes, Linkerd, and Kubedoom.

## TODO
- Add a presentation

## Useful Commands

Start a K3s Cluster in Lima:
```shell
$ brew install lima
$ limactl start https://raw.githubusercontent.com/lima-vm/lima/master/examples/k3s.yaml
$ mkdir -p "~/.lima/k3s/conf"
$ export KUBECONFIG="~/.lima/k3s/conf/kubeconfig.yaml"
$ limactl shell k3s sudo cat /etc/rancher/k3s/k3s.yaml >$KUBECONFIG
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

Deploy the Chaos Server Authroization:
```shell
$ kubectl apply -k deploy/chaos-server-authorization
```

Deploy the Chaos Server Service Profile:
```shell
$ kubectl apply -k deploy/chaos-server-authorization
```

View Effective Success Rate:
```shell
$ linkerd viz routes deploy/chaos-client -n chaos-client --to service/chaos-server --to-namespace chaos-server -o wide
```
