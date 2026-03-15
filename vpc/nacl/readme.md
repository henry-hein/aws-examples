## Get VPC ID
aws ec2 describe-vpcs \
--filters "Name=tag:Name, Value=project-vpc-vpc" \
--query "Vpcs[].VpcId" \
--output text

## Create NACL
aws ec2 create-network-acl --vpc-id vpc-069e48814aad31fee

## Get AMI for Amazon Linux 2
aws ssm get-parameters \
  --names /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 \
  --region ap-southeast-1 \
  --query "Parameters[0].Value" \
  --output text