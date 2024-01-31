## Cluster Management
- **Create a Cluster**
  ```
   k3d cluster create <cluster-name>
  ```
- **Delete a Cluster:**
  ```
  k3d cluster delete <cluster-name>
  ```
- **List Clusters:**
  ```
  k3d cluster list
  ```
- **Start a Cluster:** 
  ```
  k3d cluster start <cluster-name>
  ```
- **Stop a Cluster:** 
  ```
  k3d cluster stop <cluster-name>
  ```

## Node Management
- **Create Node:** 
  ```
  k3d node create <node-name> --cluster <cluster-name>
  ```
- **Delete Node:** 
  ```
  k3d node delete <node-name>
  ```
- **List Nodes:** 
  ```
  k3d node list
  ```

## Working with Images
- **Import Image:** 
  ```
  k3d image import <image-name> -c <cluster-name>
  ```

## Advanced Usage
- **Create Cluster with Multiple Servers (HA):**
  ```
  k3d cluster create <cluster-name> --servers <number-of-servers> --agents <number-of-agents>
  ```

- **Create Cluster with Specific Kubernetes Version:**
  ```
  k3d cluster create <cluster-name> --image rancher/k3s:<version>
  ```

- **Create Cluster with Port Mapping:**
  ```
  k3d cluster create <cluster-name> -p "<host-port>:<container-port>@loadbalancer"
  ```

- **Create Cluster with Volume Mapping:**
  ```
  k3d cluster create <cluster-name> -v "/path/on/host:/path/in/node@<node-name-or-role>"
  ```

- **Use Existing Network:**
  ```
  k3d cluster create <cluster-name> --network <docker-network-name>
  ```

- **Enable Kubernetes Feature:**
  ```
  k3d cluster create <cluster-name> --k3s-server-arg '--feature-gates=FeatureName=true'
  ```

## Configuration Files
- **Use Config File:** 
  ```
  k3d cluster create --config config.yaml
  ```

## Accessing Clusters
- **Get Kubeconfig:** 
  ```
  k3d kubeconfig get <cluster-name>
  ```
- **Merge Kubeconfig:** 
  ```
  k3d kubeconfig merge <cluster-name> --kubeconfig-switch-context
  ```

Remember to replace placeholders (like `<cluster-name>`, `<node-name>`, `<image-name>`, `<version>`, etc.) with actual values relevant to your k3d setup.
