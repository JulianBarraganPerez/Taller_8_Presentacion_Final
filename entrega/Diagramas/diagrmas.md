# Diagramas Mermaid — Bray Controls Andina

## 1. Mapa General de Arquitectura Empresarial

```mermaid
flowchart TB
    Negocio[Procesos de Negocio]
    Datos[Datos e Información]
    Apps[Aplicaciones]
    Tech[Infraestructura]
    Gov[Gobierno TI]

    Negocio --> Datos
    Datos --> Apps
    Apps --> Tech

    Gov --> Negocio
    Gov --> Datos
    Gov --> Apps
    Gov --> Tech

    Houston[Houston Corporativo]
    Houston --> Apps
    Houston --> Tech
```

## 2. Arquitectura AS-IS

```mermaid
flowchart LR
    Cliente --> Ventas
    Ventas --> Outlook
    Ventas --> Excel
    Outlook --> ERP[ERP LN]
    Excel --> ERP

    ERP --> Facturacion[Facturación Electrónica]
    ERP --> OrderTrack[Order Track]

    Houston --> ERP
    Houston --> Azure
```

## 3. Arquitectura TO-BE


```mermaid
flowchart LR
    Cliente --> Dynamics[Dynamics 365]
    Dynamics --> LN[ERP LN]

    LN --> Facturacion[Facturación Electrónica]
    LN --> OrderTrack[Order Track]
    LN --> PowerBI[Power BI]

    MFA[MFA]
    SLA[SLA Houston]
    Gov[Gobierno TI]

    Gov --> LN
    Gov --> MFA
    Houston --> LN

---

## 4. BPMN AS-IS

```mermaid
flowchart TD
    A[Cliente solicita cotización]
    B[Ventas externas]
    C[Ventas internas]
    D[Correo Outlook]
    E[Excel Reorder Point]
    F[ERP LN]
    G[Bodega]
    H[Facturación]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
```

## 5. BPMN TO-BE

```mermaid
flowchart TD
    A[Cliente solicita cotización]
    B[Dynamics 365]
    C[ERP LN]
    D{¿Hay stock?}
    E[Picking y despacho]
    F[Purchase Order]
    G[Recepción inventario]
    H[Facturación electrónica]

    A --> B
    B --> C
    C --> D

    D -- Sí --> E
    D -- No --> F

    F --> G
    G --> E
    E --> H
