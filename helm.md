# Add
`helm repo add gitlab https://charts.gitlab.io `

# Create
`helm create --starter springwebappmysql demoapp`

# Dependency
_Will pull the dependency defined in chart.yml and store charts folder_ \
`Helm dependency update firstchart` \


# Env
_List all the environment variables_ \
`helm env`

# Get
_To retrieve manifest what was installed_ \
`Helm get manifest firstapp`

# Install
`Helm install -f myvalues.yaml myredis ./redis`

# Lint
_Identify syntax and indentation_ \
`Helm lint firstchart`

# Package
_Package to tgz file_ \
`Helm package first`


# Plugin
Plugins
`helm plugin install` \
`helm plugin list` \
`helm plugin uninstall` \

# Push
_Push the image to oci registry_ \
`Helm push firstchart-0.1.0.tgz oci://localhost:5000/helm-charts` \
`docker run -d --name oci-reggistry -p 5000:5000 registry`

# Registry login and logout
`helm registry login -u myuser` \
`helm registry logout`

# Repo 
_To create index file for repo_ \
`Helm repo index` \
_To update the index of all the added repos_ \
`helm repo update`


# Search
_To view the versions of gitlab runner run below comamnd_ \
`helm search repo -l gitlab/gitlab-runner` \
_To list all the charts in a repo_ \
`helm search repo prometheus-community`

# Template
`Helm template vault hashicorp/vault --output-dir vault-manifests/helm-manifests`

# Uninstall
`Helm uninstall <name>`

# Upgrade
`Helm upgrade <name> -set `


# Schema validation
Convert values.yaml to json (json2yaml.com)
Create schema from json values file (jsonschema.net)
has context menu
