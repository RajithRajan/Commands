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

## Secret
- To read the data from secret  
`kubectl get secret gitlab-runner -n gitlab -o jsonpath="{.data.runner-registration-token}" | base64 --decode`

- To create a docker registry credential secret  
`kubectl create secret docker-registry gitlab-regcred --docker-server=registry.gitlab.com --docker-username=<gitlab_user> --docker-password=<gitlab_token>`
