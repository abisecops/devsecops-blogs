# Launch EC2 Instances with Custom AMIs

![Creating and Launching EC2 Instances from Custom AMIs](https://cdn.hashnode.com/res/hashnode/image/upload/v1728583510313/2def4331-75b4-4020-907e-80928b138a20.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Creating and Launching EC2 Instances from Custom AMIs

### How to Make and Start EC2 Instances Using Custom AMIs

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

*
  * Create an AMI named `devops-ec2-ami` from the existing EC2 instance `devops-ec2` for backup and scaling.
    * Launch a new EC2 instance using the created AMI named devops-ec2-new.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. We already have instance `devops-ec2`.
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728661445070/97defaf3-53b1-447c-8406-20556c8d7449.png?auto=compress,format\&format=webp)

    Instance → Actions → Create image
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728662393414/77386a13-968b-4eef-8afa-9044af94090e.png?auto=compress,format\&format=webp)

    EC2 → Instances → i-0746dd9047bc5660e → Create image
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728662510371/7febd017-180b-4de1-9657-5a215aa267a7.png?auto=compress,format\&format=webp)

    Currently creating AMI ami-01d43d011a7baa3da from instance i-0746dd9047bc5660e.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728662607872/1fcb27ff-3ac5-4328-83ab-1479abfb51ff.png?auto=compress,format\&format=webp)
5. EC2 → Instances → Launch an instance → Launch instance from AMI
6.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728662710168/da3c5a11-7e69-4870-b7db-7ea45fc9bde7.png?auto=compress,format\&format=webp)

    Name **devops-ec2-new** → Launch instance
7.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728662783346/fcf2e549-5cc2-4694-9647-94932dd1464d.png?auto=compress,format\&format=webp)

    Checkout instances now.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728663255940/641d0b3c-0510-4238-a680-ee05bda7296d.png?auto=compress,format\&format=webp)

    \#aws #cloudcomputing #happylearning
