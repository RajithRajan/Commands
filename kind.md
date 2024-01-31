# Enable code completion
```
source <(kind completion zsh)
```
# Create a kind cluster
```
kind create cluster --name <cluster_name>
```
# Get clusters.
```
kind get clusters
```

# Get nodes of a cluster.
```
kind get nodes --name test-cluster
```

# Get kubeconfig and use it to talk to the cluster.
```
kind get kubeconfig --name test-cluster > ~/test-cluster-kubeconfig
kubectl --kubeconfig  ~/test-cluster-kubeconfig ...
k9s --kubeconfig  ~/test-cluster-kubeconfig
```
```
kind export kubeconfig --name test-cluster
Set kubectl context to "kind-test-cluster"
```

# Export logs
```
kind export logs --name test-cluster
```

# load images; calls `ctr images import` under the hood.
```
kind load image-archive
```

# Get IP address
```
docker container inspect test-cluster-control-plane \
 --format '{{ .NetworkSettings.Networks.kind.IPAddress }}'
```

# Delete clusters.
```
kind delete cluster --name test-cluster
```

# Check kind version
```
kind version
```

# create kind clusters with multiple nodes
```
cat <<EOF | kind create cluster --name test-cluster-with-multiple-nodes --config -
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
EOF
```
