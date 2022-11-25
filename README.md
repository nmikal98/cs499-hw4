# cs499-hw4


## Deploy app (using images from DockerHub)

kubectl create deployment frontend --image=hvolos01/hotel_app_frontend_single_node_memdb:latest -- frontend

kubectl create deployment profile --image=hvolos01/hotel_app_frontend_single_node_memdb:latest -- profile

kubectl create deployment search --image=hvolos01/hotel_app_frontend_single_node_memdb:latest -- search

kubectl create deployment geo --image=hvolos01/hotel_app_frontend_single_node_memdb:latest -- geo

kubectl create deployment rate --image=hvolos01/hotel_app_frontend_single_node_memdb:latest -- rate

## watch deployment events

kubectl get deploy -w

## Expose each deployment, specifying the right port:

kubectl expose deployment profile --port 8081
kubectl expose deployment search --port 8082
kubectl expose deployment geo --port 8083
kubectl expose deployment rate --port 8084

## Create a NodePort service for the Web UI:

kubectl expose deployment frontend --type=NodePort --port 8080 

## Check the port that was allocated:
kubectl get svc
