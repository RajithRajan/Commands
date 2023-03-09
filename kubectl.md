## Apply
To apply any kubernetes manifest
`kubectl apply -f <file_name>/<folder_name>`

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
