# Change EC2 Instance Type Using AWS CLI

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Change the instance type from `t2.micro` to `t2.nano` for the `nautilus-ec2` instance using `aws-cli` only.
* Ensure the `nautilus-ec2` instance is in the `running` state after the change.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Get the instance ID and Stop the `nautilus-ec2` instance:

    ```
     aws ec2 describe-instances --filters "Name=tag:Name,Values=nautilus-ec2" --query "Reservations[*].Instances[*].InstanceId" --output text
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728464688480/161c4360-08ff-4c37-b278-26d087bc38bb.png?auto=compress,format\&format=webp)

    * **i-0a089a6cf430546c4**

```
aws ec2 stop-instances --instance-ids i-0a089a6cf430546c4
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728464782138/8a7acbab-0711-4406-9c87-ea7ea2ecf41d.png?auto=compress,format\&format=webp)

2. Wait until the instance is stopped:

```
aws ec2 wait instance-stopped --instance-ids i-0a089a6cf430546c4
```

3. Change the instance type to `t2.nano`:

```
aws ec2 modify-instance-attribute --instance-id i-0a089a6cf430546c4 --instance-type "{\"Value\": \"t2.nano\"}"
```

4. Start the `nautilus-ec2` instance:

```
aws ec2 start-instances --instance-ids i-0a089a6cf430546c4
```

5.  Ensure the instance is in the `running` state:

    ```
     aws ec2 wait instance-running --instance-ids i-0a089a6cf430546c4
    ```
6. Check the instance type now.

```
aws ec2 describe-instances --instance-ids i-0a089a6cf430546c4 --query "Reservations[*].Instances[*].InstanceType" --output text
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728465207949/4cc34a84-7ce3-4691-aeed-8b8661ae3db6.png?auto=compress,format\&format=webp)

\#aws #cloudcomputing #happylearning
