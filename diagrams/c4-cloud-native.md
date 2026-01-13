# C4 – Cloud-Native Platform

> **Icarus Nova** | High-level container diagram for cloud-native platform architecture.

## System Context

```mermaid
C4Context
    title System Context - Cloud-Native Platform
    
    Person(user, "End Users", "Application users")
    Person(admin, "Administrators", "Platform administrators")
    
    System(platform, "Cloud-Native Platform", "Scalable, resilient platform for enterprise applications")
    
    System_Ext(identity, "Identity Provider", "OIDC/OAuth2 provider")
    System_Ext(monitoring, "External Monitoring", "External monitoring services")
    
    Rel(user, platform, "Uses")
    Rel(admin, platform, "Manages")
    Rel(platform, identity, "Authenticates with")
    Rel(platform, monitoring, "Sends metrics to")
    
    UpdateElementStyle(user, $bgColor="#e1f5ff")
    UpdateElementStyle(admin, $bgColor="#e1f5ff")
    UpdateElementStyle(platform, $bgColor="#90EE90")
```

## Container Diagram

```mermaid
C4Container
    title Container Diagram - Cloud-Native Platform
    
    Person(user, "Users")
    Person(admin, "Administrators")
    
    System_Boundary(platform, "Cloud-Native Platform") {
        Container(apigw, "API Gateway", "Kong/Envoy", "Request routing, authentication, rate limiting")
        Container(core, "Core Services", "Microservices", "Business logic services (stateless)")
        Container(edge, "Edge Services", "Microservices", "External-facing services")
        Container(events, "Event Bus", "Kafka/RabbitMQ", "Asynchronous message broker")
        ContainerDb(db, "Operational Data Store", "PostgreSQL", "Transactional database")
        Container(obs, "Observability Stack", "Prometheus/Grafana", "Logging, metrics, tracing")
        Container(iam, "Identity Provider", "Keycloak/Auth0", "Authentication and authorization")
    }
    
    Rel(user, apigw, "HTTPS")
    Rel(admin, apigw, "HTTPS")
    Rel(apigw, iam, "OAuth2")
    Rel(apigw, core, "Internal")
    Rel(apigw, edge, "Internal")
    Rel(core, events, "Publish/Subscribe")
    Rel(edge, events, "Publish/Subscribe")
    Rel(core, db, "JDBC")
    Rel(edge, db, "JDBC")
    Rel(core, obs, "Metrics/Logs")
    Rel(edge, obs, "Metrics/Logs")
    
    UpdateElementStyle(apigw, $bgColor="#90EE90")
    UpdateElementStyle(core, $bgColor="#87CEEB")
    UpdateElementStyle(edge, $bgColor="#87CEEB")
    UpdateElementStyle(events, $bgColor="#FFE4B5")
    UpdateElementStyle(db, $bgColor="#DDA0DD")
    UpdateElementStyle(obs, $bgColor="#F0E68C")
    UpdateElementStyle(iam, $bgColor="#E6E6FA")
```

## Key Interactions

### Request Flow

1. **User Request**: User sends request to API Gateway
2. **Authentication**: API Gateway authenticates with Identity Provider
3. **Routing**: API Gateway routes to appropriate service (Core or Edge)
4. **Processing**: Service processes request, may publish events
5. **Response**: Service returns response through API Gateway
6. **Observability**: All operations logged and metered

### Event Flow

1. **Event Publishing**: Service publishes event to Event Bus
2. **Event Distribution**: Event Bus distributes to subscribers
3. **Event Processing**: Subscriber services process events
4. **State Updates**: Services update state based on events

## Notes

This is a high-level container view to communicate primary interactions. For detailed component views, see the architecture documentation.

## Related Documents

- [Cloud-Native Platform Architecture](../docs/cloud-native-platform.md)
- [Reference Architectures Index](../docs/index.md)

---

**Last Updated:** 2024  
**Maintained by:** Icarus Nova Architecture Team  
**Version:** 1.0
