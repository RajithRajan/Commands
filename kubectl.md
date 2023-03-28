## Apply
To apply any kubernetes manifest
`kubectl apply -f <file_name>/<folder_name>`

## Config
Configuration of the connection with the kubernetes cluster

- To get the contexts avialable in the kubeconfig  
`kubectl config get-contexts`

- To switch to docker-desktop context  
`kubectl config use-context docker-desktop `

## Create
To create a kubernetes resource  
`kubectl create ns testns`

## Delete
To delete any kubernetes resource created using manifest  
`kubectl delete -f <file_name>/<folder_name>`  
To delete a pod created by deployment  
`kubectl delete po $(kubectl get po | egrep -o "<deployment_name>[a-zA-Z0-9-]+")`

## Describe
To get additional details about a resource  
`kubectl describe po <pod_name>`

## Get PO/POD
Command to get list of images currently running in default name space  
`kubectl get pods   -o jsonpath="{.items[*].spec.containers[*].image}" | tr -ss '[[:space:]]' '\n' | sort | uniq -c`

***
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
`kubectl get secret gitlab-runner -n gitlab -o jsonpath="{.data.runner-registration-token}" | base64 --decode`

- To create a docker registry credential secret  
`kubectl create secret docker-registry gitlab-regcred --docker-server=registry.gitlab.com --docker-username=<gitlab_user> --docker-password=<gitlab_token>`

## Reference 
https://github.com/RajithRajan/kubernetes-trial
