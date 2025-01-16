# TNTK Books Helm Chart

This repository contains a Helm chart for deploying the TNTK Books application on Kubernetes. The application is a simple web service that can be deployed using Helm and Docker.

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Helm](https://helm.sh/docs/intro/install/)
- [Kubernetes](https://kubernetes.io/docs/tasks/tools/)

## Getting Started

### Running with Docker

1. **Build the Docker Image**

   First, ensure Docker is running on your machine. Then, build the Docker image:

   ```bash
   docker build -t tntk-books:latest .
   ```

2. **Run the Docker Container**

   Run the container using the following command, replacing the placeholders with your actual values:

   ```bash
   docker run -p 8000:8000 \
     -e DB_HOST=<your_db_host> \
     -e DB_PORT=<your_db_port> \
     -e DB_USER=<your_db_user> \
     -e DB_PASSWORD=<your_db_password> \
     tntk-books:latest
   ```

   The application will be accessible at `http://localhost:8000`.

### Running with Docker Compose

1. **Create a `docker-compose.yml` File**

   Below is a sample `docker-compose.yml` file with environment variables:

   ```yaml
   version: '3.8'
   services:
     books:
       image: tntk-books:latest
       build: .
       ports:
         - "8000:8000"
       environment:
         DB_HOST: <your_db_host>
         DB_PORT: <your_db_port>
         DB_USER: <your_db_user>
         DB_PASSWORD: <your_db_password>
   ```

2. **Run Docker Compose**

   Use the following command to start the application:

   ```bash
   docker-compose up
   ```

   The application will be accessible at `http://localhost:8000`.

### Deploying with Helm

1. **Add the Helm Repository**

   If you haven't already, add the Helm repository:

   ```bash
   helm repo add my-repo https://example.com/charts
   ```

2. **Install the Chart**

   Install the chart using Helm:

   ```bash
   helm install my-books-release ./tntk-books
   ```

   This will deploy the application to your Kubernetes cluster.

3. **Access the Application**

   Depending on your Kubernetes setup, you may need to use a service like `kubectl port-forward` to access the application. For example:

   ```bash
   kubectl port-forward svc/my-books-release-books 8000:8000
   ```

   The application will be accessible at `http://localhost:8000`.

## Configuration

The application can be configured using the `values.yaml` file. You can override these values by providing your own `values.yaml` file or using the `--set` flag with Helm.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## License

This project is licensed under the MIT License.

## Environment Variables

The application requires the following environment variables:

- `DB_HOST`: The hostname of the database.
- `DB_PORT`: The port number of the database.
- `DB_USER`: The username for the database.
- `DB_PASSWORD`: The password for the database.

You can set these variables in your environment or specify them in the `docker-compose.yml` file.