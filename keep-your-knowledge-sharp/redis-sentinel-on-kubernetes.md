# Redis Sentinel on Kubernetes

This document contains references to Redis Sentinel architecture with Master Slave using Kubernetes.

### Master-Slave with Sentinel

This architecture offers high availability, good data consistency, and less complexity in customer implementation.

Using this architecture with Master-Slave, there will be a master responsible for writing and the others only for reading.

In addition to the Master and Slaves, a Sentinel instance is also created for each Redis instance.

Sentinel is responsible for identifying the master, and if there is a problem with the master, Sentinel will elect a new master.

![Sentinel architecture](https://camo.githubusercontent.com/163aab4a6a4b859bcb9012218a71f35b37d774f4c0b20ea28d12e254902b0133/68747470733a2f2f7274666d2e636f2e75612f77702d636f6e74656e742f75706c6f6164732f323031392f30332f73637265656e2d73686f742d323031372d30382d31312d61742d31342d33342d34322e706e67)

### Configuring the Application

We will use a simple chat to test the Sentinel architecture. To access the code: [https://github.com/ThiagoBfim/basic-redis-chat-app-demo-jav](https://github.com/ThiagoBfim/basic-redis-chat-app-demo-jav)

The application need to have the configurations to connect to Sentinels.

[Example with Spring](https://github.com/spring-projects/spring-data-examples/blob/main/redis/sentinel/src/main/java/example/springdata/redis/sentinel/RedisSentinelApplication.java)

### Application integration with Redis.

Sentinel will be responsible for finding out who the master is and returning this information to the application.

The application will make the connection with the master to perform the writing.

For more information: [https://redis.io/topics/sentinel-clients](https://redis.io/topics/sentinel-clients)

#### Note

* If the master becomes unavailable, the Sentinel will elect a new master.
* If the Sentinel becomes unavailable, the application will make the call to the other Sentinel.

#### Important

To integrate with Kubernetes, we will use the Bitnami Helm package: [https://github.com/bitnami/charts/tree/master/bitnami/redis](https://github.com/bitnami/charts/tree/master/bitnami/redis)

### Quick Guide

Install the Redis with Kubernetes using the Helm https://github.com/bitnami/charts/tree/master/bitnami/redis

```
helm repo add bitnami https://charts.bitnami.com/bitnami

helm install my-release \
  --set auth.password=secretpassword \
  --set sentinel.enabled=true \
    bitnami/redis
```

#### Start the Application

```
git clone https://github.com/ThiagoBfim/basic-redis-chat-app-demo-java
cd basic-redis-chat-app-demo-java
docker build -t chat-app .
kubectl apply -f app-kubernetes.yaml
```

#### Access the Application

Access localhost:30001

#### Bonus: Test the Failover

```
1. $ kubectl exec --tty -i redis-client    --namespace default -- bash
2. $ redis-cli -h my-release-redis -p 26379 -a $REDIS_PASSWORD
3. $ SENTINEL get-master-addr-by-name mymaster
4. $ SENTINEL failover mymaster
5. $ SENTINEL get-master-addr-by-name mymaster
```

After that, you will notice that the IP of the master will change.

### Conclusion

After Failover, the master will be unavailable until a new master is released. During this time, writing stops working, as the Sentinels will be establishing a new Master.

I realized that it is a short time of unavailable, and it can be followed by the logs.

The Quick Guide application works because it's all within the same Kubernetes network.

If the application is not in the same network of the Redis, it is necessary to configure one NetworkPolicy to allows the access of the application to the Redis Master,

If the application is not accessing the same network as Redis, it will be necessary to configure NetworkPolicy to allow the return of the Redis Master application, through the return of Sentinel by the command `SENTINEL get-master-addr-by-name mymaster` .

Remembering that this is just a POC, these settings should not be used in production.

### References

If you want to access the code of the application, access: [https://github.com/ThiagoBfim/basic-redis-chat-app-demo-java](https://github.com/ThiagoBfim/basic-redis-chat-app-demo-java)

* [Redis on Kubernetes](https://medium.com/swlh/production-checklist-for-redis-on-kubernetes-60173d5a5325)
* [Bitnami Redis Cluster - master-slave cluster with Redis Sentinel](https://engineering.bitnami.com/articles/deploy-and-scale-a-redis-cluster-on-kubernetes-with-bitnami-and-helm.html)
* [Redis Documentation](https://docs.redislabs.com/latest/platforms/kubernetes/getting-started/quick-start/)
* [Redis Cluster Specification](https://redis.io/topics/cluster-spec)
* [Redis Sentinel Documentation](https://redis.io/topics/sentinel)
* [Example Java Project](https://developpaper.com/understanding-springboot-integration-in-redis-cluster-environment/)
