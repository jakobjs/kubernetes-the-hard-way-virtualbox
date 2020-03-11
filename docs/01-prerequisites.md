# Prerequisites

## VirtualBox

This tutorial leverages [VirtualBox](https://www.virtualbox.org/) to streamline provisioning of the compute infrastructure required to bootstrap a Kubernetes cluster from the ground up. Click to [download and install VirtualBox](https://www.virtualbox.org/wiki/Downloads).

### Vagrant

The [Vagrant](https://www.vagrantup.com/) binary should be installed on your system. Also set up [vagrant-hosts](https://github.com/oscar-stack/vagrant-hosts) that can manage `/etc/hosts`:

```
vagrant plugin install vagrant-hosts
```

> Output

```
Installing the 'vagrant-hosts' plugin. This can take a few minutes...
Installed the plugin 'vagrant-hosts (2.8.0)'!
```

Next: [Installing the Client Tools](02-client-tools.md)
