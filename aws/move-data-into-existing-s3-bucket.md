# Move Data into Existing S3 Bucket

![Transfer Data to Existing S3 Bucket](https://cdn.hashnode.com/res/hashnode/image/upload/v1728390559162/25a1774e-5e63-4500-8cba-c660c4753539.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Transfer Data to Existing S3 Bucket

### Guide to Transferring Data into Your Current S3 Bucket

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* S3 bucket named `xfusion-cp-7889` already exists. Copy the file `/tmp/xfusion.txt` to s3 bucket `xfusion-cp-7889`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. First of all checkout the s3 bucket, to ensure this is already exists.
   * Amazon S3 → Buckets → xfusion-cp-7889
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728391085175/67f07174-d92b-4a0e-b20f-f516fa765b32.png?auto=compress,format\&format=webp)

    Verify the file on path, /tmp/xfusion.txt
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728391164336/a1f7ddb6-d18b-4ea8-afce-f80fa9e7dfdc.png?auto=compress,format\&format=webp)

    Now use command

```
aws s3 cp /tmp/xfusion.txt s3://xfusion-cp-7889/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728391296421/3546f164-b75d-4b99-bfb5-ac6f91e1ba50.png?auto=compress,format\&format=webp)

4.  Refresh and check, we can see the txt file is copied to S3 bucket.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728391332302/ca552b52-c833-4f2a-830b-fea8b30480c1.png?auto=compress,format\&format=webp)

    \#aws #cloudcomputing #happylearning
