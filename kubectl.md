## annotate
Annotate a resource which might trigger an action by an operator/controller
```
kubectl annotate pods my-pod icon-url=http://goo.gl/XXBTWq       # Add an annotation
kubectl annotate pods my-pod icon-                               # Remove annotation
```

## api-resources
List the api & versions currently available in the kubernetes clusters 
```
kubectl api-resources
```

## Apply
To apply any kubernetes manifest
```
kubectl apply -f <file_name>/<folder_name>
```

## auth
To check and reconcile access

This will give yes or no based on the access setup
```
kubectl auth can-i view pods
```

## autoscale
To add hpa
```
kubectl autoscale deployment foo --min=2 --max=10                # Auto scale a deployment "foo"
```

## Config
Configuration of the connection with the kubernetes cluster

- To get the contexts avialable in the kubeconfig  
```
kubectl config get-contexts
```

- To switch to docker-desktop context  
```
kubectl config use-context docker-desktop 
```

- To set default namespace to _abc_
```
kubectl config set-context --current --namespace=abc
```

## Cordon & drain
```
kubectl cordon my-node                                                # Mark my-node as unschedulable
kubectl drain my-node                                                 # Drain my-node in preparation for maintenance
kubectl uncordon my-node                                              # Mark my-node as schedulable
```

## Create
To create a kubernetes resource  
```
kubectl create ns testns
```

## Delete
To delete any kubernetes resource created using manifest  
```
kubectl delete -f <file_name>/<folder_name>
```  
To delete a pod created by deployment  
```
kubectl delete po $(kubectl get po | egrep -o "<deployment_name>[a-zA-Z0-9-]+")
```

## Describe
To get additional details about a resource  
```
kubectl describe po <pod_name>
```

## diff
Compares the current state of the cluster against the state that the cluster would be in if the manifest was applied.
```
kubectl diff -f ./my-manifest.yaml
```

## Get PO/POD
Command to get list of images currently running in default name space  
```
kubectl get pods   -o jsonpath="{.items[*].spec.containers[*].image}" | tr -ss '[[:space:]]' '\n' | sort | uniq -c
```

## label
```
kubectl label pods my-pod new-label=awesome                      # Add a Label
kubectl label pods my-pod new-label-                             # Remove a label
```

## log
to get the logs of the current or previous pod
```
kubectl logs my-pod                                 # dump pod logs (stdout)
kubectl logs -l name=myLabel                        # dump pod logs, with label name=myLabel (stdout)
kubectl logs my-pod --previous                      # dump pod logs (stdout) for a previous instantiation of a container
kubectl logs my-pod -c my-container                 # dump pod container logs (stdout, multi-container case)
kubectl logs -l name=myLabel -c my-container        # dump pod logs, with label name=myLabel (stdout)
```

## port-forward
To port forward  local port to container port, it can be executed on  pod, service, rs or deployment.
```
kubectl port-forward deployment/mongo 28015:27017
```

## rollout
```
kubectl set image deployment/frontend www=image:v2               # Rolling update "www" containers of "frontend" deployment, updating the image
kubectl rollout history deployment/frontend                      # Check the history of deployments including the revision
kubectl rollout undo deployment/frontend                         # Rollback to the previous deployment
kubectl rollout undo deployment/frontend --to-revision=2         # Rollback to a specific revision
kubectl rollout status -w deployment/frontend                    # Watch rolling update status of "frontend" deployment until completion
kubectl rollout restart deployment/frontend                      # Rolling restart of the "frontend" deployment
```
***

## top
```
kubectl top pod POD_NAME --containers               # Show metrics for a given pod and its containers
kubectl top pod POD_NAME --sort-by=cpu              # Show metrics for a given pod and sort it by 'cpu' or 'memory'
```
# Resources

