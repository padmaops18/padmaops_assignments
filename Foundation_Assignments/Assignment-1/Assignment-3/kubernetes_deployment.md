# Kubernetes Deployment Assignment

## 1. Why do we need Kubernetes in our application lifecycle?

We use Kubernetes to manage and run our containerized applications. When we deploy an application using Docker, we can run it inside a container. But when we have multiple containers and applications running across different environments, managing them manually becomes difficult.

This is where Kubernetes comes into the picture. It helps us automate the deployment, scaling, and management of containerized applications.

Some important reasons why we use Kubernetes are:

1. **Container Management:** Kubernetes helps us manage multiple containers running across different nodes in a cluster.

2. **Auto Scaling:** When application traffic increases, Kubernetes can automatically increase the number of application pods based on resource utilization, if autoscaling is configured.

3. **Self-Healing:** If a pod crashes or becomes unhealthy, Kubernetes can automatically restart it or create a replacement pod to maintain the desired number of replicas.

4. **Load Balancing:** Kubernetes Services help distribute incoming traffic across multiple application pods.

5. **High Availability:** We can run multiple replicas of an application so that if one pod fails, other pods can continue serving requests.

6. **Rolling Updates and Rollbacks:** We can deploy a new application version gradually without taking the entire application down. If something goes wrong, we can roll back to the previous version.

7. **Resource Management:** Kubernetes helps manage CPU and memory resources allocated to containers.

In simple terms, Kubernetes makes it easier to deploy, manage, scale, and maintain applications in a reliable way.

## 2. What are the Kubernetes objects required to deploy an application and why do we need them?

To deploy an application in Kubernetes, we use different Kubernetes objects. Each object has its own purpose.

1. **Namespace:** We use namespaces to logically separate applications and environments within a Kubernetes cluster. For example, we can have separate namespaces for development, QA, and production.

2. **Deployment:** This is one of the main objects we use to deploy our application. It manages the application pods and maintains the desired number of replicas. It also helps with rolling updates and rollbacks.

3. **Pod:** A pod is the smallest deployable unit in Kubernetes. It runs one or more containers. Our application container runs inside the pod.

4. **Service:** We use a Service to provide a stable network endpoint for accessing application pods. Since pod IP addresses can change when pods are recreated, the Service provides a consistent way to communicate with them.

5. **ConfigMap:** We use ConfigMaps to store non-sensitive configuration information, such as application settings and environment-specific values. This allows us to keep configuration separate from the application image.

6. **Secret:** We use Secrets to store sensitive information such as passwords, API keys, and database credentials. This helps keep sensitive information separate from application code. In production, we should also configure appropriate encryption and access controls.

7. **Ingress:** We use Ingress to manage external HTTP and HTTPS access to applications running inside the Kubernetes cluster. It allows us to route traffic to different services based on hostnames or URL paths. It requires an Ingress Controller to work.

8. **Horizontal Pod Autoscaler (HPA):** We use HPA to automatically increase or decrease the number of application pod replicas based on CPU, memory, or other configured metrics.

9. **Persistent Volume (PV) and Persistent Volume Claim (PVC):** We use these when an application needs persistent storage. A PVC requests storage, and a PV provides the storage resource.

### Conclusion

In a typical application deployment, we build a Docker image and push it to a container registry such as Amazon ECR. Then Kubernetes pulls that image and deploys it using a Deployment object.

The Deployment creates and manages the Pods, and the Service provides a stable way to access those Pods. We can use ConfigMaps and Secrets for configuration, and Ingress to expose the application externally.

Together, these Kubernetes objects help us deploy, manage, scale, and maintain our applications efficiently.
