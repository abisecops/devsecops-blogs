# Kubernetes Cronjob Scheduling Guide

![Schedule Cronjobs in Kubernetes](https://cdn.hashnode.com/res/hashnode/image/upload/v1729013210536/d775c58b-d758-47b6-b179-f2b2a23da527.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Schedule Cronjobs in Kubernetes

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a cronjob named `xfusion`.
* Set its schedule to something like `*/7 * * * *`. You can set any schedule for now.
* Name the container `cron-xfusion`.
* Utilize the `httpd` image with `latest tag` (specify as `httpd:latest`).
* Execute the dummy command `echo Welcome to xfusioncorp!`.
* Ensure the restart policy is `OnFailure`.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Create a manifest file `cronjob.yaml` using given details.

    ```
     apiVersion: batch/v1
     kind: CronJob
     metadata:
       name: xfusion
     spec:
       schedule: "*/7 * * * *"
       jobTemplate:
         spec:
           template:
             spec:
               restartPolicy: OnFailure
               containers:
                 - name: cron-xfusion
                   image: httpd:latest
                   command: ["echo", "Welcome to xfusioncorp!"]
    ```

    ```
     cat <<EOF > cronjob.yaml
     apiVersion: batch/v1
     kind: CronJob
     metadata:
       name: xfusion
     spec:
       schedule: "*/7 * * * *"
       jobTemplate:
         spec:
           template:
             spec:
               restartPolicy: OnFailure
               containers:
                 - name: cron-xfusion
                   image: httpd:latest
                   command: ["echo", "Welcome to xfusioncorp!"]
     EOF
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729013879975/7209f03b-bf38-406b-99e1-adc23f91cba8.png?auto=compress,format\&format=webp)
2.  Now apply the yaml manifest file.

    ```
     k apply -f cronjob.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729013949582/a5a2b526-d01a-4e14-b9ff-5db6a63d29e4.png?auto=compress,format\&format=webp)

    * We can also use `kubectl apply -f cronjob.yaml` too.
3.  Let’s get the result.

    ```
      k get cronjob -o wide
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729014098343/38b4bfa6-abb5-46bb-8f59-08c496b9dd3a.png?auto=compress,format\&format=webp)
4.  Describe the cronjob now.

    ```
     k describe cronjob
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729014220136/4452faa6-180d-439d-bbdb-ce420136442a.png?auto=compress,format\&format=webp)

    \#cronjob #k8s #kubernetes #happylearning
