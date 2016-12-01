# Demo Code for Prometheus Monitoring via Kubernetes Service Discovery.

This demo code assumes a working kubernetes cluster. Furthermore all service accounts should have read permissions on the kubernetes API. 

## Setup Prometheus and Grafana

```
kubectl apply -f prometheus
```

The following command should show you the external IPs of the services.
```
kubectl get svc --namespace=monitoring
```

After all pods have started, you can import the grafana dashboards in the grafana Web UI. The dashboards are located in the `grafana_dashboards` directory.

## Deployment of ToDo App
The initial deployment of the ToDo App is done via:
```
kubectl apply -f todo-app
```

## Scale ToDo App
```
kubectl --namespace=todo-app scale deployment/todo-app --replicas=10
```

## Downgrade of ToDo App

```
kubectl set --namespace=todo-app image deployment/todo-app todo-app=johscheuer/todo-app-web:v4
```

## Update of ToDo App

```
kubectl set --namespace=todo-app image deployment/todo-app todo-app=johscheuer/todo-app-web:v6
``` 
