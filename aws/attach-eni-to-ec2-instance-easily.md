# Attach ENI to EC2 Instance Easily

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

An instance named `devops-ec2` and an elastic network interface named `devops-eni` already exists in `us-east-1` region.

* Attach the `devops-eni` network interface to the `devops-ec2` instance.
* Make sure status is `attached` before submitting the task.

Please make sure instance initialization has been completed before submitting this task.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. We can see given instance `devops-ec2` is running
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728321662353/fa3b14bf-0d8c-446e-93b5-406a2e6bac33.png?auto=compress,format\&format=webp)

    Select the instance and actions → Networking → Attach Network Interface

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728322093513/4c5b96e2-71f3-4ce7-87e6-63b7061e65de.png?auto=compress,format\&format=webp)
3. Select the given network interface
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728322178478/1ce21f83-c829-4f97-83e1-48dfd2ed4681.png?auto=compress,format\&format=webp)

    Lets attach the `devops-eni` network interface to the `devops-ec2` instance.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728322306591/ec8c10d6-3d71-4e87-ae62-5f6e042fb0f9.png?auto=compress,format\&format=webp)

    * Successfully attached network interface eni-09ed3171880f8103c to instance i-097dbe018aa801707.

\#aws

\#cloud\_computing

\#happy\_learning
