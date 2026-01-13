# ADR-0001: Reference Architecture Format

## Status

**Accepted** - This decision establishes the standard format for all reference architectures.

## Context

Reference architectures must remain consistent, readable, and comparable across different domains and use cases. Without a standard format, architectures become difficult to understand, compare, and reuse.

We need a consistent template that:
- Makes architectures easy to understand
- Enables comparison between architectures
- Facilitates reuse and adaptation
- Maintains credibility and professionalism

## Decision

**All reference architectures will follow the same template structure:**

1. **Context**: Problem statement and scope
2. **Design Drivers**: Key requirements and constraints
3. **Key Capabilities**: Core functionality provided
4. **High-Level Architecture**: Container-level view with reference to diagrams
5. **Security Baseline**: Authentication, authorization, encryption, auditability
6. **Observability**: Logging, metrics, tracing, correlation
7. **Scalability & Resilience**: Scaling model, failure modes, recovery
8. **Trade-offs**: What is optimized for and what is not
9. **Evolution Strategy**: How the architecture evolves over time

## Consequences

### Positive

✅ **Faster Authoring**: Clear template reduces authoring time  
✅ **Easier Review**: Consistent structure enables quick review  
✅ **Higher Credibility**: Professional, consistent presentation  
✅ **Better Reuse**: Standard format facilitates adaptation  
✅ **Comparability**: Easy to compare different architectures  

### Negative

❌ **Rigidity**: Template may not fit all cases perfectly  
❌ **Maintenance**: Template updates require updating all architectures  

### Mitigation

- Template is flexible enough for most cases
- Sections can be marked as "N/A" if not applicable
- Template evolves based on feedback

## Implementation

### Template Location

- Template file: `/docs/_template.md`
- All architectures reference the template
- Template includes examples and guidance

### Review Process

- All new architectures must follow the template
- Existing architectures updated to match template
- Template reviewed and updated periodically

## Related Documents

- [Architecture Template](../docs/_template.md)
- [Reference Architectures Index](../docs/index.md)

---

**Date**: 2024  
**Deciders**: Icarus Nova Architecture Team  
**Status**: Accepted
