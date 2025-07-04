# Create Key Pair Using Terraform

### Tasks:&#x20;

1. Use Terraform to create an RSA key pair named `xfusion-kp`.
2. Store the private key file in `/home/bob/xfusion-kp.pem`.
3. The Terraform working directory is `/home/bob/terraform`.
4. Use only `main.tf` to define the configuration.

### Steps

{% stepper %}
{% step %}
### Create main.tf file

```hcl
resource "tls_private_key" "ssh_key" {
     algorithm = "RSA"
     rsa_bits  = 4096
   }

   resource "aws_key_pair" "xfusion_key" {
     key_name   = "xfusion-kp"
     public_key = tls_private_key.ssh_key.public_key_openssh
   }

   resource "local_file" "private_key" {
     content  = tls_private_key.ssh_key.private_key_pem
     filename = "/home/bob/xfusion-kp.pem"
   }
```

We already have provider.tf

```hcl
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.91.0"
    }
  }
}

provider "aws" {
  region                      = "us-east-1"
  skip_credentials_validation = true
  skip_requesting_account_id  = true
  s3_use_path_style = true

endpoints {
    ec2            = "http://aws:4566"
    apigateway     = "http://aws:4566"
    cloudformation = "http://aws:4566"
    cloudwatch     = "http://aws:4566"
    dynamodb       = "http://aws:4566"
    es             = "http://aws:4566"
    firehose       = "http://aws:4566"
    iam            = "http://aws:4566"
    kinesis        = "http://aws:4566"
    lambda         = "http://aws:4566"
    route53        = "http://aws:4566"
    redshift       = "http://aws:4566"
    s3             = "http://aws:4566"
    secretsmanager = "http://aws:4566"
    ses            = "http://aws:4566"
    sns            = "http://aws:4566"
    sqs            = "http://aws:4566"
    ssm            = "http://aws:4566"
    stepfunctions  = "http://aws:4566"
    sts            = "http://aws:4566"
    rds            = "http://aws:4566"
  }
}

```
{% endstep %}

{% step %}
### Initalize terraform

```bash
terraform init
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Terraform apply with auto approve flag

```
terraform apply -auto-approve
```

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Check out the pem file

```
ls -l /home/bob/xfusion-kp.pem
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Give permission to pem file

```
chmod 400 /home/bob/xfusion-kp.pem
```
{% endstep %}
{% endstepper %}
