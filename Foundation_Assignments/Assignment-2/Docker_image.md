## Assignment 2: Why do we need to build a Docker image for an application?

### 1. Why do we need to build a Docker image?

We build a Docker image to package an application along with all its dependencies, libraries, runtime, and configuration needed to run it.

The main reason is to make sure the application runs consistently across different environments, such as development, testing, and production.

For example, an application might work perfectly on a developer's laptop but fail on a server because of different software versions or missing dependencies. Docker solves this problem by packaging everything required to run the application into an image.

Some important reasons for using Docker images are:

- **Consistency:** The application runs the same way across different environments.
- **Portability:** We can run the same Docker image on a laptop, virtual machine, AWS EC2, or Kubernetes.
- **Dependency management:** All required libraries, packages, and runtime versions are included in the image.
- **Isolation:** Applications run in separate containers without interfering with each other.
- **Scalability:** We can create multiple containers from the same image when application traffic increases.
- **Easy deployment:** We can build the image once, push it to a Docker registry, and use the same image across different environments.

### 2. What pointers should we collect before developing a Dockerfile?

Before writing a Dockerfile, we need to understand the application and its requirements. We should collect the following information:

1. **Application details:** Understand what type of application we are containerizing, such as Java, Python, Node.js, or a web application.

2. **Base image:** Identify the required operating system or runtime image. For example, Python applications may use a Python base image, while Java applications may use an OpenJDK image.

3. **Application dependencies:** Identify all the libraries, packages, and dependencies required to run the application.

4. **Source code location:** Know where the application source code is located and which files need to be copied into the Docker image.

5. **Working directory:** Decide the directory inside the container where the application files will be stored and executed.

6. **Build commands:** Identify the commands needed to build the application, such as Maven for Java or pip for Python dependencies.

7. **Startup command:** Understand how to start the application. For example, whether we need to run a JAR file, Python script, or Node.js application.

8. **Ports:** Identify which port the application listens on so that we can expose the appropriate port in the Dockerfile.

9. **Environment variables:** Identify configuration values required by the application, such as environment names, database URLs, and application settings. Sensitive information like passwords should not be hardcoded in the image.

10. **Storage requirements:** Check whether the application needs persistent storage or access to external volumes.

11. **Security requirements:** Use trusted base images, avoid running the application as root where possible, and avoid including unnecessary files or secrets in the image.

12. **Image size:** Identify unnecessary files and dependencies that can be excluded to keep the Docker image smaller.

### Conclusion

Before writing a Dockerfile, we should understand the application, its runtime, dependencies, build process, ports, and startup requirements. Once we have these details, we can write a Dockerfile to build an image that can be used consistently across different environments.

As a DevOps engineer, the goal is to build the Docker image once, store it in a container registry, and use that same image throughout the CI/CD deployment pipeline.
