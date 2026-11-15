# 4. How code promotion happens and what testing processes are involved and why?

Once the developer raises a PR, CI gets triggered. It runs the required checks such as build validation, unit tests, code quality checks and security scans. Once all the checks pass, the PR is approved and the code is merged into the main branch.

After the merge, the CI/CD pipeline gets triggered. It compiles the code using a build tool like Maven or Gradle, runs the unit test cases, performs static code analysis using SonarQube and checks dependencies for any vulnerabilities.

Once these checks pass, we package the application into a Docker image, scan it using Trivy, and push it to a container registry like JFrog Artifactory or Amazon ECR.

## Deployment and Testing Across Environments

### 1. Dev Environment

The image from ECR is deployed onto the Dev environment running on an AWS EKS cluster.

We perform the following tests:

- **Smoke Testing:** Quickly checks whether the application is up and running, its health endpoints respond, and basic API functionality works.
- **Integration Testing:** Verifies that the application communicates properly with its dependent services, databases, and external APIs.

Once Dev validation passes, the same Docker image is promoted to the QA environment.

### 2. QA Environment

In QA, we perform different types of testing:

- **Functional Testing:** Verifies that new features work as expected based on business requirements.
- **Regression Testing:** Ensures that new code changes did not break any existing functionality.
- **End-to-End Testing:** Validates the complete user journey across different application components.
- **Performance Testing:** Checks the application response time, stability, and behavior under load.
- **Security Testing:** Identifies potential security vulnerabilities in the application.
- **UAT (User Acceptance Testing):** Ensures the application meets business expectations and is ready for release.

### 3. Pre-Prod Environment

After QA approval, the image is promoted to Pre-Prod, which closely resembles Production.

We perform final validation, check environment configurations, and verify deployment and rollback readiness.

### 4. Production Environment

Finally, after the required approvals, we promote the image to Production.

We perform smoke tests and monitor application health, logs, and performance using tools like Prometheus, Grafana, or CloudWatch.

## Why do we follow this process?

The main purpose is to catch issues as early as possible, validate the application at every stage, and make sure that only tested and approved code reaches Production.

We build the Docker image once and promote that same image across Dev, QA, Pre-Prod, and Production. We don't rebuild a separate image for every environment. Only environment-specific configurations change.
