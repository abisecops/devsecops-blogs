# RDS Instance: Allow Public Access

![Enabling Public Access to an RDS Instance](https://cdn.hashnode.com/res/hashnode/image/upload/v1733065158531/e2dff6d0-d235-4d66-a0eb-8e3cee6f8ea8.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Enabling Public Access to an RDS Instance

### How to Allow Public Access to an RDS Instance

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

1. **Verify Existing RDS Instance:** Confirm that the RDS instance `devops-rds` is already created.
2. **Configure Public Access:** Set the RDS instance `devops-rds` to be publicly accessible.
3. **Check Default Port:** Ensure the RDS instance is accessible on the default port `3306`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Navigate to the **RDS** service and search for instance.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733065618697/3f90396c-112e-49b2-8013-f005ee466d91.png?auto=compress,format\&format=webp)
2. RDS → Databases → devops-rds → Modify
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733065756118/5905a011-eba3-45e3-adb9-b34ecd4823da.png?auto=compress,format\&format=webp)

    Connectivity → Publicly Accessible
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733065916730/19a6c6dd-9d20-45c4-be3e-22a2b0480051.png?auto=compress,format\&format=webp)

    Click `Continue`.
5.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733065998514/6f7d8ba2-7bc8-4f9e-8941-ffddb7ec7e6b.png?auto=compress,format\&format=webp)

    Select `Apply immediately`
6.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733066048517/adc6efd4-3e0f-43f1-bd58-c5162514788f.png?auto=compress,format\&format=webp)

    Edit the inbound rules to allow traffic on **port 3306** by opening it to `0.0.0.0/0`.
7.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733066319889/e97ed8c9-29e2-4cc7-af91-5b605288f77d.png?auto=compress,format\&format=webp)

    To get username

```
aws rds describe-db-instances --db-instance-identifier devops-rds --query "DBInstances[0].MasterUsername"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733066955140/d5b7c44b-aa35-427b-90a3-4b0be7e3338f.png?auto=compress,format\&format=webp)

8. Now let’s connect with endpoints.
9.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733067357714/8a0bb465-e779-4199-bc62-842a65f533bc.png?auto=compress,format\&format=webp)

    Let’s try to connect the mysql from outside with the username, endpoints and password which we already created on **devops-rds**.
10.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733067475727/fda2ca1b-a874-4911-86f4-a446476eb582.png?auto=compress,format\&format=webp)

    Boom!! We are able to access the mysql from our localhost too.

\#cloud #aws #cloudcomputing #rds #mysql #happlearning
