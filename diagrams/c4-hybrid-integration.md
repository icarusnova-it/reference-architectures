# C4 – Hybrid Integration Platform

> **Icarus Nova** | High-level container diagram for hybrid integration platform architecture.

## System Context

```mermaid
C4Context
    title System Context - Hybrid Integration Platform
    
    Person(user, "Business Users", "Users accessing integrated systems")
    Person(admin, "Integration Administrators", "Managing integrations")
    
    System(platform, "Hybrid Integration Platform", "Integration platform connecting on-premises and cloud systems")
    
    System_Ext(onprem, "On-Premises Systems", "Legacy and on-premises systems")
    System_Ext(cloud, "Cloud Services", "Cloud-based services and APIs")
    
    Rel(user, platform, "Uses")
    Rel(admin, platform, "Manages")
    Rel(platform, onprem, "Integrates with")
    Rel(platform, cloud, "Integrates with")
    
    UpdateElementStyle(user, $bgColor="#e1f5ff")
    UpdateElementStyle(admin, $bgColor="#e1f5ff")
    UpdateElementStyle(platform, $bgColor="#90EE90")
```

## Container Diagram

```mermaid
C4Container
    title Container Diagram - Hybrid Integration Platform
    
    Person(user, "Users")
    Person(admin, "Administrators")
    
    System_Boundary(platform, "Hybrid Integration Platform") {
        Container(apigw, "API Gateway", "Kong/Envoy", "Unified API management")
        Container(hub, "Integration Hub", "Integration Platform", "Central integration platform")
        Container(broker, "Message Broker", "RabbitMQ/Kafka", "Message routing and queuing")
        Container(connector, "On-Premises Connector", "Connector Service", "Secure on-premises connectivity")
        Container(cloud_svc, "Cloud Services", "Microservices", "Cloud-based services")
        Container(sync, "Data Sync Service", "Sync Service", "Data synchronization")
        Container(monitor, "Monitoring Platform", "Monitoring Stack", "Unified monitoring")
    }
    
    System_Ext(onprem_sys, "On-Premises Systems", "Legacy systems")
    System_Ext(cloud_sys, "Cloud Services", "External cloud services")
    
    Rel(user, apigw, "HTTPS")
    Rel(admin, apigw, "HTTPS")
    Rel(apigw, hub, "Internal")
    Rel(hub, broker, "Publish/Subscribe")
    Rel(hub, connector, "Internal")
    Rel(connector, onprem_sys, "Secure Tunnel")
    Rel(hub, cloud_svc, "Internal")
    Rel(cloud_svc, cloud_sys, "HTTPS")
    Rel(hub, sync, "Internal")
    Rel(hub, monitor, "Metrics/Logs")
    
    UpdateElementStyle(apigw, $bgColor="#90EE90")
    UpdateElementStyle(hub, $bgColor="#87CEEB")
    UpdateElementStyle(broker, $bgColor="#FFE4B5")
    UpdateElementStyle(connector, $bgColor="#DDA0DD")
    UpdateElementStyle(cloud_svc, $bgColor="#87CEEB")
    UpdateElementStyle(sync, $bgColor="#F0E68C")
    UpdateElementStyle(monitor, $bgColor="#F0E68C")
```

## Key Interactions

### Integration Flow

1. **Request**: User sends request via API Gateway
2. **Routing**: API Gateway routes to Integration Hub
3. **Transformation**: Hub transforms and routes message
4. **On-Premises**: Connector securely connects to on-premises systems
5. **Cloud**: Cloud services connect to external cloud services
6. **Synchronization**: Data sync service synchronizes data
7. **Monitoring**: All operations monitored

## Related Documents

- [Hybrid Integration Platform Architecture](../docs/hybrid-integration-platform.md)
- [Reference Architectures Index](../docs/index.md)

---

**Last Updated:** 2024  
**Maintained by:** Icarus Nova Architecture Team  
**Version:** 1.0
