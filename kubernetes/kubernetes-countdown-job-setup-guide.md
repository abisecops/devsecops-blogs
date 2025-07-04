# Kubernetes Countdown Job Setup Guide

![Create Countdown Job in Kubernetes](https://cdn.hashnode.com/res/hashnode/image/upload/v1729094419071/ab0d60e1-4732-4d8e-8c8c-285f481afd8a.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Create Countdown Job in Kubernetes

### How to Set Up a Countdown Job in Kubernetes

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a job named `countdown-datacenter`.
* Name the spec template `countdown-datacenter` (under metadata), and name the container `container-countdown-datacenter`.
* Use the image `fedora` with the `latest` tag (specify as `fedora:latest`), and set the restart policy to `Never`.
* Execute the command `sleep 5`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Create a `job.yaml` manifest file.

    ```
     apiVersion: batch/v1
     kind: Job
     metadata:
       name: countdown-datacenter
     spec:
       template:
         metadata:
           name: countdown-datacenter
         spec:
           containers:
           - name: container-countdown-datacenter
             image: fedora:latest
             command: ["sleep", "5"]
           restartPolicy: Never
    ```

    ```
     cat <<EOF > job.yaml
     apiVersion: batch/v1
     kind: Job
     metadata:
       name: countdown-datacenter
     spec:
       template:
         metadata:
           name: countdown-datacenter
         spec:
           containers:
           - name: container-countdown-datacenter
             image: fedora:latest
             command: ["sleep", "5"]
           restartPolicy: Never
     EOF
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729097493624/f3920933-1778-4616-8cfe-4c5446ca7269.png?auto=compress,format\&format=webp)
2.  Apply the manifest file.

    ```
     k apply -f job.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729097622320/6e4728ac-fcd4-43d7-931e-8068f5c3f8cc.png?auto=compress,format\&format=webp)
3.  Now describe `job`.

    ```
     k describe job
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729097768616/0ebaf640-fdd6-4b5b-96e6-e54e9edf44d5.png?auto=compress,format\&format=webp)

    \#k8s #coundown #devops #happylearning
