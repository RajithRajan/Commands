## Configure
Configuring the AWS credential to be used for run the CLI 
```
aws configure set aws_access_key_id <AWS_ACCESS_KEY_ID>
aws configure set aws_secret_access_key <AWS_SECRET_ACCESS_KEY>
```

## EC2
_Describe an EC2 instance which has a specific tag_  
```
aws ec2 describe-instances --query "Reservations[*].Instances[*].InstanceId" --filters Name=tag:type,Values=EC2-Win --output text
```

## EKS
Update the Kube config to enable connection to kubernetes api server using kubectl  
```
aws eks --region <aws-region> update-kubeconfig --name <cluster_name>
```

## EMR
To list the virtual cluster id for the EMR container along with namespace which are in terminated state.
```
aws emr-containers list-virtual-clusters --query "virtualClusters[*].[id , containerProvider.info.eksInfo.namespace]" --states TERMINATED --output text
```

## S3
_Sync S3 content from the local directory_  
```
aws s3 sync . s3://<s3-uri>
```
_Sort content of a S3 bucket in order of last modified by data
```
aws s3 ls s3://<bucket-path> --query 'sort_by(Contents, &LastModified)[0].Key'
```
## s3api
_Get the last modified version for a object
```
aws s3api list-object-versions --bucket <bucket-name> --prefix=abc.txt --query 'sort_by(Versions, &LastModified)[-1].VersionId' --output text
```
_Delete the S3 object version
```
aws s3api delete-object --bucket <bucket-name> --key <object-name> --version-id <ver_ID>
```

## SSM
_Fetching the parameter store variable having secretstring data_  
```
aws ssm get-parameter --name <parameter-name> --with-decryption | jq '.Parameter.Value' -r
```

_Port forward the RDP(3389) port to a local port 54321 (SSM plugin needed and EC2 instance should have SSM role)_  
```
aws ssm start-session --target $ec2_id --document-name AWS-StartPortForwardingSession --parameters "localPortNumber=54321,portNumber=3389" --region ap-south-1
```

## STS
_Get information regarding the user which would be used by CLI_
```
aws sts get-caller-identity
```
