# Kubernetes Time Check Pod Setup Guide

![Set Up Time Check Pod in Kubernetes](https://cdn.hashnode.com/res/hashnode/image/upload/v1729179915591/f16fc29e-74d2-4bdc-bea4-e56b67e77d25.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Set Up Time Check Pod in Kubernetes

### How to Efficiently Set Up a Time Check Pod in Kubernetes

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Create a pod called `time-check` in the `devops` namespace. The pod should have a container named `time-check`, using the `busybox` image with the `latest` tag (`busybox:latest`).
* Create a config map named `time-config` with the data `TIME_FREQ=12` in the same namespace.
* Configure the `time-check` container to run the command: `while true; do date; sleep $TIME_FREQ; done`. Ensure the output is written to `/opt/sysops/time/time-check.log`. Add an environment variable `TIME_FREQ` in the container, getting its value from the config map `TIME_FREQ` key.
* Create a volume `log-volume` and mount it at `/opt/sysops/time` within the container.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Create a manifest file `time-check.yaml`.

    ```
     apiVersion: v1
     kind: Namespace
     metadata:
       name: devops
     ---
     apiVersion: v1
     kind: ConfigMap
     metadata:
       name: time-config
       namespace: devops
     data:
       TIME_FREQ: "12"
     ---
     apiVersion: v1
     kind: Pod
     metadata:
       name: time-check
       namespace: devops
     spec:
       containers:
         - name: time-check
           image: busybox:latest
           command: ["sh", "-c", "while true; do date >> /opt/sysops/time/time-check.log; sleep $TIME_FREQ; done"]
           env:
             - name: TIME_FREQ
               valueFrom:
                 configMapKeyRef:
                   name: time-config
                   key: TIME_FREQ
           volumeMounts:
             - name: log-volume
               mountPath: /opt/sysops/time
       volumes:
         - name: log-volume
           emptyDir: {}
    ```

    ```
     cat << EOF > time-check.yaml
     apiVersion: v1
     kind: Namespace
     metadata:
       name: devops
     ---
     apiVersion: v1
     kind: ConfigMap
     metadata:
       name: time-config
       namespace: devops
     data:
       TIME_FREQ: "12"
     ---
     apiVersion: v1
     kind: Pod
     metadata:
       name: time-check
       namespace: devops
     spec:
       containers:
         - name: time-check
           image: busybox:latest
           command: ["sh", "-c", "while true; do date >> /opt/sysops/time/time-check.log; sleep \$TIME_FREQ; done"]
           env:
             - name: TIME_FREQ
               valueFrom:
                 configMapKeyRef:
                   name: time-config
                   key: TIME_FREQ
           volumeMounts:
             - name: log-volume
               mountPath: /opt/sysops/time
       volumes:
         - name: log-volume
           emptyDir: {}
     EOF
    ```
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729180872302/711da3b2-a07a-4942-ab0e-13c28986c37d.png?auto=compress,format\&format=webp)

    Now apply

    ```
     kubectl apply -f time-check.yaml
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729181012497/f9673bd7-cce2-416d-bb50-8df8f7134ddf.png?auto=compress,format\&format=webp)
3. ss
