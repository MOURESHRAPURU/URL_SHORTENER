#Docker Instructions
#Details
### A.Build Docker Image docker build -t url-shortener . ### B. Run Docker Container Locally docker run -p 8080:8080 url-shortener
Kubernetes Instructions
Details
### Ensure Docker Desktop or Minikube is running and kubectl is configured. ### A.Apply ConfigMap kubectl apply -f url-shortener-configmap.yaml ### B. Deploy Application kubectl apply -f url-shortener-deployment.yaml ### C. Expose Service via NodePort kubectl apply -f url-shortener-service.yaml ### D. Access the App Open your browser at: http://:30080 If using Minikube, get the IP using: minikube ip
📈 Scaling the App
Details
You can manually scale the app or use HPA.
Manual Scaling:
kubectl scale deployment url-shortener --replicas=5

Autoscaling via HPA
kubectl autoscale deployment url-shortener --cpu-percent=50 --min=2 --max=10

🔍 Monitoring & Logs
kubectl get pods
kubectl logs

🧪 Testing
Details
#Manual Testing Open the UI in browser (NodePort or Ingress URL).
Enter a long URL (e.g., https://example.com).

Click Shorten.

Copy the shortened URL.

Paste in browser → It should redirect to original URL.

Try with non-existent short links → Should show 404-style page.

API Testing (Optional)
Use curl or Postman:
curl -X POST http://:/shorten
-H "Content-Type: application/json"
-d '{"url": "https://example.com"}'

💣 Load/Stress Testing
Use Apache Benchmark:
ab -n 1000 -c 10 http://:/
Or use locust for interactive load testing.

# URL_SHORTENER