```

## 6. ERD Simplificado

```mermaid
erDiagram
    CLIENTE ||--o{ COTIZACION : genera
    COTIZACION ||--|{ SALES_ORDER : convierte
    SALES_ORDER ||--o{ PURCHASE_ORDER : crea
    SALES_ORDER ||--o{ FACTURA : produce
    INVENTARIO ||--o{ SALES_ORDER : abastece
    BODEGA ||--o{ INVENTARIO : contiene
```

## 7. Flujo de Datos

```mermaid
flowchart LR
    Dynamics[Dynamics 365]
    LN[ERP LN]
    Facturacion[Facturación]
    PowerBI[Power BI]
    OrderTrack[Order Track]

    Dynamics --> LN
    LN --> Facturacion
    LN --> PowerBI
    LN --> OrderTrack
```

## 8. Diagrama de Integraciones

```mermaid
flowchart TB
    Dynamics[Dynamics CRM]
    LN[ERP LN]
    FE[Facturación Electrónica]
    OT[Order Track]
    BI[Power BI]

    Dynamics --> LN
    LN --> FE
    LN --> OT
    LN --> BI
```

## 9. Infraestructura Tecnológica

```mermaid
flowchart TB
    subgraph Colombia
        Bogota[Bogotá]
        Cali[Cali]
        Barranquilla[Barranquilla]
    end

    subgraph Corporativo
        Houston[Houston]
        Azure[Azure Cloud]
    end

    Bogota --> Azure
    Cali --> Azure
    Barranquilla --> Azure
    Houston --> Azure
```

## 10. Gobierno TI

```mermaid
flowchart TD
    Gerencia --> DirectorTI[Director Técnico]
    DirectorTI --> HoustonIT[IT Houston]
    DirectorTI --> Contratista[Soporte Local]
    DirectorTI --> Datos[Responsable Datos]
```

## 11. Gestión de Incidentes

```mermaid
flowchart TD
    A[Usuario reporta incidente]
    B[Director Técnico evalúa]
    C{Nivel de severidad}
    D[Escalar a Houston]
    E[Resolver localmente]
    F[Documentar incidente]

    A --> B
    B --> C

    C -- Alto/Crítico --> D
    C -- Medio/Bajo --> E

    D --> F
    E --> F
```

## 12. Matriz STRIDE

```mermaid
flowchart LR
    S[Spoofing]
    T[Tampering]
    R[Repudiation]
    I[Information Disclosure]
    D[Denial of Service]
    E[Elevation of Privilege]

    S --> ERP
    T --> Datos
    R --> Logs
    I --> Clientes
    D --> Operación
    E --> Accesos
```

## 13. Roadmap de Transformación

```mermaid
gantt
    title Roadmap Bray Controls Andina
    dateFormat YYYY-MM-DD

    section Fase 1
    Plan contingencia :a1, 2026-01-01, 30d
    SLA Houston :a2, 2026-01-10, 30d
    Política SMI :a3, 2026-01-15, 20d

    section Fase 2
    Integración facturación :b1, 2026-03-01, 60d
    Migración Reorder Point :b2, 2026-03-15, 60d
    MFA :b3, 2026-04-01, 45d

    section Fase 3
    Dashboards Power BI :c1, 2026-06-01, 60d
    Gobierno TI :c2, 2026-06-15, 60d
```

## 14. Heatmap de Riesgos

```mermaid
quadrantChart
    title Riesgos Bray Controls Andina
    x-axis Bajo Impacto --> Alto Impacto
    y-axis Baja Probabilidad --> Alta Probabilidad
    quadrant-1 Monitorear
    quadrant-2 Riesgo Alto
    quadrant-3 Riesgo Bajo
    quadrant-4 Mitigación Prioritaria

    DependenciaHouston: [0.9, 0.9]
    ReorderPoint: [0.8, 0.8]
    SMI: [0.7, 0.6]
    FacturacionManual: [0.6, 0.7]
```

## 15. Dependencias Críticas

```mermaid
flowchart LR
    Houston --> ERP
    ERP --> Inventario
    ERP --> Facturacion
    ERP --> OrderTrack
    ReorderPoint --> ERP
    Excel --> ReorderPoint
```

## 16. Single Source of Truth

```mermaid
flowchart TD
    Clientes --> Dynamics
    Cotizaciones --> Dynamics
    Inventario --> LN
    Facturas --> Facturacion
    Reportes --> PowerBI
```

## 17. Gestión Alta/Baja de Usuarios

```mermaid
flowchart TD
    A[RRHH notifica]
    B[Director Técnico]
    C[Ticket Houston]
    D[Creación/Desactivación]
    E[Configuración local]

    A --> B
    B --> C
    C --> D
    D --> E
```

## 18. Continuidad Operativa

```mermaid
flowchart TD
    A[Caída ERP]
    B[Activar plan contingencia]
    C[Operación manual mínima]
    D[Escalar a Houston]
    E[Recuperación servicios]

    A --> B
    B --> C
    C --> D
    D --> E
```

## 19. KPI Dashboard Ejecutivo

```mermaid
pie title Estado Objetivos TO-BE
    "Integración completada" : 40
    "Procesos manuales" : 25
    "Gobierno TI" : 15
    "Seguridad" : 20
```

## 20. Capa Informal de Operación

```mermaid
flowchart LR
    Outlook[Correos Outlook]
    Excel[Excel]
    Personas[Usuarios]
    ERP[ERP LN]
    Dynamics[Dynamics]

    Dynamics --> Outlook
    Outlook --> Personas
    Personas --> Excel
    Excel --> ERP

```


