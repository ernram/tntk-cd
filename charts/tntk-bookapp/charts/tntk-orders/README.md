# tntk-order

Welcome to the `tntk-order` repository! This project contains a Helm chart for deploying an order management application on Kubernetes. This guide will help you understand the structure of the repository and how to get started.

## Repository Structure

- **.helmignore**: Lists files and directories to ignore when packaging the Helm chart.
- **Chart.yaml**: Contains metadata about the Helm chart, such as its name, version, and description.
- **templates/**: Contains Kubernetes resource templates that Helm uses to deploy the application.
  - **_helpers.tpl**: Defines reusable template functions for the chart.
  - **deployment.yaml**: Describes the deployment configuration for the application.
  - **hpa.yaml**: Configures horizontal pod autoscaling if enabled.
  - **service.yaml**: Defines the Kubernetes service to expose the application.
  - **serviceaccount.yaml**: Manages the service account for the application.
  - **tests/test-connection.yaml**: A test pod to verify the connection to the service.
- **values.yaml**: Default configuration values for the Helm chart. You can override these values during deployment.

## Getting Started

### Prerequisites

- **Kubernetes**: Ensure you have a Kubernetes cluster running.
- **Helm**: Install Helm to manage Kubernetes applications.

### Installation

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd tntk-cd-2.0/tntk-order
   ```

2. **Deploy the Chart**:
   Use Helm to deploy the chart to your Kubernetes cluster.
   ```bash
   helm install my-order ./ --values values.yaml
   ```

   Replace `my-order` with your desired release name.

### Configuration

You can customize the deployment by modifying the `values.yaml` file or by providing your own values file. Key configuration options include:

- **replicaCount**: Number of replicas for the deployment.
- **image.repository**: Docker image repository for the application.
- **service.type**: Type of Kubernetes service (e.g., `ClusterIP`, `NodePort`).
- **postgresql**: Database connection details.

### Testing

To test the deployment, Helm provides a test hook defined in `templates/tests/test-connection.yaml`. Run the following command to execute the test:
