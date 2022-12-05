# cs499-hw4

## Deploy app (using images from DockerHub)

kubectl create deployment frontend --image=hvolos01/hotel_app_frontend_single_node_memdb:latest -- frontend

kubectl create deployment profile --image=hvolos01/hotel_app_profile_single_node_memdb:latest -- profile

kubectl create deployment search --image=hvolos01/hotel_app_search_single_node_memdb:latest -- search

kubectl create deployment geo --image=hvolos01/hotel_app_geo_single_node_memdb:latest -- geo

kubectl create deployment rate --image=hvolos01/hotel_app_rate_single_node_memdb:latest -- rate

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

## scale deployment

kubectl scale deployment NAME --replicas NUMBER

## WRK

git clone https://github.com/wg/wrk.git

cd wrk

make -j

./wrk -t2 -c5 -d5s --timeout 2s http://kube1:3xxxx

## Results

![](/Img/Latency.png)

![](/Img/Troughput.png)


we can see that latency decreaces and throuput increases with uncreasing number of pods. This is expected since we have more resources to serve our requests.
With larer number of pods we notice more stable response times, this could be due to networking overheads. If the load is not too large a bigger amount of pods will no increace the performace.
