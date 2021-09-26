# Chaos Engineering

Simple repo to demo chaos engineering concepts internally

## Plans
- Demo Linkerd Service Profiles to perform automated retries of pods

## TODO
- Add more plans

## Useful Commands

View Effective Success Rate:
```shell
$ linkerd viz routes deploy/chaos-client -n chaos-client --to service/chaos-server --to-namespace chaos-server -o wide
```
