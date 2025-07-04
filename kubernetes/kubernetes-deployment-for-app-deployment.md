# Kubernetes Deployment for App Deployment

![Deploy Applications with Kubernetes Deployments](https://cdn.hashnode.com/res/hashnode/image/upload/v1728839949052/ba59f0d9-a6f7-44a5-8c26-f3bab7c8278d.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Deploy Applications with Kubernetes Deployments

### How to Deploy Apps Using Kubernetes Deployments

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a deployment named `httpd`.
* Deploy the application `httpd`.
* Use the image `httpd:latest` (make sure to specify the tag).

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Make yaml file or you can try EOF. Personally I like using EOF. (Alternatively, you can try **vim**/ **nano** anything.

    ```
     cat > httpd-deployment.yaml <<EOF
     apiVersion: apps/v1
     kind: Deployment
     metadata:
       name: httpd
     spec:
       replicas: 1
       selector:
         matchLabels:
           app: httpd
       template:
         metadata:
           labels:
             app: httpd
         spec:
           containers:
           - name: httpd-container
             image: httpd:latest
     EOF
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728840506872/a3a1be00-ab9a-4b35-a62f-dd68b5ab0ba5.png?auto=compress,format\&format=webp)
2.  Now apply the yaml file

    ```
     kubectl apply -f httpd-deployment.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728840626665/d1d30d7b-17fc-4e6a-9cbe-badc25775d87.png?auto=compress,format\&format=webp)
3.  Apply the deployment with the following command:

    ```
     kubectl apply -f httpd-deployment.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728840703204/3372592f-25d2-48d5-a576-7f53005c7a6e.png?auto=compress,format\&format=webp)
4.  To check if the deployment is created, run:

    ```
     kubectl get deployments
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728840803790/77395b56-0f82-4912-aa03-8d26a09eb300.png?auto=compress,format\&format=webp)
5. To make sure to specify the tag (latest)
   * As we already have deployment named `httpd`.

```
    kubectl describe deployment httpd
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728841033204/32b70700-1df2-4256-8d28-5b80b93b408d.png?auto=compress,format\&format=webp)

\#k8s #devops #deployments #happylearning
