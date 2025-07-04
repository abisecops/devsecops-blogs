# Revert Deployment to Previous Version

![Revert Deployment to Previous Version in Kubernetes](https://cdn.hashnode.com/res/hashnode/image/upload/v1728901692959/8bf54529-28d2-44f3-8014-e3bff006fe50.png?w=1600\&h=840\&fit=crop\&crop=entropy\&auto=compress,format\&format=webp)

### Revert Deployment to Previous Version in Kubernetes

### How to Roll Back to a Previous Deployment Version in Kubernetes

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Rollback the deployment named `nginx-deployment` to the previous revision.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1.  Check the existing deployments

    ```
     kubectl get deployments
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728901797671/5bb60131-082c-4bec-b7b3-531180ffb64b.png?auto=compress,format\&format=webp)
2.  Roll Back the Deployment

    ```
     kubectl rollout undo deployment/nginx-deployment
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728901930974/8ac10e8b-9487-41de-acdd-063252c649c5.png?auto=compress,format\&format=webp)
3.  Now verfify with status

    ```
     kubectl rollout status deployment/nginx-deployment
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728901996974/7e414b18-2e54-44b2-915a-bd9a3892037d.png?auto=compress,format\&format=webp)
4.  List pods

    ```
     kubectl get pods
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728902071340/521e8fd1-d4f3-49b8-ae14-9ad1047e81ba.png?auto=compress,format\&format=webp)
5.  Confirm the image version

    ```
     kubectl describe deployment nginx-deployment
    ```

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728902162171/729528e1-cc80-44ce-8af0-d6fb376c5807.png?auto=compress,format\&format=webp)

    You can see image version is `nginx:1.16` now.
6.  Out of the box, chill method with `404 error`;

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728902288827/d9a51ac9-52b1-4801-9766-65f982265442.png?auto=compress,format\&format=webp)

    \#k8s #revert #happylearning
