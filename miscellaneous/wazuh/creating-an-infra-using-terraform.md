# Creating an infra using Terraform

As, I already mentioned Terraform introduction earlier on previous page.

#### **Prerequisites**

1. IAM User with required ec2 policy
2. aws cli
3. terraform installed



{% content-ref url="../../terraform/" %}
[terraform](../../terraform/)
{% endcontent-ref %}

Also the terraform installation part.

{% content-ref url="../../terraform/terraform-installation.md" %}
[terraform-installation.md](../../terraform/terraform-installation.md)
{% endcontent-ref %}

Here is the terraform code which can be used to create an infra.

{% embed url="https://github.com/whoami-anoint/wazu/tree/main/terraform" %}

1. Clone the repo and use it

```
git clone https://github.com/whoami-anoint/wazu/
cd terraform/infra-templates/prod-minimal/
terraform validate
terraform init
terraform plan
terraform apply -auto-approve
```

2. In case you want to destroy the infra, use the given command

```
terraform destroy -auto-approve
```

***

Let's check the validity of our terraform code:

<figure><img src="../../.gitbook/assets/image (199).png" alt="" width="348"><figcaption></figcaption></figure>

**The configuration is valid**.

_Pending issue on this challenge._

_As I am using the organizational aws labs for learning purpose, I do have no access for this policy to create ec2 from iam users (aws cli) on this terraform. But we can try with any other account as we can see our code is valid too._

<figure><img src="../../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure>





