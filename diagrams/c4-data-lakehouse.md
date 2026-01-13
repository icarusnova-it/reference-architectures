# C4 – Data Platform (Lakehouse)

> **Icarus Nova** | High-level container diagram for data platform lakehouse architecture.

## System Context

```mermaid
C4Context
    title System Context - Data Platform Lakehouse
    
    Person(analyst, "Data Analysts", "Analyzing data")
    Person(scientist, "Data Scientists", "Building ML models")
    Person(admin, "Data Administrators", "Managing data platform")
    
    System(platform, "Data Platform Lakehouse", "Modern data platform combining data lake and warehouse")
    
    System_Ext(sources, "Data Sources", "External data sources")
    
    Rel(analyst, platform, "Queries Data")
    Rel(scientist, platform, "Trains Models")
    Rel(admin, platform, "Manages")
    Rel(sources, platform, "Ingests Data")
    
    UpdateElementStyle(analyst, $bgColor="#e1f5ff")
    UpdateElementStyle(scientist, $bgColor="#e1f5ff")
    UpdateElementStyle(admin, $bgColor="#e1f5ff")
    UpdateElementStyle(platform, $bgColor="#90EE90")
```

## Container Diagram

```mermaid
C4Container
    title Container Diagram - Data Platform Lakehouse
    
    Person(analyst, "Data Analysts")
    Person(scientist, "Data Scientists")
    Person(admin, "Data Administrators")
    
    System_Boundary(platform, "Data Platform Lakehouse") {
        Container(ingestion, "Ingestion Layer", "Ingestion Services", "Multi-source data ingestion")
        Container(storage, "Storage Layer", "Data Lake", "Data lake storage (S3, ADLS)")
        Container(processing, "Processing Layer", "Processing Services", "ETL/ELT processing")
        Container(warehouse, "Warehouse Layer", "Data Warehouse", "Data warehouse for analytics")
        Container(analytics, "Analytics Layer", "Analytics Tools", "Analytics and BI tools")
        Container(governance, "Governance Layer", "Governance Services", "Data catalog, lineage, quality")
        Container(access, "Access Layer", "Access APIs", "Unified data access APIs")
    }
    
    System_Ext(sources, "Data Sources", "External data sources")
    
    Rel(sources, ingestion, "Ingests")
    Rel(ingestion, storage, "Stores")
    Rel(storage, processing, "Processes")
    Rel(processing, warehouse, "Loads")
    Rel(warehouse, analytics, "Queries")
    Rel(analyst, access, "Queries")
    Rel(scientist, access, "Accesses Data")
    Rel(admin, governance, "Manages")
    Rel(governance, storage, "Catalogs")
    Rel(governance, warehouse, "Catalogs")
    
    UpdateElementStyle(ingestion, $bgColor="#87CEEB")
    UpdateElementStyle(storage, $bgColor="#DDA0DD")
    UpdateElementStyle(processing, $bgColor="#90EE90")
    UpdateElementStyle(warehouse, $bgColor="#DDA0DD")
    UpdateElementStyle(analytics, $bgColor="#FFE4B5")
    UpdateElementStyle(governance, $bgColor="#F0E68C")
    UpdateElementStyle(access, $bgColor="#E6E6FA")
```

## Key Interactions

### Data Flow

1. **Data Ingestion**: Ingestion layer ingests data from multiple sources
2. **Data Storage**: Data stored in data lake (raw data)
3. **Data Processing**: Processing layer transforms data (ETL/ELT)
4. **Data Warehouse**: Processed data loaded into data warehouse
5. **Data Analytics**: Analytics tools query data warehouse
6. **Data Governance**: Governance layer catalogs and tracks data lineage
7. **Data Access**: Access layer provides unified data access

## Related Documents

- [Data Platform Lakehouse Architecture](../docs/data-platform-lakehouse.md)
- [Reference Architectures Index](../docs/index.md)

---

**Last Updated:** 2024  
**Maintained by:** Icarus Nova Architecture Team  
**Version:** 1.0
