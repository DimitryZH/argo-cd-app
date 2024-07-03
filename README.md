# Argo CD Root Application Manager

This project showcases the use of a root Argo CD Application to manage and orchestrate the deployment of two other Argo CD applications, `myapp1` and `myapp2`. The root application approach enables a hierarchical management structure, simplifying the governance of multiple applications across different environments (development and production) within a Kubernetes cluster. The project utilizes a customizable Helm Chart, allowing for easy adaptation of the applications with support for custom container images and replica counts.

## Project Structure

- **Argo CD Application Definitions**: YAML files defining Argo CD Application resources for both development and production environments. These files specify the source repository, target revision, deployment destination, and synchronization policies.
- **Helm Charts**: Contains the Helm chart for deploying the applications. The chart includes templates for Kubernetes `Deployment` and `Service` resources, configured to deploy a web application.
- **Values Files**: Separate values files for development (`values_dev.yaml`) and production (`values_prod.yaml`) environments, allowing for environment-specific configurations such as the number of replicas and the container image.

## Key Features

- **Multi-Environment Deployment**: Supports separate configurations for development and production environments, facilitating easy promotion of changes.
- **Automated Synchronization**: Leveraging Argo CD's sync policies for automated deployment, pruning, and self-healing of application resources.
- **Customizable Helm Chart**: A Helm chart that can be easily adapted for different applications, with support for custom container images and replica counts.

## Prerequisites

Before deploying this project, ensure the following prerequisites are met:

1. **AWS EKS Deployed**: An Amazon EKS cluster must be deployed and operational. For guidance on setting up an EKS cluster, refer to the project ["AWS EKS Clusters Configuration"](https://github.com/DimitryZH/eks-clusters).
2. **ArgoCD Deployed in EKS**: ArgoCD must be installed and configured within your EKS cluster to manage application deployments. For instructions on deploying ArgoCD on EKS using Terraform, see the project ["ArgoCD Deployment on Amazon EKS with Terraform"](https://github.com/DimitryZH/argo-cd-app-terraform/tree/main).
3. **Choose Container Application**: For this project, a Dockerized application is used. You can find the source code on GitHub at ["Dockerized TestApp"](https://github.com/DimitryZH/docker-testapp) and the container image on DockerHub at [Dockerized PHP web application](https://hub.docker.com/r/dmitryzhuravlev/testapp)
## Implementation

To leverage the power of automation provided by ArgoCD, follow these steps:

1. **Create a Repository**: Host the code for this project in a version control repository.
2. **Provide Repository Link to ArgoCD**: Access the ArgoCD UI and add the repository link for both the development and production environments.
3. **Automatic Deployment**: ArgoCD will periodically check the specified repository for changes. Upon detecting updates, it will automatically deploy these changes to the respective environments, ensuring that your applications are always up-to-date with the source code.

This approach minimizes manual intervention and leverages ArgoCD's capabilities to ensure a seamless continuous deployment pipeline.

## Results

### Root Application Management
![Root Application Management](https://github.com/DimitryZH/argo-cd-app/assets/146372946/7e5eebed-106f-43f5-b4a3-191cbfb40298)


### Development Environment Deployment
![Development Environment Deployment](https://github.com/DimitryZH/argo-cd-app/assets/146372946/d1b1c863-da16-43f3-8b4d-004d21aa2230)

### Production Environment Deployment
![Production Environment Deployment](https://github.com/DimitryZH/argo-cd-app/assets/146372946/1607da94-cb19-478d-8408-6f434cefe5e3)

### Container Application Running in Development and Production Environments
![Running Container Application](https://github.com/DimitryZH/argo-cd-app/assets/146372946/9bd67ec9-8991-4e05-ad23-a06a6f9be74e)

