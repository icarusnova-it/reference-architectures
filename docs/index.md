# Reference Architectures Index

This repository contains curated reference architectures for enterprise-grade systems.

## Catalog

1. **Cloud-Native Platform** → [`cloud-native-platform.md`](./cloud-native-platform.md)
   - Scalable, resilient, and observable platforms in cloud environments
   - API-first services, event-driven integration, centralized observability

2. **Hybrid Integration Platform** → [`hybrid-integration-platform.md`](./hybrid-integration-platform.md)
   - Integration between on-premises and cloud systems
   - API management, message routing, data synchronization

3. **Secure API Platform** → [`secure-api-platform.md`](./secure-api-platform.md)
   - Enterprise-grade API platform with security-first design
   - Identity and access management, threat protection, compliance

4. **Event-Driven Enterprise** → [`event-driven-enterprise.md`](./event-driven-enterprise.md)
   - Event-driven architecture for large-scale systems
   - Event sourcing, CQRS, distributed event processing

5. **Data Platform (Lakehouse)** → [`data-platform-lakehouse.md`](./data-platform-lakehouse.md)
   - Modern data platform combining data lake and warehouse
   - Data ingestion, transformation, analytics, governance

## How to Use

1. **Start with Business Context**: Review the context and design drivers for each architecture
2. **Review Diagrams**: Check the C4 diagrams in `/diagrams` for visual understanding
3. **Check ADRs**: Review `/adr` for architectural decisions and rationale
4. **Adapt to Your Needs**: Use these as starting points, not prescriptive solutions

## Principles

- **Security by Design**: Security is built in, not bolted on
- **Observability First**: Full visibility into system behavior and health
- **Evolutionary Architecture**: Architectures evolve with business needs
- **Explicit Trade-offs**: Clear documentation of what is optimized for and what is not

## Architecture Template

All reference architectures follow a consistent format:
- **Context**: Problem and scope
- **Design Drivers**: Key requirements and constraints
- **Key Capabilities**: Core functionality
- **High-Level Architecture**: Container-level view
- **Security Baseline**: Authentication, authorization, encryption
- **Observability**: Logging, metrics, tracing
- **Scalability & Resilience**: Scaling and failure handling
- **Trade-offs**: What is optimized and what is not
- **Evolution Strategy**: How the architecture evolves

## Related Documents

- [Architecture Template](./_template.md)
- [ADR-0001: Reference Architecture Format](../adr/0001-reference-architecture-format.md)
- [ADR-0002: Security Baseline](../adr/0002-security-baseline.md)

---

**Last Updated:** 2024  
**Maintained by:** Icarus Nova Architecture Team  
**Version:** 1.0
