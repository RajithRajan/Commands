## Getting started
Get going with the gcloud CLI.
```
gcloud init                                       # Initialize, authorize, and configure the gcloud CLI.
gcloud version                                    # Display version and installed components.
gcloud components install                         # Install specific components.
gcloud components install gke-gcloud-auth-plugin  ## To connect to gke using kubectl on k8s v1.26+
gcloud components update                          # Update your gcloud CLI to the latest version.
gcloud config set project                         # Set a default Google Cloud project to work on.
gcloud config set project <PROJECT_ID>
gcloud info                                       # Display current gcloud CLI environment details.
```

## Personalization
Make the gcloud CLI your own; personalize your configuration with properties.
```
gcloud config set                         # Define a property (like compute/zone) for the current configuration.
gcloud config get                         # Fetch the value of a gcloud CLI property.
gcloud config list                        # Display all the properties for the current configuration.
gcloud config configurations create       # Create a new named configuration.
gcloud config configurations list         # Display a list of all available configurations.
gcloud config configurations activate     # Switch to an existing named configuration.
```

## Authorization and Credentials
Grant and revoke authorization to the gcloud CLI and manage credentials.
```
gcloud auth login                         # Authorize Google Cloud access for the gcloud CLI with Google Cloud user credentials and set the current account as active.
gcloud auth login --cred-file=<path_to_keyfile>
gcloud auth activate-service-account      # Authorize Google Cloud access similar to gcloud auth login but with service account credentials.
gcloud auth activate-service-account --key-file=<path_to_keyfile>
gcloud auth application-default           # Manage your Application Default Credentials (ADC) for Cloud Client Libraries.
gcloud auth list                          # List all credentialed accounts.
gcloud auth print-access-token            # Display the current account's access token.
gcloud auth revoke                        # Remove access credentials for an account.
```

===========================================================================================================
##  App Engine (Serverless)

Build highly scalable applications on a fully managed serverless platform
```
gcloud app deploy                                   # Deploy your app's code and configuration to the App Engine server.
gcloud app versions list                            # List all versions of all services deployed to the App Engine server.
gcloud app browse                                   # Open the current app in a web browser.
gcloud app create                                   # Create an App Engine app within your current project.
gcloud app logs read                                # Display the latest App Engine app logs.
```

## Compute Engine (Virtual Machines)

Create, run, and manage VMs on Google Cloud infrastructure.
```
gcloud compute zones list                           # List Compute Engine zones.
gcloud compute instances create                     # Create a VM instance.
gcloud compute instances describe                   # Display a VM instance's details.
gcloud compute instances list                       # List all VM instances in a project.
gcloud compute disks snapshot                       # Create snapshot of persistent disks.
gcloud compute snapshots describe                   # Display a snapshot's details.
gcloud compute snapshots delete                     # Delete a snapshot.
gcloud compute ssh                                  # Connect to a VM instance by using SSH.
```
### ssh
SSH into an instance
```
gcloud compute ssh --project=<PROJECT_ID> --zone=<ZONE> <VM_NAME>
```

### Start up script
Get logs
```
sudo journalctl -u google-startup-scripts.service
```
Rerun the start up script
```
sudo google_metadata_script_runner --script-type startup
```


## Container & Google Kubernetes Engine (GKE)

Manage containerized applications on Kubernetes.
```
gcloud auth configure-docker                        # Register the gcloud CLI as a Docker credential helper.
gcloud container clusters create                    # Create a cluster to run GKE containers.
gcloud container clusters list                      # List clusters for running GKE containers.
gcloud container clusters get-credentials           # Update kubeconfig to get kubectl to use a GKE cluster.
gcloud container clusters get-credentials <cluster_name> --region <region> --project <project_name>
gcloud container images list-tags                   # List tag and digest metadata for a container image.
```
List the fleet memberships for the project
```
gcloud container fleet memberships list --project <project_id>
```
Describe that Anthos Mesh 
```
gcloud container fleet mesh describe --project <project_id>
```
Describe the status of Anthos control plane
```
kubectl describe controlplanerevision asm-managed -n istio-system
```

## IAM

Configuring Identity and Access Management (IAM) preferences and service accounts.
```
gcloud iam list-grantable-roles                     # List IAM grantable roles for a resource.
gcloud iam roles create                             # Create a custom role for a project or org.
gcloud iam service-accounts create                  # Create a service account for a project.
gcloud iam service-accounts add-iam-policy-binding  # Add an IAM policy binding to a service account.
gcloud iam service-accounts set-iam-policy-binding  # Replace existing IAM policy binding.
gcloud iam service-accounts keys list               # List a service account's keys.
```

## Projects

Manage project access policies.
```
gcloud projects describe                  # Display metadata for a project (including its ID).
gcloud projects add-iam-policy-binding    # Add an IAM policy binding to a specified project.
```


## Pub-Sub
Publishing message to a topic
```
gcloud pubsub subscriptions pull <topic_name> --auto-ack
```
Reading message from the topic using a subscription
```
gcloud pubsub subscriptions pull <subscription_name> --auto-ack
```

## Storage (GCS)
List buckets
```
gcloud storage ls
```
List bucket objects
```
gcloud storage ls gs://<bucket_name>/
```
Uploading a file
```
gcloud storage cp <object_location> gs://<bucket_name>
```
Deleting a file
```
gcloud storage rm gs://<bucket_name>/<path_of_object>
```


===========================================================================================================

## Global flags

Some flags are available throughout the gcloud CLI experience, like:
```
--help                                              # For when in doubt; display detailed help for a command.
--project                                           # If using a project other than the current one.
--quiet                                             # Disabling interactive prompting (and applying default values for inputs).
--verbosity                                         # Can set verbosity levels at debug, info, warning, error, critical, and none.
--version                                           # Display gcloud version information.
--format                                            # Set output format as config, csv, default, diff, disable, flattened, get, json, list, multi, none, object, table, text, value, or yaml.
```

===========================================================================================================
## Reference
https://cloud.google.com/sdk/docs/cheatsheet
https://cloud.google.com/sdk/gcloud/reference
