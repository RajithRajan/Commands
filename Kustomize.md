# Kustomize
Kustomize is a way of performing few modification to the manifest on each environment, it is much simpler way of managing Kubernetes manifest for deployment into different environment. It does not have a templating feature like a Helm but it an inbuild plugin to kubectl with few feature which make modification possible per environment.    

Structure of a kustomize project
```
~/k8s
├── base
│   ├── configMap.yaml
│   ├── deployment.yaml
│   ├── kustomization.yaml
│   └── service.yaml
└── overlays
    ├── production
    │   ├── deployment.yaml
    │   └── kustomization.yaml
    └── staging
        ├── kustomization.yaml
        └── map.yaml
```
Multi-directory structure
```
.
└── code
    ├── README.md
    └── k8s
        ├── db
        │   ├── NoSql
        │   │   ├── db-depl.yaml
        │   │   ├── db-service.yaml
        │   │   └── kustomization.yaml
        │   ├── Sql
        │   │   ├── db-depl.yaml
        │   │   ├── db-service.yaml
        │   │   └── kustomization.yaml
        │   ├── db-config.yaml
        │   └── kustomization.yaml
        ├── kustomization.yaml
        ├── monitoring
        │   ├── grafana-depl.yaml
        │   ├── grafana-service.yaml
        │   └── kustomization.yaml
        └── nginx
            ├── kustomization.yaml
            ├── nginx-depl.yaml
            └── nginx-service.yaml
```
Sample Kustomization.yaml file in base dir.
```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
metadata:
  name: arbitrary

commonLabels:
  app: hello-world

resources:
- deployment.yaml
- service.yaml
- configMap.yaml
```
Deploying this kustomize project
```
kustomize build overlays/staging |\
    kubectl apply -f -

# OR

kubectl apply -k overlays/staging
```

## Common Tranformer
Common transformation are used to solve certain common usecases
- commonLabel - adds a label to all kubernetes resources
- namePrefix/Suffic - adds a common prefix-suffix to all resource names
- namespace - adds a common namespace to all resources
- commonAnnotations - adds an annotation to all resources

```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
metadata:
  name: arbitrary

namespace: dummy
nameSuffix: -stage
namePrefix: teama-
  
commonLabels:
  app: hello-world
commonAnnotations:
  app.datadog.service: hello-world

resources:
- deployment.yaml
- service.yaml
- configMap.yaml
```

## Image Transformer
Image transformer would let up modify or edit the image which a deployment would use though kustomize
```
images:
  - name: nginx
    newName: haproxy
```
where `name` is the name of image and `newName` is the image which would be replacing `nginx`

For adding a tag we can use something like this
```
images:
  - name: nginx
    newTag: haproxy
```

## Patches
Patches provide a way yo modify specific sections in a kubernetes resource

To create a patch these 3 parameters must be provided
 - Operation Type: add/remove/replace
 - Target: What resource should this patch be applied on
   - Kind
   - Version/Group
   - Name
   - Namespace
   - labeSelector
   - AnnotationSelector
 - Value: what is the value that will either be replaced or added with (add/replace operation, not needed for remove) 

### Json 6902 Patch
Sample kustomization
```
# Json 6902 Patch
patches:
  - target:
      kind: Deployment
      name: api-deployment
    patch: |-
      - op: replace
        path: /metadata/name
        value: web-deployment

# Json 6902 Patch - dictionary
patches:
  - target:
      kind: Deployment
      name: api-deployment
    patch: |-
      - op: replace
        path: /metadata/name
        value: web-deployment

# Json 6902 Patch - list
patches:
  - target:
      kind: Deployment
      name: api-deployment
    patch: |-
      - op: replace
        path: /spec/template/spec/containers/0
        value:
          name: haproxy
          image: haproxy

# Json 6902 Patch - list add - end of list
patches:
  - target:
      kind: Deployment
      name: api-deployment
    patch: |-
      - op: replace
        path: /spec/template/spec/containers/-
        value:
          name: haproxy
          image: haproxy

# separate file json 6902
patches:
  - path: patch-file.yaml
    target:
      kind: Deployment
      name: api-deployment

```

### Strategic Patch
Sample kustomization
```
# strategic merge patch
patches:
  - patch: |-
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: api-deployment
      spec:
        replicas: 5

# separate file stategic merge path
patches:
  - patch-dev.yaml

# strategic merge patch - remove dictionary
patches:
  - patch: |-
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: api-deployment
      spec:
        template:
          metadata:
            labels:
              org: null

# strategic merge patch - list replace (name should be same is existing)/add 
patches:
  - patch: |-
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: api-deployment
      spec:
        template:
          spec:
            containers:
              - name: web
                image: haproxy

# strategic merge patch - list replace (name should be same is existing)/add 
patches:
  - patch: |-
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: api-deployment
      spec:
        template:
          spec:
            containers:
              - $patch: delete
                name: database
```
