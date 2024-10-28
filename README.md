# Docker Build and Deployment Workflow

This repository contains a CI/CD workflow for building Docker images, pushing them to a Docker registry, and deploying applications to a Kubernetes cluster using Gitea Actions and Ansible.

## Workflow Overview

The workflow is triggered on every push to the repository. It performs the following steps:

1. **Checkout Code**: Pulls the latest code from the repository.
2. **Set up Docker Buildx**: Prepares the environment for building Docker images.
3. **Build Docker Image**: Constructs a Docker image from the provided Dockerfile.
4. **Login to Docker Registry**: Authenticates with the Docker registry using stored credentials.
5. **Push Docker Image**: Tags and pushes the Docker image to the registry.
6. **Install kubectl**: Downloads and sets up `kubectl` for Kubernetes interactions.
7. **Create Kubeconfig**: Configures access to the Kubernetes cluster.
8. **Install Ansible**: Sets up Ansible and necessary Kubernetes collections.
9. **Run Ansible Playbook**: Executes the Ansible playbook to update the Kubernetes deployment.

## Prerequisites

Before using this workflow, ensure you have:

- A Docker account and repository set up to store your images.
- Access to a Kubernetes cluster and the appropriate credentials.
- The following secrets configured in your Gitea repository:
  - `DOCKERUSER`: Your Docker username.
  - `DOCKERPWD`: Your Docker password.
  - `KUBE_CONFIG`: Your Kubernetes config file content.

## Usage

To use this workflow:

1. Clone the repository.
2. Update the `.gitea.yml` file with your specific image name and repository details.
3. Push your changes to trigger the workflow.

## Additional Resources

For a more detailed explanation of this workflow and related concepts, check out my blog on Hashnode: [GITEA](https://invisible.hashnode.dev/how-to-build-a-cicd-pipeline-using-gitea-docker-ansible-and-kubernetes).

## Workflow Diagram

![Workflow Diagram](./gitea-cicd.drawio.svg)
