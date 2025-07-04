# EC2 Instance Setup and Cloud Watch Alarm

![Setting Up an EC2 Instance and Cloud Watch Alarm](https://cdn.hashnode.com/res/hashnode/image/upload/v1733028591122/35ad62e0-63de-4673-8327-809e1fcb902a.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Setting Up an EC2 Instance and Cloud Watch Alarm

### How to Configure EC2 Instances and Cloud Watch Alarms

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

1. **Launch EC2 Instance:** Set up an EC2 instance named `datacenter-ec2` using a suitable Ubuntu AMI.
2. **Create CloudWatch Alarm:** Set up a CloudWatch alarm named `datacenter-alarm` with these details:
   * Statistic: Average
   * Metric: CPU Utilization
   * Threshold: >= 90% for one consecutive 5-minute period.
   * Alarm Actions: Notify `datacenter-sns-topic`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Launch instance

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733029108291/aaf185d6-4bac-483b-8cfd-5c71e51facc3.png?auto=compress,format\&format=webp)
2.  Create a default VPC

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733034926760/2ab71b9e-3d4a-45b2-9f14-8795a171694c.png?auto=compress,format\&format=webp)

    VPC → Your VPCs → Create default VPC

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035028531/7d1ae919-f287-4f5d-8a32-fad5bb98172c.png?auto=compress,format\&format=webp)
3. You successfully created **vpc-0e139ab7aa6d8c882**.
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035063863/7e614bec-7392-4e48-afcc-9b240608cb4c.png?auto=compress,format\&format=webp)

    Now, time to launch the instance
5.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035158488/be3194cf-f023-4f6e-b671-abe46e532eea.png?auto=compress,format\&format=webp)

    Instance is running now.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035346743/0d337f9b-75e0-4dc6-92f7-7e0c29290f26.png?auto=compress,format\&format=webp)
6.  Verify SNS Topic

    **Amazon → SNS → Topics**

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733036281227/c6398ebe-3b62-448b-98f8-7d5e0db0e624.png?auto=compress,format\&format=webp)
7. Select the instance → Actions → Monitor and troubleshoot → Manage CloudWatch Alarms
8.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035408414/91030106-8442-4406-a3f7-b2f4c4637e96.png?auto=compress,format\&format=webp)

    Name the alarm and mention alarm notification, **datacenter-sns-topic**.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733036468460/8e88b417-af59-420c-af80-8107355d2606.png?auto=compress,format\&format=webp)
9. Create now.
10.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035835028/2ad89901-0f4e-4d02-8718-9485052d7a83.png?auto=compress,format\&format=webp)

    Created CloudWatch alarm: datacenter-alarm
11.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733035876394/d1a6d986-258c-4fc5-9ec8-551eeb9164c7.png?auto=compress,format\&format=webp)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733036791456/e5bc0b87-0ac4-4f25-8d06-04d4c9076e6e.png?auto=compress,format\&format=webp)

    Boom! We have set up an EC2 instance and configured a CloudWatch alarm.

    \#happylearning #aws #cloud
