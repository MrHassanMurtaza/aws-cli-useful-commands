# :raised_hands: AWS CLI Useful Commands
Some useful AWS CLI commands to increase your productivity:

:fire:Get private ip address of instance by providing public ip address:

Note: Replace $region with your region and $publicIp with your public ip.

```
aws ec2 describe-instances --region $region --filters "Name=ip-address,Values=$publicIp" --query Reservations[*].Instances[*].PrivateIpAddress --output table  
```

:fire:Get public ip address of instance by providing private ip address:

Note: Replace $region with your region and $private_ip with your privateIp.

```
aws ec2 describe-instances --region $region --filters "Name=private-ip-address,Values=$privateIp" --query Reservations[*].Instances[*].PublicIpAddress --output table
```
:fire: Get InstanceId, Public Ip Address,Private Ip Address,Vpc Id based on Tag: 

Note: Replace $tag with your required tag name and $tag_content with your tag content.

```
aws ec2 describe-instances --region $region --filters "Name=tag:$tag,Values=$tag_content" --query 'Reservations[*].Instances[*].[Tags[?Key==`Name`].Value,InstanceId,PublicIpAddress,PrivateIpAddress,VpcId]' --output text
```

:star: Get VPC details: 

Note: Replace $vpcId with your vpc id and $region with your region.

```
aws ec2 describe-vpcs --vpc-ids $vpcId --region $region   

```

:star: Get VPC name by giving vpc id:

Note: Replace $vpcid with your vpc id and $region with your region.

```aws ec2 describe-vpcs --vpc-ids $vpcid --region $region --query Vpcs[*].Tags[*].Value ```


:unlock: List AWS Secret Manager Secrets:

Note: Replace $region with your region
```
aws secretsmanager list-secrets --region $region --query SecretList[*].Name --output table
```

:unlock: Decrypt and get specific secret:

Note: Replace $secretId with your secret.

```
aws secretsmanager get-secret-value --secret-id $secretId --region $region --query SecretString --output text
````

# License

Licensed Under GPL 2.0.
