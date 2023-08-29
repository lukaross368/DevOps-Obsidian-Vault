#AWS #dataBases #cloud #devops #awsServices 

A Managed Database service from AWS. It Supports MySQL and Postgres and is 'Cloud Optimized' meaning it gets increased performance over [[RDS]]

It can Automatically grow up to 64 TB

Can have up to 15 Replicas 

Native High Availability 

Faster Failover than RDS

Costs more but is more efficient


### Aurora HA and Read Scaling

- 6 Copies of your Data across 3 AZ ([[Availability Zones]])
	- 4 copies out of 6 needed for writes
	- 3 copies out of 6 needed for reads
	- self healing with peer to peer replication
	- storage is striped across 100s of volumes in the backend
- One Aurora Instance takes the writes (master node), this instance will fail over in less than 30 seconds if it crashes
- Master + up to 15 read replicas to serve read workloads (read replicas can be auto-scaling)
- Also supports cross region replicas 

### Aurora DB Cluster

to connect to your cluster you have a writer endpoint and a reader endpoint 

![[aurora_db.png]]

### Aurora Features

- Auto fail-over
- backup and recovery
- isolation and security
- industry compliance
- push-button scaling
- auto patching with 0 downtime
- advanced monitoring 
- routine maintenance
- backtrack: restore data at any point of time without using backups 

### Aurora Security

- Encryption at rest using KMS
- Auto backups, snapshots and replicas are also encrypted
- encryption in flight using SSL (See [[SSL]])
- authentication using [[IAM]]
- you are responsible for protecting the instance with [[Security Groups]]
- You cant [[SSH]]
