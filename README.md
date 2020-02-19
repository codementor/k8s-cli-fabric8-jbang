# k8s-cli-fabric8-jbang project

This project is an example of how to extend kubernetes cli (kubectl) with a Java application.  It demonstrates the use of [Fabric8 Kubernetes Client](https://github.com/fabric8io/kubernetes-client) and access the Kubernetes API.  In order to be a kubectl plugin it is necessary to have a file which uses the defined naming convention of `kube-<plugin-name>`.  This is a challenge in Java, but can be done with `jbang`. In order to provide a good CLI experience [picocli](https://picocli.info/) is used.


## Prerequisites

* Running Kubernetes 1.15+ cluster.  [Kind 0.7.0](https://github.com/kubernetes-sigs/kind) was used for testing.
* Java 1.8 and [jbang 0.16+](https://github.com/maxandersen/jbang)

## j'bang and Fabric8

I have found that the quickest way to get started with kubectl plugins and Kubernetes development in Java is jbang and fabric8.   jbang strips away the extra cruft allowing demonstrations to be barebones what is necessary.  Fabric8 provides a way of accessing the Kubernetes API in a Java friendly way without all the (null, null, null, null...).  

## Getting Started

Start a cluster:  `kind create cluster`

and run one of the commands:  `./kubectl-example pod list`

Example:

```bash
./kubectl-example pod list
________________________________________________________________
| Pod Name                                  | namespace         |
|===============================================================|
| coredns-6955765f44-f966p                  | kube-system       |
| coredns-6955765f44-xnzbg                  | kube-system       |
| etcd-kind-control-plane                   | kube-system       |
| kindnet-cznll                             | kube-system       |
| kube-apiserver-kind-control-plane         | kube-system       |
| kube-controller-manager-kind-control-plane| kube-system       |
| kube-proxy-tw9cb                          | kube-system       |
| kube-scheduler-kind-control-plane         | kube-system       |
| local-path-provisioner-7745554f7f-gk5j9   | local-path-storage|
```

## List of Commands

* pod list
* pod add <pod-name> [-n namespace] [-i image]
* resources

## Adding as a kubectl plugin

The executable needs to be the path.  From the root of the project run: `export PATH=$PATH:$PWD`

Now give `kubectl` a try with `example`.  run: `kubectl example pod list`
You should get the same output as above.
