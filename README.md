🌀 Reverse Proxy App - 📁 Project Overview

✅ Option 1: Run with docker-compose

▶️ Run the App
docker-compose up --build

🌐 Access the App
http://localhost

🛑 Stop the App
docker-compose down


✅ Option 2: Run with Docker Only

▶️ Build App Image 
docker build -t my-app-image .

🔍 Run App Container
docker run -d --name app -p 5000:5000 my-app-image

⚙️ Run NGINX Container
docker run -d \
  --name nginx \
  --link app \
  -p 80:80 \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  nginx


✅ Option 3: Run on Kubernetes

▶️ Apply Kubernetes Resources
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

🔍 Get Service Info
kubectl get service


📦 TL;DR Command Summary
# With Docker Compose
docker-compose up --build

# With Docker only
docker build -t my-app-image .
docker run -d --name app -p 5000:5000 my-app-image
docker run -d --name nginx --link app -p 80:80 -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro nginx

# With Kubernetes
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
