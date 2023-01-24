## EC2
_Describe an EC2 instance which has a specific tag_
`aws ec2 describe-instances --query "Reservations[*].Instances[*].InstanceId" --filters Name=tag:type,Values=EC2-Win --output text`

## EKS
Update the Kube config to enable connection to kubernetes api server using kubectl
`aws eks --region <aws-region> update-kubeconfig --name <cluster_name>`

## S3
_Sync S3 content from the local directory_
`aws s3 sync . s3://<s3-uri>`

## SSM
_Fetching the parameter store variable having secretstring data_
`aws ssm get-parameter --name <parameter-name> --with-decryption | jq '.Parameter.Value' -r`

_Port forward the RDP(3389) port to a local port 54321 (SSM plugin needed and EC2 instance should have SSM role)_
aws ssm start-session --target $ec2_id --document-name AWS-StartPortForwardingSession --parameters "localPortNumber=54321,portNumber=3389" --region ap-south-1 
