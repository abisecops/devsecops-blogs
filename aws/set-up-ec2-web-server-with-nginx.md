# Set Up EC2 Web Server with Nginx

![Configuring an EC2 Instance as a Web Server with Nginx](https://cdn.hashnode.com/res/hashnode/image/upload/v1733037202539/99811ea5-db99-4ada-b1a0-8df05961b7bd.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Configuring an EC2 Instance as a Web Server with Nginx

### Hosting Websites on EC2: Configure Your Web Server with Nginx

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Set up a new EC2 instance for the Nautilus project.
* **Instance Name:** Name the EC2 instance `devops-ec2`.
* **AMI:** Use any available Ubuntu AMI to create the instance.
* **User Data Script:** Configure the instance to run a script at launch to:
  * Install the Nginx package.
  * Start the Nginx service.

**Security Group:** Configure the instance to allow HTTP traffic on port `80` from the internet.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. Launch instance with name **devops-ec2.**
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733037562996/31aa925d-b851-4332-895b-438d19939a1b.png?auto=compress,format\&format=webp)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733037694239/37cbb2be-5f6b-4822-bc00-7e994742fb86.png?auto=compress,format\&format=webp)

    Paste the given userdata in advance section.

```
#!/bin/bash
sudo apt-get update -y
sudo apt-get install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

3. Instance is created
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733038037005/02c0debf-ba3e-48f6-a737-07a3113985d2.png?auto=compress,format\&format=webp)

    Now, let’s verify whether the IP has nginx installed or not.
5.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733038201675/ad73eb99-1a99-4f83-91a0-29a4ed61d639.png?auto=compress,format\&format=webp)

    Boom! we have successfully completed the tasks.

    \#happylearning #userdata #aws #cloudcomputing
