# Kubernetes Rolling Updates Guide

![Execute Rolling Updates in Kubernetes](https://cdn.hashnode.com/res/hashnode/image/upload/v1728899012860/0163ab98-11c0-4bbe-89a3-29803e762543.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Execute Rolling Updates in Kubernetes

### Step-by-Step Guide to Rolling Updates in Kubernetes

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Execute a rolling update for the application using the `nginx:1.17` image.
* Ensure the deployment is named `nginx-deployment`.
* Verify that all pods are operational after the update.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Get the description of deployment named `nginx-deployement`

    ```
     kubectl describe deployment nginx-deployment
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728899602075/47b772d1-adb1-4d8e-92f0-3dd8f4e523a7.png?auto=compress,format\&format=webp)

    We can see there is image: `nginx:1.16`
2.  Lets update nginx container

    ```
     kubectl set image deployment/nginx-deployment nginx-container=nginx:1.17
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728899762673/6f5fab4f-60e3-40cf-90a5-d9e964df445f.png?auto=compress,format\&format=webp)
3.  Check the Rollout Status.

    ```
     kubectl rollout status deployment/nginx-deployment
    ```
4.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728899934460/231dbf92-9947-4703-9d2c-0d1d8250af94.png?auto=compress,format\&format=webp)
5.  Again check the update

    ```
     kubectl describe deployment nginx-deployment
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728899833776/62e95dc1-0350-41e3-aac5-85915db1a501.png?auto=compress,format\&format=webp)

    We can see we have image, `nginx:1.17` now.
6. Out of the box.
   * Check our nginx is running on web or not.
   *

       ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728900237024/9f5c6802-aab0-4665-ba94-d565c025be21.png?auto=compress,format\&format=webp)

       Not check the nginx version `making 404 error` :p

       ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728900262970/3f5cbc3b-310c-40e1-a350-63200401533b.png?auto=compress,format\&format=webp)

       \#nginx #k8s #kubernetes #happylearning
