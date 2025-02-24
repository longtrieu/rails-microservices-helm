# rails-microservices-helm
Rails Microservices Helm

Helm Chart Structure
```
helm-charts/
  ├── charts/
  │   ├── order-service/
  │   ├── payment-service/
  │   ├── kafka/
  │   ├── zookeeper/
  │   ├── postgres/
  │   ├── redis/
  │   ├── sidekiq/
  ├── values.yaml
  ├── Chart.yaml
  ├── templates/
```


High-Level Kubernetes architecture
```
+----------------------------------------------------+
| Kubernetes Cluster                                |
| +-------------------+  +----------------------+   |
| | Order Service     |  | Payment Service      |   |
| | (Rails API)       |  | (Rails API)          |   |
| | + Sidekiq         |  | + Kafka Consumer     |   |
| | + Redis           |  |                      |   |
| +-------------------+  +----------------------+   |
| +-------------------+  +----------------------+   |
| | Kafka Broker      |  | Zookeeper            |   |
| | (Event Streaming) |  | (Manages Kafka)      |   |
| +-------------------+  +----------------------+   |
| +-------------------+  +----------------------+   |
| | PostgreSQL DB     |  | Redis (Sidekiq)      |   |
| | Persistent Data   |  | Queue Management     |   |
| +-------------------+  +----------------------+   |
+----------------------------------------------------+
```
