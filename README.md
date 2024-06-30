
# Initial Configuration for Spring Boot 3 Microservice Template

[Spring Boot 3 Base Microservices Template](https://github.com/OlveraRobertP/Spring-Boot-3-Base-MicroServices)

This repository contains the initial configuration for setting up microservices using Spring Boot 3. It supports two environments: `dev` (development) and `prod` (production).

## Configuration Overview

### General Configuration

The `application.yml` file contains general parameters applicable to all microservices. Specific configurations required for each microservice are then overwritten as needed.

### Environment-Specific Settings

- **Development (`dev`)**: Designed for local development and testing.
- **Production (`prod`)**: Configured for deployment in a production environment.

### Eureka Server Configuration

In the `eureka-server`, you need to configure the `hostname` and `defaultZone` settings specifically for the production environment. This ensures that the service discovery mechanism functions correctly in the intended deployment scenario.

### API Gateway Configuration

The `api-gateway` defines the routing of services. It acts as the entry point for all incoming requests and forwards them to the appropriate microservices based on the configured routes.

## Detailed Configuration Steps

1. **Clone the Repository**
   ```sh
   git clone https://github.com/OlveraRobertP/Spring-Boot-3-Base-MicroServices.git
   ```

2. **Navigate to the Project Directory**
   ```sh
   cd Spring-Boot-3-Base-MicroServices
   ```

3. **Configure `application.yml`**
   - General settings for all microservices.
   - Overwrite specific settings for `dev` and `prod` environments.

4. **Eureka Server Configuration**
   - Set `hostname` and `defaultZone` for the production environment in `eureka-server`:
     ```yaml
     eureka:
       instance:
         hostname: your-production-hostname
       client:
         serviceUrl:
           defaultZone: http://your-production-eureka-server/eureka/
     ```

5. **API Gateway Configuration**
   - Define service routes in `api-gateway`:
     ```yaml
     spring:
       cloud:
         gateway:
           routes:
             - id: your-service-id
               uri: lb://your-service-name
               predicates:
                 - Path=/your-service-path/**
     ```

## Additional Instructions

- Ensure environment variables are set appropriately before starting the services.
- Verify that the configured ports are not in use by other services.
- Refer to the documentation of each component for specific adjustments and customizations.

For further details and advanced configurations, please refer to the [official repository](https://github.com/OlveraRobertP/Spring-Boot-3-Base-MicroServices).
