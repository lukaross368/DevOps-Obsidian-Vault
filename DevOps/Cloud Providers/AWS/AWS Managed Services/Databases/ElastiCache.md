#devops #cloud #AWS #dataBases #awsServices 

ElastiCache one of two in memory database solutions provided by AWS. 

Designed to serve workloads with super low latency and high throughput performance demands. 

ElastiCache comes in two flavours; Memcached and [[Redis]]


## ElastiCache for Redis

### Key Features

- Fully compatible with open source Redis
- AWS manages all hardware and software setup, config and monitoring 
- multi AZ (see [[Availability Zones]]) with auto failover cross-region replication cluster and auto scaling 
- in memory data store and cache for microsecond response times
- network isolation encryption at rest/in transit, RBAC HIPAA, PCI-DSS, FedRAMP
- scale reads with replicas scale writes with shards up to 500 nodes per cluster

Think of Redis as a distributed in-memory datastore 

### Use Cases

- Caching
- Real-time analytics
- gaming leader boards
- media streaming
- session store
- message queues

### Auto Scaling

- Automatically add shards or replicas to your cluster
- use predefined rules or [[Amazon CloudWatch]] metrics to horizontally scale in and out
- schedule scaling activities for predictable workload capacity changes
