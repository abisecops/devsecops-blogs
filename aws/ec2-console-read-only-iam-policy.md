# EC2 Console Read-Only IAM Policy

![Create Read-Only IAM Policy for EC2 Console Access](https://cdn.hashnode.com/res/hashnode/image/upload/v1728369874305/0bf7192a-9682-4105-9d9b-13d29c75bb54.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Create Read-Only IAM Policy for EC2 Console Access

### How to Set Up an IAM Policy for Read-Only Access to the EC2 Console

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create an IAM policy named `iampolicy_rose` in `us-east-1` region, it must allow read-only access to the EC2 console, i.e this policy must allow users to view all instances, AMIs, and snapshots in the Amazon EC2 console.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. Select Policies under IAM.
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728370128999/a01fdcb5-aea7-48ba-9f77-25500f104e10.png?auto=compress,format\&format=webp)

    IAM → Policies → Create Policy
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728370204389/b105964a-cb77-421e-b62d-a49c127eb0ae.png?auto=compress,format\&format=webp)

    Specify permissions → **Select a service**
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728370313979/0b79decd-4b0e-4c07-aedf-b974c1b33ea2.png?auto=compress,format\&format=webp)

    Read-only access to the EC2 console
5.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728370567943/e0814db0-10ee-421d-af85-2266593b01fe.png?auto=compress,format\&format=webp)

    Name Policy and create
6.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728370679569/0b3bfd2f-d9f2-450f-9ecd-0a4ba91d6796.png?auto=compress,format\&format=webp)

    **Policy iampolicy\_rose created.**

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728370748785/f2836554-85f4-4a98-8789-ccfd337c8587.png?auto=compress,format\&format=webp)
