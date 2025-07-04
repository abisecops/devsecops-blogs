# EC2 instance using AWS CLI

Task :  EC2 instance using AWS CLI under default VPC:&#x20;

1\) The name of the instance must be `devops-ec2`.

2\) You can use the `ami-0cd59ecaf368e5ccf` AMI to launch this instance.

3\) The Instance type must be `t2.micro`.

4\) Create a new RSA key pair named `devops-kp`.

5\) Attach the default (available by default) security group.



First you need to install aws cli and IAM role for this task.&#x20;

```bash
# Create a new RSA key pair named devops-kp and save it to a file
aws ec2 create-key-pair --key-name devops-kp --query 'KeyMaterial' --output text > devops-kp.pem

# Launch the EC2 instance using the created key pair
aws ec2 run-instances \
    --image-id ami-0cd59ecaf368e5ccf \
    --instance-type t2.micro \
    --key-name devops-kp \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=devops-ec2}]' \
    --security-groups default

# Verify the status of the EC2 instance
aws ec2 describe-instances --filters "Name=tag:Name,Values=devops-ec2" --query "Reservations[*].Instances[*].[InstanceId,State.Name]"

```
