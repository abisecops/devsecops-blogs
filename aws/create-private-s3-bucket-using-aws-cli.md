# Create Private S3 Bucket Using AWS CLI

![Create Private S3 Bucket via AWS CLI](https://cdn.hashnode.com/res/hashnode/image/upload/v1728461697812/f9d84bab-d932-4124-a83f-5d5ad649685d.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### How to Use AWS CLI for Creating Private S3 Buckets

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

Create a S3 bucket through `aws-cli` with the following details:

* The name of the S3 bucket must be `xfusion-s3-29022`.
* The S3 bucket must block all `public` access, i.e., it must be a `private` bucket.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Create the S3 bucket named `xfusion-s3-29022` in the `us-east-1` region:

    ```
     aws s3api create-bucket --bucket xfusion-s3-29022 --region us-east-1
    ```
2.  Block all public access to the bucket to make it private:

    ```
     aws s3api put-public-access-block \
     --bucket xfusion-s3-29022 \
     --public-access-block-configuration BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true
    ```
3.  AWS CLI

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728462728989/8523c670-b0e9-4c3c-ad9e-6fdba69abf06.png?auto=compress,format\&format=webp)
4.  Verify now.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728462829246/20137f7d-c08a-4dd3-b321-f51559373c1e.png?auto=compress,format\&format=webp)

    \#aws #cloudcomputing #happylearning
