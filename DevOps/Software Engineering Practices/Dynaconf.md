#python #SEP #configManagement
## Why do we need Dynaconf?

According to the 12 factor app model, an apps config should be strictly separate from code and should not compromise any credentials. Config here can be defined as everything that is likely to vary between deploys (staging, production, developer environments, etc). For example;

- Resource handles to the database, Memcached, and other services
- Credentials to external services such as Amazon S3 or Twitter
- Per-deploy values such as the canonical hostname for the deploy

Dynaconf helps this problem by providing the ability to do configuration management in Python and aims to simplify the process.

It is a useful tool with the following features

- Settings Management
- Protection of sensitive info
- Full Support for env variables 
- Optional layered system for multi environments
- Built-in extensions for [[Django]]
### Hierarchical Configuration

Dynaconf allows you to manage config settings in a hierarchical way. You can define config values at different levels (global, env-specific or local), this flexibility enables you to have different configurations fir dev, staging and prod.  
### Environment-based configuration Management

Dynaconf simplifies handling env-specific config settings. It provides an easy way to define and switch between different envs.
### Dynamic Configuration updates 

Dynaconf provides the ability to update configuration values dynamically without restarting the application. This is useful when we want to make config changes immediately such as updating DB connections parameters or toggling [[Feature Flags]]. 
### Automated secret management

Dynaconf includes built in support for managing secrets. It provides a secure configuration management workflow allowing you to store sensitive information separately and securely away from the configuration files. This can be integrated with [[Hashicorp Vault]]
