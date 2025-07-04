# Private RDS Setup for Development Projects

![Configuring a Private RDS Instance for Application Development](https://cdn.hashnode.com/res/hashnode/image/upload/v1733063061400/284ab9ba-d9c4-4fc5-b98c-b3957e9fc3a4.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Configuring a Private RDS Instance for Application Development

### How to Configure a Private RDS Instance for Developing Applications

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* **Provision a Private RDS Instance:** Create a new private RDS instance named `datacenter-rds` using a free tier template. It must be a `db.t3.micro` type instance.
* **Engine Configuration:** Use the `MySQL` engine with version `8.0.x`.
* **Enable Storage Autoscaling:** Enable storage autoscaling and set the threshold value to `50GB`. Keep the rest of the configurations as default.
* **Instance Availability:** Ensure the instance is in the `available` state before submitting this task.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Launch a Database Instance

    RDS → Create database

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733063572283/0b2aab82-8e1a-422a-a1af-f012abfd5a20.png?auto=compress,format\&format=webp)
2. **Choose the database creation method**:
   * Select `Standard create`.
   * Select `MySQL`.
   * Under **Version**, choose `8.0.x`.
   * Select `Free tier`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733063818624/e2471a60-3e55-4a34-b0ef-60a2f3de0f8d.png?auto=compress,format\&format=webp)

3. DB instance identifier
   * Enter `datacenter-rds`.
4. Instance configuration
   * Select `db.t3.micro`.
5.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733064016232/4216b967-1291-4971-bc0e-fc665a9b52f9.png?auto=compress,format\&format=webp)

    **Storage**:

    * Enable `Storage autoscaling`.
    * Set the **Maximum storage threshold** to `50 GB`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733064143163/6e081c16-229b-4337-b232-a17980664fa2.png?auto=compress,format\&format=webp)

6. Click `Create database`
7.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733064372973/fc634689-b868-46c1-9242-29c93a3240c8.png?auto=compress,format\&format=webp)

    **Successfully created database** [**datacenter-rds**](https://us-east-1.console.aws.amazon.com/rds/home?region=us-east-1#database:id=datacenter-rds;is-cluster=false)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733064763075/3871c803-d3d1-4db1-935a-2110557f87e4.png?auto=compress,format\&format=webp)

    Boom! We've successfully completed this exercise as well.

\#aws #cloudcomputing #rds #happylearning
