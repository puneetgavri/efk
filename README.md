## ELK Stack
![efk](https://github.com/puneetgavri/efk/blob/main/efk.jpeg "efk")


### Elastic Search 
> is a no sql db that stores the data from various sources

### Logstash 
> is a service that can collect the data from various sources & pushes to Elastic Search DB

### beats 
> beats are small agents, that can collet the data from various sources & push data to either Logstash or directly to Elastic Search DB

### Kibana
> Kibana is a data visualization and exploration tool used for log and time-series analytics, application monitoring, and operational intelligence use cases. It offers powerful and easy-to-use features such as histograms, line graphs, pie charts, heat maps, and built-in geospatial support.

![efk_k8s](https://github.com/puneetgavri/efk/blob/main/EFK-stack-on-Kubernetes.jpg "efk_k8s")

### Introduction to EFK stack

The EFK stack is a set of open-source tools designed for log management and analysis in a modern software development environment. EFK stands for Elasticsearch, Fluentd, and Kibana. Let’s break down each component:

### Elasticsearch:

Role: Elasticsearch is a distributed, RESTful search and analytics engine.
Function: It stores and indexes data, making it easily searchable and analyzable. Elasticsearch is highly scalable and can handle large amounts of data across multiple nodes.

### Fluentd:

Role: Fluentd is a log collector and aggregator.
Function: Fluentd is responsible for collecting log data from various sources within a system, such as applications, servers, and containers. It then normalizes and forwards this data to Elasticsearch for indexing. Fluentd supports a wide range of inputs and outputs, making it versatile for diverse log sources.

### Kibana:

Role: Kibana is a web-based visualization tool.
Function: Kibana provides a user-friendly interface for interacting with the log data stored in Elasticsearch. It allows users to create dashboards, visualizations, and perform ad-hoc queries to gain insights into the log data. Kibana is instrumental in turning raw log information into meaningful and actionable visual representations.
## Deploy Elatic Search, Kibana & Filebeat on kubernetes Cluster 

>> **Note: the stack requries minimum of 2cpu/4gb ram in each worker node where they will run**

```sh
kubectl apply -f https://raw.githubusercontent.com/puneetgavri/efk/refs/heads/main/elastic-search.yaml
```

```sh
kubectl apply -f https://raw.githubusercontent.com/puneetgavri/efk/refs/heads/main/kibana.yaml
```

```sh
kubectl apply -f https://raw.githubusercontent.com/puneetgavri/efk/refs/heads/main/filebeat.yaml
```

## get kibana login credentials 
> **username**
```sh
kubectl get secrets --namespace=default elasticsearch-master-credentials -ojsonpath='{.data.username}' | base64 -d ; echo
```

> **password**
```sh
kubectl get secrets --namespace=default elasticsearch-master-credentials -ojsonpath='{.data.password}' | base64 -d ; echo
```
