# The Hitchhiker's Guide to Testing Kubernetes

## Building the Kubernetes source code

```bash
kind build node-image .
```

If you're on an M1 Mac,

```bash
kind build node-image --arch amd64 .
```

The above command will compile the Kubernetes source code and generate the `kindest/node:latest` image locally.

## Creating the kind cluster

```bash
kind create cluster --name my-local-cluster --config kind-config.yaml
```

Once kind finishes running, try if your cluster is up and running:

```bash
kubectl get nodes
```

## Running kubetest2

```bash
kubetest2 kind -v 10 --test=ginkgo -- --use-binaries-from-path
```

If `--use-binaries-from-path` throws an error:

```bash
export PATH=$PATH:/Users/your/path/to/kubernetes/_output/bin
```

## Running hydrophone

```bash
hydrophone --kubeconfig="~/.kube/config" --conformance
```
