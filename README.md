
🛠️ Ecommerce Microservices - Configuration Repository
======================================================

This repository contains all configuration files used by the [Ecommerce Microservices Project](https://github.com/DarshanAguru/ecommerceMicroservice.git).  
It is meant to be used with Spring Cloud Config Server for dynamic, centralized configuration management.

------------------------------------------------------------
📁 Structure
------------------------------------------------------------

Each `.properties` or `.yml` file in this repository corresponds to a specific microservice and is named according to the Spring Cloud Config conventions:

| File Name                   | Description                                      |
|----------------------------|--------------------------------------------------|
| auth-server.properties     | Configs for the authentication service          |
| consumer-server.properties | Configs for async data update Kafka consumer     |
| eureka-server.yml          | Configs for Eureka service discovery server      |
| gateway-server.properties  | Configs for the API gateway                      |
| gateway-server.yml         | Additional YAML configs for the gateway          |
| order-server.properties    | Configs for order processing service             |
| payment-server.properties  | Configs for the payment service                  |
| product-server.properties  | Configs for the product catalog service          |

------------------------------------------------------------
⚙️ How It Works
------------------------------------------------------------

- The `configServer` service in the main ecommerce project is configured to pull from this Git repository.
- When each microservice starts, it queries the config server and fetches its corresponding configuration file.
- Format: `{application-name}-{profile}.properties` or `.yml`

Example:
A microservice named `auth-server` with profile `default` will fetch:
```
auth-server.properties
```

------------------------------------------------------------
📦 Configuration Includes
------------------------------------------------------------

- Server ports and service names
- Spring Data source (PostgreSQL) settings
- Kafka Bootstrap and topic config
- Zipkin tracing URL
- Eureka client/server settings
- Authentication filters and token paths (for API Gateway)

------------------------------------------------------------
🔐 Security
------------------------------------------------------------

If this repository is private, configure `configServer` to use a Git token or basic auth credentials to access it.

------------------------------------------------------------
📎 How to Use
------------------------------------------------------------

1. Make sure the `application.yml` in `configServer` points to this repo:
```yaml
spring:
 cloud:
  config:
   server:
    git:
     uri: https://github.com/DarshanAguru/ecommerceMicroserviceConfigs.git
```

2. Run the `configServer` first, then start other microservices.

------------------------------------------------------------
✍️ Contribution
------------------------------------------------------------

Feel free to fork, clone, or improve the configs.  
Make sure you follow naming conventions and avoid leaking sensitive info like passwords or tokens.

------------------------------------------------------------
📬 Contact
------------------------------------------------------------

Darshan Aguru  
GitHub: https://github.com/DarshanAguru  
Devfolio: https://agurudarshan.tech


