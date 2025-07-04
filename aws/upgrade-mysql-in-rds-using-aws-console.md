# Upgrade MySQL in RDS Using AWS Console

![Upgrade RDS MySQL Engine Version via AWS Console](https://cdn.hashnode.com/res/hashnode/image/upload/v1728454711333/5ca77450-f962-4490-80e1-aa830a09f869.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Upgrade RDS MySQL Engine Version via AWS Console

### Step-by-Step Guide to Upgrading RDS MySQL Version in the AWS Console

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Identify the current MySQL version running on the RDS instance `devops-rds` as `8.0.32`.
* Plan to upgrade the RDS MySQL engine from version `8.0.32` to `8.0.36`.
* Ensure the changes take effect immediately.
* Confirm that the RDS instance remains in the `Available` state after the upgrade.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. RDS → Databases
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728455268950/a4e5d5a2-fb6e-4741-81c7-fd742fc838aa.png?auto=compress,format\&format=webp)

    RDS → Databases → Modify DB instance: devops-rds
3.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728455826200/e79a7779-0047-49d9-81e3-abad70a78c46.png?auto=compress,format\&format=webp)

    Schedule modifications → Apply immediately → Modify DB instance
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728455890995/a21e0e6f-287d-4ca1-b6a3-837b248a2830.png?auto=compress,format\&format=webp)

    Successfully modified **devops-rds**.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728455970635/1d87e58a-b926-417d-9d01-e3593f513f6e.png?auto=compress,format\&format=webp)

    \#aws #cloudcomputing #happylearning
