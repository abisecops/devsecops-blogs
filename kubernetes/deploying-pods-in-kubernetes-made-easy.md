---
cover: ../.gitbook/assets/lab1.png
coverY: 0
---

# Deploying Pods in Kubernetes Made Easy

![Deploy Pods in Kubernetes Cluster](https://cdn.hashnode.com/res/hashnode/image/upload/v1728836337560/fc1c60c7-022a-4f5b-9c9a-e944ba15f8c2.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Deploy Pods in Kubernetes Cluster

### How to Deploy Pods in a Kubernetes Cluster

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a pod named `pod-httpd` using the `httpd` image with the `latest` tag. Ensure to specify the tag as `httpd:latest`.
* Set the `app` label to `httpd_app`, and name the container as `httpd-container`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. Create a pod called `pod-httpd` using the `httpd` image with the `latest` tag, ensuring the tag is specified as `httpd:latest`.
   * Create a yaml file

```
cat > pod-httpd.yaml <<EOF
apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
  - name: httpd-container
    image: httpd:latest
EOF
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728838613883/67114734-decf-4ebd-8588-1c30a62e7569.png?auto=compress,format\&format=webp)

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
  - name: httpd-container
    image: httpd:latest
```

2.  You can apply this configuration with this command.

    ```
     kubectl apply -f pod-httpd.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728838777934/41b6845c-6e74-40d9-98dc-9dd591b18ea6.png?auto=compress,format\&format=webp)

    3.  To ensure or check the create pods.

        ```
         kubectl get pods
        ```

        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728838889673/30a405a8-faf0-4295-ace5-9026fc0fe17f.png?auto=compress,format\&format=webp)

        \#k8s #pods #devops
