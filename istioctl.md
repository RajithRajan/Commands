# istioctl
This command line utility is used for install, debug, diagnose & uninstall istio mesh.

## install
install default version of istio
```
istioctl install
```
Install istio with demo profile, with full tracing enabled
```
istioctl install --set profile=demo
```
Install using a configuration file
```
istioctl install -f \path_to_file.yaml
```

## Manifest
Generate kubernetes manifest for the configuration file passed
```
istioctl manifeat generate -f /path_to_file.yaml > manifest_file.yaml
```

## profile
Get the profile dump
```
istioctl profile dump <profile_name>  > /path_to_file.yaml   # default, demo, minimal
```

## uninstall
```
istioctl uninstall --purge
```
