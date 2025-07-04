# AWS CLI: Delete EC2 Instance Guide

![Delete EC2 Instance via AWS CLI](https://cdn.hashnode.com/res/hashnode/image/upload/v1728465483881/bd98f6f4-dd54-44c5-b680-b56f5e7b8fdb.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### AWS CLI Commands for Deleting EC2 Instances

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Using AWS CLI, delete an EC2 instance named `nautilus-ec2` present in the `us-east-1` region.
* Before submitting your task, make sure the instance is in the `terminated` state.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Get the instance ID and Stop the `nautilus-ec2` instance.

    ```
     aws ec2 describe-instances --filters "Name=tag:Name,Values=nautilus-ec2" --query "Reservations[*].Instances[*].InstanceId" --output text
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728465737660/1bfebb72-46ea-4525-bae3-1f64fcb9d882.png?auto=compress,format\&format=webp)

    * **i-04575360679a33d0b**
2.  Delete the EC2 Instance

    ```
     aws ec2 terminate-instances --instance-ids i-04575360679a33d0b --region us-east-1
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728465874908/5aef0903-a843-4f60-9624-1b2e29040155.png?auto=compress,format\&format=webp)
3.  Verify the instance state is on terminated state

    ```
     aws ec2 describe-instances --instance-ids i-04575360679a33d0b --region us-east-1 --query "Reservations[*].Instances[*].State.Name" --output text
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728465957596/35a33db4-bc38-4b14-be87-556829628aac.png?auto=compress,format\&format=webp)

    \#aws #cloudcomputing #happylearning
