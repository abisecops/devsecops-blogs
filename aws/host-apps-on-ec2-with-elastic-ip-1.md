# Host Apps on EC2 with Elastic IP

![Setting Up an EC2 Instance with an Elastic IP for Application Hosting](https://cdn.hashnode.com/res/hashnode/image/upload/v1728578728820/ff108ed5-8a26-4009-a7c6-dffa993fe17b.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Setting Up an EC2 Instance with an Elastic IP for Application Hosting

### How to Launch an EC2 Instance and Use an Elastic IP for Hosting Applications

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create an EC2 instance named `nautilus-ec2` using a Linux AMI like Ubuntu.
* Set the instance type to `t2.micro`.
* Associate an `Elastic IP` address with the instance and name it `nautilus-eip`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. EC2 → Instances → Launch an instance → Launch instance
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728579110075/a8c4c1f9-87ef-490a-a98b-414617811449.png?auto=compress,format\&format=webp)

    EC2 → Elastic IP addresses → Allocate Elastic IP address
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728579443358/2500fd99-92ab-4f78-a149-2fc97154a588.png?auto=compress,format\&format=webp)

    **Elastic IP address allocated successfully.**
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728579564231/483b6aab-d780-4d36-9484-104cf56e1d9a.png?auto=compress,format\&format=webp)

    EC2 → Elastic IP addresses → 54.204.92.83 Associate Elastic IP address

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728579660795/5af90c6c-2178-4616-858a-3a286c6974f3.png?auto=compress,format\&format=webp)
5.  Instance summary for i-0a4137871948e099d (nautilus-ec2)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728579766600/dd6efa48-f10f-4bcf-a483-ee666c4f22a2.png?auto=compress,format\&format=webp)

    \#aws #cloudcomputing #happylearning
