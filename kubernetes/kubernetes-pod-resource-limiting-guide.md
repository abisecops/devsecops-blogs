# Kubernetes Pod Resource Limiting Guide

![Set Resource Limits in Kubernetes Pods](https://cdn.hashnode.com/res/hashnode/image/upload/v1728896872813/1f395ec8-ce53-471b-b629-6badce23620e.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Set Resource Limits in Kubernetes Pods

### How to Define Resource Restrictions for Kubernetes Pods

#### Steps <a href="#heading-steps" id="heading-steps"></a>

* Create a pod named `httpd-pod` with a container named `httpd-container`.
* Use the `httpd` image with the `latest` tag (`httpd:latest`).
* Set resource requests:
  * Memory: `15Mi`
  * CPU: `100m`
* Set resource limits:
  * Memory: `20Mi`
  * CPU: `100m`

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

1.  Create a manifest yaml file, `httpd-pod.yaml`

    ```
     apiVersion: v1
     kind: Pod
     metadata:
       name: httpd-pod
     spec:
       containers:
       - name: httpd-container
         image: httpd:latest
         resources:
           requests:
             memory: "15Mi"
             cpu: "100m"
           limits:
             memory: "20Mi"
             cpu: "100m"
    ```

    As I prefer **EOF**,

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728897681682/4e7e5444-0be3-41cb-8588-f306fb9da848.png?auto=compress,format\&format=webp)
2.  Apply the manifest file

    ```
     kubectl apply -f httpd-pod.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728897772682/f5bb62f3-32ca-49ff-ae60-239252207c1a.png?auto=compress,format\&format=webp)
3.  `pod/httpd-pod` created. Now, Verify the Pod.

    ```
     kubectl get pods
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728897866907/7a434ef0-23c0-4b2e-8baf-7be00ccf8513.png?auto=compress,format\&format=webp)
4.  Then, check the resources on given pod

    ```
     kubectl describe pod httpd-pod
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728897990933/e2bc4c6c-5adf-4529-8dc8-6a5cf42645c7.png?auto=compress,format\&format=webp)

\#k8s #kubernetes #devops #pods #limitation #happylearning
