# local-kubernetes-nginx-minikube

# Local Kubernetes Nginx Minikube Deployment

This project demonstrates a basic deployment of the Nginx web server on a local Kubernetes cluster using Minikube. It serves as a foundational example for understanding how to containerize and orchestrate applications with Kubernetes in a local development environment.

## Problem Statement

To provide a simple and reproducible example of deploying a web application using Kubernetes on a local machine for learning and development purposes.

## Architecture

This project utilizes a single Kubernetes Deployment to manage three replicas of the Nginx container. Minikube provides the local Kubernetes cluster where this deployment runs.

```mermaid
graph LR
    A[Local Machine] --> B(Minikube Cluster);
    B --> C(Kubernetes Deployment);
    C --> D1(Nginx Pod 1);
    C --> D2(Nginx Pod 2);
    C --> D3(Nginx Pod 3);
    D1 -- Runs --> E(Nginx Container);
    D2 -- Runs --> E;
    D3 -- Runs --> E;

Okay, let's create a good README.md file for your "Local Kubernetes Nginx Minikube Deployment" project. Here's a suggestion with key sections that are helpful for GitHub projects:
Markdown

# Local Kubernetes Nginx Minikube Deployment

This project demonstrates a basic deployment of the Nginx web server on a local Kubernetes cluster using Minikube. It serves as a foundational example for understanding how to containerize and orchestrate applications with Kubernetes in a local development environment.

## Problem Statement

To provide a simple and reproducible example of deploying a web application using Kubernetes on a local machine for learning and development purposes.

## Architecture

This project utilizes a single Kubernetes Deployment to manage three replicas of the Nginx container. Minikube provides the local Kubernetes cluster where this deployment runs.

```mermaid
graph LR
    A[Local Machine] --> B(Minikube Cluster);
    B --> C(Kubernetes Deployment);
    C --> D1(Nginx Pod 1);
    C --> D2(Nginx Pod 2);
    C --> D3(Nginx Pod 3);
    D1 -- Runs --> E(Nginx Container);
    D2 -- Runs --> E;
    D3 -- Runs --> E;

Prerequisites

    Docker: Must be installed on your local machine as Minikube is configured to use the Docker driver. You can find installation instructions here.
    Minikube: Must be installed to run the local Kubernetes cluster. Installation instructions can be found here.
    kubectl: The Kubernetes command-line tool must be installed to interact with the Minikube cluster. Installation instructions can be found here.
    Git: Installed for version control (you've already used this!).

Deployment Commands

    Start Minikube:
    Bash

minikube start --driver=docker

(If you used a specific profile like mynewcluster, use that: minikube start --driver=docker --profile mynewcluster)

Ensure kubectl is configured for your Minikube cluster:
Bash

kubectl config use-context minikube

(Or the name of your Minikube context, e.g., mynewcluster)

Apply the Nginx Deployment: Navigate to the directory containing the nginx-deployment.yaml file and run:
Bash

    kubectl apply -f nginx-deployment.yaml

Validation Steps

    Check the Deployment status:
    Bash

kubectl get deployments -n default

You should see nginx-deployment with READY as 3/3.

Check the running Pods:
Bash

kubectl get pods -n default

You should see three Pods with names starting with nginx-deployment- and their status as Running.

(Optional) Access Nginx via Port Forwarding (for testing):
Bash

    kubectl port-forward deployment/nginx-deployment 8000:80 -n default

    Open a web browser on your local machine and navigate to http://localhost:8000. You should see the default Nginx welcome page. Remember to stop the port forwarding with Ctrl+C when you are finished.

Troubleshooting

    kubectl not found: Ensure kubectl is installed and in your system's PATH.
    Minikube not starting: Check the Minikube documentation for common issues and try running minikube logs.
    Deployment not creating Pods: Use kubectl describe deployment nginx-deployment to see any error messages.
    Pods in Pending state: Use kubectl describe pod <pod-name> to investigate resource issues or node availability.

Key Learnings

    Basic Kubernetes Deployment concepts.
    Using kubectl to interact with a Kubernetes cluster.
    Deploying a containerized application on a local Kubernetes environment.
    Understanding the role of Minikube for local Kubernetes development.
