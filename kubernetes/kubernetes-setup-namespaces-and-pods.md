# Kubernetes: Setup Namespaces and PODs

![Setup Kubernetes Namespaces and PODs](https://cdn.hashnode.com/res/hashnode/image/upload/v1728895051410/ff7bd2c8-4942-461d-992c-3ce2f8626e94.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### How to Create and Manage Kubernetes Namespaces and PODs

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a namespace named `dev`.
* Deploy a pod named `dev-nginx-pod` in the `dev` namespace.
* Use the `nginx` image with the `latest` tag for the pod.
* Ensure to specify the image tag as `nginx:latest`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  First create the namespace named dev.

    ```
     kubectl create namespace dev
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728895411813/bd19b64e-8123-4201-8b0f-c05bb12354be.png?auto=compress,format\&format=webp)
2.  Manifest with `yaml file`:

    ```
     apiversion: v1
     kind: Namespace
     metadata:
       name: dev
    ```

    But I prefer using EOF

    ```
     cat <<EOF > namespace-dev.yaml
     apiVersion: v1
     kind: Namespace
     metadata:
       name: dev
     EOF
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728895874115/be9cf035-2963-4559-b3f3-151621049c93.png?auto=compress,format\&format=webp)
3.  Create namespace now:

    ```
     kubectl create -f namespace-dev.yaml --save-config
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728895998189/e69a4180-d44b-404a-8d99-fa0ccb68e4b5.png?auto=compress,format\&format=webp)
4.  Create pods now, `nginx-pod.yaml`

    ```
     apiVersion: v1
     kind: Pod
     metadata:
       name: dev-nginx-pod
       namespace: dev
     spec:
       containers:
       - name: nginx
         image: nginx:latest
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728896179907/dcdf3d8a-e5d7-4e96-af0e-4169d9732742.png?auto=compress,format\&format=webp)
5.  Apply the YAML manifest file.

    ```
     kubectl apply -f nginx-pod.yaml
    ```
6.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728896229529/9315abe4-807d-46ed-a73c-3363a5ca9951.png?auto=compress,format\&format=webp)

    Now List Namespaces

    ```
     kubectl get namespaces
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728896319761/5c3308e9-7728-4347-bfa8-366c9bcc4e0d.png?auto=compress,format\&format=webp)
7.  List Pods in a Namespace

    ```
     kubectl get pods -n dev
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728896411670/36a3a149-71b4-4f46-a27a-c019c6e8b38a.png?auto=compress,format\&format=webp)

    \#k8s #kubernetes #pods #namespace #happylearning :)
