# K8s

To create a Kubernetes Pod using the Docker image `mranoint/abisec1:latest` that you've pushed to Docker Hub, you'll need to create a YAML manifest file (`pod.yaml`) specifying the Pod configuration. Here's how you can do it:

#### Step-by-Step Guide:

**1. Create a Pod YAML File (`pod.yaml`)**

Create a file named `pod.yaml` and add the following content. This configuration specifies a basic Pod that uses your Docker image:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: abisec1-pod
spec:
  containers:
  - name: abisec1-container
    image: mranoint/abisec1:latest
    ports:
    - containerPort: 80  # Port your application listens on inside the container
```

* **Explanation**:
  * `apiVersion`: Specifies the Kubernetes API version.
  * `kind`: Specifies the type of resource, in this case, a Pod.
  * `metadata`: Provides metadata about the Pod, including its name (`abisec1-pod`).
  * `spec`: Specifies the specification for the Pod.
    * `containers`: Defines an array of containers within the Pod.
      * `name`: Specifies the name of the container (`abisec1-container`).
      * `image`: Specifies the Docker image to use (`mranoint/abisec1:latest`).
      * `ports`: Specifies the ports to expose from the container. In this example, it exposes port 80.

**2. Apply the Pod Configuration**

Apply the `pod.yaml` file to your Kubernetes cluster to create the Pod:

```bash
kubectl apply -f pod.yaml
```

This command sends the Pod configuration to Kubernetes, which will create the Pod based on the specified configuration.

**3. Verify Pod Creation**

Check the status of the Pod to ensure it has been created successfully:

```bash
kubectl get pods
```

You should see your Pod (`abisec1-pod`) in the list, and its status should eventually change to `Running` once the container starts and is ready.

#### Notes:

* **Image Availability**: Ensure that the Docker image `mranoint/abisec1:latest` is accessible from your Kubernetes cluster. Kubernetes will pull the image from Docker Hub (`docker.io`) unless configured otherwise.
* **Networking**: Verify that your Kubernetes cluster has network access to Docker Hub to pull the image.
* **Permissions**: Make sure your Kubernetes environment has the necessary permissions to pull images from Docker Hub.

By following these steps, you should be able to deploy your Docker image (`mranoint/abisec1:latest`) as a Kubernetes Pod successfully. Adjust the `pod.yaml` file as needed based on your application's specific requirements (e.g., additional environment variables, volume mounts, etc.).
