2. Walk through the core stages of the DevOps lifecycle, from the moment code is planned until it is running
   DevOps Lifecycle – From Planning to Production

3. Plan: We gather the requirements, break them into tasks or JIRA tickets and prioritize the work for that sprint.
4. Code: Developers write the application code, create short-lived feature branches, and raise pull requests for review.
5. Build: Once the code is approved and merged, Jenkins triggers the pipeline to compile the code and create a build artifact.
6. Test: We run unit tests, integration tests, code quality checks using SonarQube, and security scans using tools like OWASP Dependency-Check.
7. Release: After the checks pass, we package the application into a Docker image, scan it using Trivy, and push it to Amazon ECR.
8. Deploy: We deploy the application to AWS EKS, moving it through Dev, QA, Pre-Prod and finally Production after the required validations and approvals are done.
9. Operate and Monitor: Once the application is running, we monitor the application health, logs, performance and errors using tools like Prometheus, Grafana or CloudWatch.
10. Feedback: We use monitoring results and user feedback to identify issues, create new tasks, and improve the next development cycle.
