# Increase EC2 Storage for Development

![Expanding EC2 Instance Storage for Development Needs](https://cdn.hashnode.com/res/hashnode/image/upload/v1728580174508/1b8c15f2-5651-4563-9c18-33ef80a7ff67.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Expanding EC2 Instance Storage for Development Needs

### How to Increase EC2 Instance Storage for Better Development

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* **Identify Volume:** Find the volume attached to the `xfusion-ec2` instance.
* **Expand Volume:** Increase the volume size from `8 GiB` to `12 GiB`.
* **Reflect Changes:** Ensure the root (`/`) partition within the instance reflects the expanded size from `8 GiB` to `12 GiB`.
* **SSH Access:** Use the key pair located at `/root/xfusion-keypair.pem` on the `aws-client` host to SSH into the EC2 instance.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. We already have **Instances,** `xfusion-ec2`.
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728582181471/15bd741b-e21d-43c2-91c1-7ea3b32dfdd3.png?auto=compress,format\&format=webp)

    EC2 → Volumes → vol-044ea2f7bad002711 → Modify volume
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728582335887/e1e2a470-c354-42bd-b735-5fbe0fe41d60.png?auto=compress,format\&format=webp)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728582375622/2f738ca3-95db-406f-83e0-c45a5d0d0f71.png?auto=compress,format\&format=webp)

    Modify vol-044ea2f7bad002711 → Modify
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728582410472/d72c3ab0-7a2f-4220-85eb-c8949abc1c15.png?auto=compress,format\&format=webp)

    Pem files stored at /root/xfusion-keypair.pem.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728582533285/da624c50-f126-4c20-a676-3795b3368d5a.png?auto=compress,format\&format=webp)
5. Verify the Partition Size on the EC2 Instance

```
sudo growpart /dev/xvda 1
```

6.  Resize the Filesystem

    ```
     sudo xfs_growfs /
    ```
7.  Verify the Resized Filesystem

    ```
     df -h
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728583007349/e42921c1-38c4-4154-874e-728bbd83df61.png?auto=compress,format\&format=webp)
