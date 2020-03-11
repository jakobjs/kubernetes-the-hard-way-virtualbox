# Provisioning Pod Network Routes

## Flannel

Set up [Flannel](https://github.com/coreos/flannel#flannel) for container networking.

```
wget --quiet --show-progress https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
```

Modify the lines in kube-flannel.yml:

```
        - --ip-masq
        - --kube-subnet-mgr
```

To:

```
        - --ip-masq
        - --kube-subnet-mgr
        - --iface-regex=192\.168\.100\.[0-9]{0,3}
		- --healthz-port=8445
```

```
kubectl apply -f kube-flannel.yml
```

> output

```
clusterrole "flannel" created
clusterrolebinding "flannel" created
serviceaccount "flannel" created
configmap "kube-flannel-cfg" created
daemonset "kube-flannel-ds" created
```

### Check Flannel status
```
kubectl -n kube-system get pods
```

> output

```
NAME                    READY     STATUS    RESTARTS   AGE
kube-flannel-ds-8p2pd   1/1       Running   0          1m
kube-flannel-ds-9mxnc   1/1       Running   0          1m
kube-flannel-ds-ldfq6   1/1       Running   0          1m
```

Check if worker nodes are `Ready`。

```
kubectl get nodes
```

> output

```
NAME       STATUS    ROLES     AGE      VERSION
worker-0   Ready     <none>    3m       v1.17.3
worker-1   Ready     <none>    3m       v1.17.3
worker-2   Ready     <none>    3m       v1.17.3
```

Next: [Deploying the DNS Cluster Add-on](12-dns-addon.md)
