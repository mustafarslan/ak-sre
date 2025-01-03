# ak-sre

## Prerequisites
Ensure you have the following installed on your system:
- Docker
- Docker Compose
- Kubernetes
- Minikube

Start Minikube before performing the following operations:
```
    minikube start
```



## Docker Image
The Docker image for this project is available at:
```
    docker pull mustafarslan/k8s-java-sample:0.0.4
```


## Kubernetes Deployment
All necessary deployment, service, and ingress YAML files are located inside the `k8s` folder.

To deploy the application on Kubernetes, use the following commands:

1. Apply the Kubernetes configurations:
```
    kubectl apply -f .
```

2. Expose the deployment as a LoadBalancer service:
```
   kubectl expose deployment java-api --type=LoadBalancer --name=java-api-service 
```

3. Forward the port to access the application locally:
```
   kubectl port-forward deployment/java-api 8081:8081 
```


4. To check out deployed pods, use the Minikube dashboard:
```
    minikube dashboard
```

## Grafana and Prometheus
To set up Grafana and Prometheus, use Docker Compose. The necessary `docker-compose.yaml` file is located under the `foundation` folder.

1. Start the services:
```
    docker compose up -d
```


## Blackbox Exporter
To build and run the Blackbox Exporter, the required Dockerfile is located under the `blackbox` folder:

1. Build the Docker image:
```
    docker build -t blackbox .
```

2. Run the Docker container:
```
     docker run -d -p 9115:9115 --name blackbox blackbox
```


## Additional Information
- Ensure you have Docker, Docker Compose, and Kubernetes installed on your system.
- For testing API endpoints, you can use Postman or a similar API client.
- Refer to the provided Postman collection in the `app/foundation/postman` directory for API requests.

## Author
- **Mustafa Arslan**