# Migrate S3 Buckets with AWS CLI

![Data Migration Between S3 Buckets Using AWS CLI](https://cdn.hashnode.com/res/hashnode/image/upload/v1733038478969/79ec0bed-2af1-4684-a4a3-16e83d2d1a29.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Data Migration Between S3 Buckets Using AWS CLI

### How to Transfer Data Between S3 Buckets with AWS CLI

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a new private S3 bucket named `xfusion-sync-9739`.
* Migrate all data from the existing `xfusion-s3-29917` bucket to the new `xfusion-sync-9739` bucket.
* Ensure data consistency between both buckets.
* Use the AWS CLI for creating the bucket and migrating the data.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Ensure that we have aws cli configured with credentials.

    ```
     aws configure
    ```

    ```
     ~ on ☁️  (us-east-1) ➜  aws configure
     AWS Access Key ID [****************KG6C]: 
     AWS Secret Access Key [****************LyeE]: 
     Default region name [us-east-1]: 
     Default output format [None]: 

     ~ on ☁️  (us-east-1) ➜
    ```
2.  Time to create a new private S3 bucket named `xfusion-sync-9739`.

    ```
     aws s3api create-bucket --bucket xfusion-sync-9739 --region us-east-1
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733039034828/7b425b7f-8fff-4c21-840b-1a69993a19e0.png?auto=compress,format\&format=webp)
3.  Verify the bucket is created or not.

    ```
     aws s3 ls
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733039144576/6435a183-3923-45a5-b979-57017410756f.png?auto=compress,format\&format=webp)
4.  Migrate Data from the Source Bucket.

    ```
     aws s3 sync s3://xfusion-s3-29917 s3://xfusion-sync-9739
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733039313825/be4860f6-533e-4036-a822-edb77c71e2cc.png?auto=compress,format\&format=webp)
5.  Verify Data Consistency

    Compare the total number of objects in both buckets to confirm the data migration was successful.

    *   For the source bucket:

        ```
          aws s3 ls s3://xfusion-s3-29917 --recursive --summarize | grep "Total Objects"
        ```

        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733039487305/35b22b9a-1836-4502-928b-9fa46c4ade9f.png?auto=compress,format\&format=webp)
    *   For the destination bucket:

        ```
          aws s3 ls s3://xfusion-s3-29917 --recursive --summarize | grep "Total Objects"
        ```

        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733039522957/2e8f2fee-bcfc-46c1-838f-43075b0e1a54.png?auto=compress,format\&format=webp)

        Boom! we have successfully solved the exercise.

        \#happylearning #cloud #aws #S3 #awscli
