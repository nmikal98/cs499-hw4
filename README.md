# cs499-h4

curl -L https://github.com/kubernetes/kompose/releases/download/v1.26.0/kompose-linux-amd64 -o kompose
chmod +x kompose
sudo mv ./kompose /usr/local/bin/kompose

kompose convert

kubectl apply -f frontend-service.yaml,geo-service.yaml,jaeger-service.yaml,profile-service.yaml,rate-service.yaml,search-service.yaml,frontend-deployment.yaml,geo-deployment.yaml,jaeger-deployment.yaml,profile-deployment.yaml,rate-deployment.yaml,search-deployment.yaml
