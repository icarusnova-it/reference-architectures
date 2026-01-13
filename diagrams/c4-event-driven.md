# C4 – Event-Driven Enterprise

> **Icarus Nova** | High-level container diagram for event-driven enterprise architecture.

## System Context

```mermaid
C4Context
    title System Context - Event-Driven Enterprise
    
    Person(user, "End Users", "Application users")
    Person(analyst, "Data Analysts", "Analyzing event data")
    
    System(platform, "Event-Driven Enterprise", "Large-scale event-driven system for real-time processing")
    
    System_Ext(external, "External Systems", "External event sources")
    
    Rel(user, platform, "Uses")
    Rel(analyst, platform, "Analyzes")
    Rel(external, platform, "Publishes Events")
    Rel(platform, external, "Publishes Events")
    
    UpdateElementStyle(user, $bgColor="#e1f5ff")
    UpdateElementStyle(analyst, $bgColor="#e1f5ff")
    UpdateElementStyle(platform, $bgColor="#90EE90")
```

## Container Diagram

```mermaid
C4Container
    title Container Diagram - Event-Driven Enterprise
    
    Person(user, "Users")
    Person(analyst, "Data Analysts")
    
    System_Boundary(platform, "Event-Driven Enterprise") {
        Container(events, "Event Bus", "Kafka/Pulsar", "High-throughput event streaming")
        Container(producers, "Event Producers", "Microservices", "Services producing events")
        Container(consumers, "Event Consumers", "Microservices", "Services consuming events")
        Container(store, "Event Store", "Event Store", "Event sourcing storage")
        Container(query, "Query Store", "Read Models", "CQRS read models")
        Container(router, "Event Router", "Router Service", "Event routing and filtering")
        Container(processing, "Processing Services", "Processing Services", "Event processing services")
    }
    
    Rel(user, producers, "Triggers Events")
    Rel(analyst, query, "Queries Data")
    Rel(producers, events, "Publishes")
    Rel(events, consumers, "Subscribes")
    Rel(events, router, "Routes")
    Rel(router, processing, "Processes")
    Rel(processing, store, "Stores Events")
    Rel(processing, query, "Updates Read Models")
    Rel(consumers, store, "Stores Events")
    
    UpdateElementStyle(events, $bgColor="#FFE4B5")
    UpdateElementStyle(producers, $bgColor="#87CEEB")
    UpdateElementStyle(consumers, $bgColor="#87CEEB")
    UpdateElementStyle(store, $bgColor="#DDA0DD")
    UpdateElementStyle(query, $bgColor="#DDA0DD")
    UpdateElementStyle(router, $bgColor="#F0E68C")
    UpdateElementStyle(processing, $bgColor="#90EE90")
```

## Key Interactions

### Event Flow

1. **Event Production**: Producers publish events to Event Bus
2. **Event Routing**: Event Router routes events to appropriate consumers
3. **Event Processing**: Processing services process events
4. **Event Storage**: Events stored in Event Store (event sourcing)
5. **Read Model Update**: Read models updated for queries
6. **Event Consumption**: Consumers process events and update state

## Related Documents

- [Event-Driven Enterprise Architecture](../docs/event-driven-enterprise.md)
- [Reference Architectures Index](../docs/index.md)

---

**Last Updated:** 2024  
**Maintained by:** Icarus Nova Architecture Team  
**Version:** 1.0
