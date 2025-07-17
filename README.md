
# 🌐 Travel-Bank_K8S-Deployment_v_13.0

> 🧭 Kubernetes-based deployment for Travel Bank Microservices Suite, enhanced with role-based dashboard access and clean microservice orchestration.

---

## 📁 Project Structure

```
sectionNew15/
├── kubernetes/
│   ├── 1_keycloak.yml
│   ├── 2_configmaps.yaml
│   ├── 3_configserver.yml
│   ├── 4_eurekaserver.yml
│   ├── 5_accounts.yml
│   ├── 6_loans.yml
│   ├── 7_cards.yml
│   ├── 8_gateway.yml
├── kubernetes-dashboard-UI/
│   ├── dashboard-adminuser.yaml
│   ├── dashboard-rolebinding.yaml
│   ├── secret.yaml
```

---

## 🛠️ Kubernetes Dashboard Setup

### 🧩 Step-by-Step

1. `kubectl config use-context docker-desktop`
2. `kubectl get nodes`
3. Apply dashboard configs:
    ```bash
    kubectl apply -f dashboard-adminuser.yaml
    kubectl apply -f dashboard-rolebinding.yaml
    kubectl apply -f secret.yaml
    ```
4. Generate admin token (PowerShell):
    ```powershell
    kubectl get secret admin-user -n kubernetes-dashboard -o jsonpath="{.data.token}" | ForEach-Object {
        [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($_))
    }
    ```

5. Access dashboard via proxy:
    ```bash
    kubectl proxy
    ```

---

## ⚙️ Microservices Management Commands

| Command | Description |
|--------|-------------|
| `kubectl get deployments` | View deployments |
| `kubectl get services` | View all services |
| `kubectl get pods` | Check pod status |
| `kubectl delete pod <pod-name>` | Delete a specific pod |
| `kubectl get events --sort-by=.metadata.creationTimestamp` | View events (logs) |
| `kubectl scale deployment accounts-deployment --replicas=1` | Manually scale deployment |
| `kubectl set image deployment gatewayserver-deployment gatewayserver=vinaysteja0231/gatewayserver:v9.0 --record` | Update deployment image |
| `kubectl rollout history deployment gatewayserver-deployment` | View deployment revisions |
| `kubectl rollout undo deployment gatewayserver-deployment --to-revision=1` | Rollback to a previous revision |
| `kubectl delete -f 8_gateway.yml` | Delete gateway microservice |

---

## 🔁 Previous Versions

### 📦 Travel-Bank_Apache-Kafka_v_12.0

> Apache Kafka + Spring Cloud Stream + Function = Asynchronous Microservice Architecture

### 🧱 Key Concepts

- **Producers / Consumers / Topics**
- **Partitions and Offsets**
- **Spring Cloud Function (Supplier, Function, Consumer)**

### ⚙️ Setup

```bash
docker-compose up     # Start Kafka & Zookeeper
Start Spring Boot Apps
```

---

## 🧾 Version History

| Version | Features |
|--------|----------|
| v1.0 | Core Microservices |
| v2.0 | Docker Integration |
| v3.0 | Config Client |
| v4.0 | Config Server |
| v5.0 | MySQL Integration |
| v6.0 | Eureka Service Discovery |
| v7.0 | API Gateway |
| v8.0 | Resilience4j Circuit Breaker |
| v9.0 | Grafana + Prometheus Observability |
| v10.0 | OAuth2 + Keycloak |
| v11.0 | RabbitMQ Asynchronous |
| v12.0 | Kafka Asynchronous |
| v13.0 | Full Kubernetes Deployment with Dashboard Support |

---

## 🧑‍💻 Author

Built with ❤️ by **Vinay Steja**  
🔗 [GitHub](https://github.com/vinaysteja2)

---

## 🪪 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