<table>
    <tr>
        <th>Type</th>
        <th>Short</th>
        <th>Description</th>
        <th>CRD</th>
    </tr>
    <tr>
        <td>Configmap</td>
        <td>cm</td>
        <td>used to store configurable data of app</td>
        <td>n</td>
    </tr>  
    <tr>
        <td>Deamonset</td>
        <td></td>
        <td>used for having single pod per node</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Deployment</td>
        <td>deploy</td>
        <td>is super set of replicationset</td>
        <td>n</td>
    </tr>
    <tr>
        <td>HorizontalPodAutoscaler</td>
        <td>hpa</td>
        <td>Scales the pod based on CPU, memory or any custom matrix </td>
        <td>n</td>
    </tr> 
    <tr>
        <td>Ingress</td>
        <td>ing</td>
        <td>used to create as a proxy for multiple services, uses ALB instead of NLB</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Limits</td>
        <td></td>
        <td>to sent resource limit on all containers on ns/td>
        <td>n</td>
    </tr>
    <tr>
        <td>Namespace</td>
        <td>ns</td>
        <td>used to create virtual cluster inside cluster</td>
        <td>n</td>
    </tr>
    <tr>
        <td>PersistentVolume</td>
        <td>pv</td>
        <td>define storage which could be used by pvc</td>
        <td>n</td>
    </tr>
    <tr>
        <td>PersistentVolumeClaim</td>
        <td>pvc</td>
        <td>used to bound a pv to pod</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Pod</td>
        <td>po</td>
        <td>for creation of single pod for test not recommended</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Quota</td>
        <td></td>
        <td>to set quota for hard limits for CPU, memory, pod, cm, secret</td>
        <td>n</td>
    </tr>  
    <tr>
        <td>Replicationset</td>
        <td>rs</td>
        <td>is used to maintain replica of pod at desired level</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Secret</td>
        <td></td>
        <td>used to store sensitive data like username and password</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Service</td>
        <td>svc</td>
        <td>proxy for deployment, statefulset & pod, LB</td>
        <td>n</td>
    </tr>
    <tr>
        <td>Statefulset</td>
        <td></td>
        <td>used for stateful app in place of deployment</td>
        <td>n</td>
    </tr>
    <tr>
        <td>StorageClass</td>
        <td>sc</td>
        <td>dynamic creation of pv</td>
        <td>n</td>
    </tr>
    <tr>
        <td>VolumeSnapshot</td>
        <td>vs</td>
        <td>Snapshot of volume for backup</td>
        <td>y</td>
    </tr>
    <tr>
        <td>VolumeSnapshotClass</td>
        <td>vsclass</td>
        <td>Storage class used while creating snapshot</td>
        <td>y</td>
    </tr>
    <tr>
        <td>VolumeSnapshotContent</td>
        <td>vsc</td>
        <td>Its created from volume snapshot and would be used while creating volume</td>
        <td>y</td>
    </tr>
    <tr>
        <td>VerticalPodAutoscaler</td>
        <td>vpa</td>
        <td>To upgrade CPU & Memory based on utilization</td>
        <td>n</td>
    </tr>
</table>

## Secret
- To read the data from secret
```  
kubectl get secret gitlab-runner -n gitlab -o jsonpath="{.data.runner-registration-token}" | base64 --decode
```

- To create a docker registry credential secret  
```
kubectl create secret docker-registry gitlab-regcred --docker-server=registry.gitlab.com --docker-username=<gitlab_user> --docker-password=<gitlab_token>
```

# Issues
## Stuck namespace in terminating status
Run below command to find the resource which is still present in the namespace causing the issue.
```
kubectl api-resources --verbs=list --namespaced -o name \
  | xargs -n 1 kubectl get --show-kind --ignore-not-found -n argo-events
```

## Ingress or other resources not getting deleted
Run patch command to remove the finalizers, it would get deleted.
```
kubectl patch ing argocd-server  -p '{"metadata":{"finalizers":[]}}' --type=merge -n argocd
```

## Reference 
https://github.com/RajithRajan/kubernetes-trial  
https://kubernetes.io/docs/reference/kubectl/cheatsheet/  
https://kubernetes.io/docs/reference/kubectl/jsonpath/
