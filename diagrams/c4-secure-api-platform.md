# C4 – Secure API Platform

> **Icarus Nova** | High-level container diagram for secure API platform architecture.

## System Context

```mermaid
C4Context
    title System Context - Secure API Platform
    
    Person(user, "API Consumers", "External and internal API consumers")
    Person(admin, "Security Administrators", "Managing security policies")
    
    System(platform, "Secure API Platform", "Enterprise-grade API platform with security-first design")
    
    System_Ext(identity, "Identity Provider", "OIDC/OAuth2 provider")
    System_Ext(monitoring, "Security Monitoring", "External security monitoring")
    
    Rel(user, platform, "Uses APIs")
    Rel(admin, platform, "Manages")
    Rel(platform, identity, "Authenticates with")
    Rel(platform, monitoring, "Sends security events")
    
    UpdateElementStyle(user, $bgColor="#e1f5ff")
    UpdateElementStyle(admin, $bgColor="#e1f5ff")
    UpdateElementStyle(platform, $bgColor="#90EE90")
```

## Container Diagram

```mermaid
C4Container
    title Container Diagram - Secure API Platform
    
    Person(user, "API Consumers")
    Person(admin, "Security Administrators")
    
    System_Boundary(platform, "Secure API Platform") {
        Container(apigw, "API Gateway", "Kong/Envoy", "Advanced API gateway with security")
        Container(iam, "Identity Provider", "Keycloak/Auth0", "Identity and access management")
        Container(threat, "Threat Protection", "WAF/DDoS", "DDoS protection, WAF, rate limiting")
        Container(api_svc, "API Services", "Microservices", "Backend API services")
        Container(security, "Security Services", "Security Stack", "Security scanning, threat detection")
        Container(audit, "Audit Service", "Audit Service", "Comprehensive audit logging")
        Container(monitor, "Monitoring Platform", "Security Monitoring", "Security monitoring and alerting")
    }
    
    Rel(user, threat, "HTTPS")
    Rel(admin, apigw, "HTTPS")
    Rel(threat, apigw, "Filtered Requests")
    Rel(apigw, iam, "OAuth2")
    Rel(apigw, api_svc, "Authenticated Requests")
    Rel(apigw, security, "Security Checks")
    Rel(apigw, audit, "Audit Logs")
    Rel(api_svc, audit, "Audit Logs")
    Rel(api_svc, monitor, "Security Events")
    Rel(security, monitor, "Threat Alerts")
    
    UpdateElementStyle(apigw, $bgColor="#90EE90")
    UpdateElementStyle(iam, $bgColor="#E6E6FA")
    UpdateElementStyle(threat, $bgColor="#FF6B6B")
    UpdateElementStyle(api_svc, $bgColor="#87CEEB")
    UpdateElementStyle(security, $bgColor="#FFE4B5")
    UpdateElementStyle(audit, $bgColor="#DDA0DD")
    UpdateElementStyle(monitor, $bgColor="#F0E68C")
```

## Key Interactions

### Secure API Request Flow

1. **Request**: User sends request to Threat Protection
2. **Threat Check**: Threat protection filters malicious requests
3. **Authentication**: API Gateway authenticates with Identity Provider
4. **Authorization**: API Gateway authorizes request
5. **Security Scan**: Security services scan for threats
6. **API Processing**: API services process request
7. **Audit**: All operations logged
8. **Monitoring**: Security events monitored

## Related Documents

- [Secure API Platform Architecture](../docs/secure-api-platform.md)
- [Reference Architectures Index](../docs/index.md)

---

**Last Updated:** 2024  
**Maintained by:** Icarus Nova Architecture Team  
**Version:** 1.0
