# 📄 Resumen Ejecutivo del Proyecto Arquitectónico

**Equipo:** ARQTEAM-05  
**Integrantes:** Julián Andrés Barragán Pérez · Juan David González Rubio · Josue David Sarmiento Guarnizo  
**Cliente:** Bray Controls Andina Ltda  
**Curso:** Arquitectura Empresarial — Universidad de La Sabana  
**Fecha:** 2026

---

## 🏢 Nombre del Cliente

**Bray Controls Andina Ltda** — Subsidiaria comercial de Bray International en Colombia, con operación en Colombia, Ecuador y Venezuela. Dedicada a la comercialización B2B de válvulas, actuadores y sistemas de automatización industrial para sectores de petróleo y gas, energía, manufactura y tratamiento de agua. 45 empleados, tres bodegas activas (Bogotá, Cali, Barranquilla), gestión tecnológica centralizada en Houston, Estados Unidos.

---

## 🎯 Objetivo General del Proyecto

El proyecto tuvo como propósito realizar un análisis integral de arquitectura empresarial de Bray Controls Andina siguiendo el marco metodológico TOGAF ADM, identificando el estado actual (AS-IS) de la organización en sus cuatro capas fundamentales (negocio, datos, aplicaciones y tecnología), documentando las brechas críticas frente a buenas prácticas y proponiendo una arquitectura objetivo (TO-BE) con un roadmap de transformación priorizado.

El reto central no era tecnológico sino estructural: la empresa tiene herramientas sólidas pero no integradas, procesos que funcionan pero no están documentados, y controles de seguridad robustos que el personal local no puede ver ni auditar. En palabras de la coordinadora de Operaciones durante las entrevistas:

> *"Me encantaría poder tener algo donde yo tenga todo en el mismo sistema. Tanto correo para dar una vaina de una orden. Lo que cambiaría es integrarlo."*

---

## 🧱 Vistas Arquitectónicas Cubiertas

| Vista | Entregable | Alcance de la solución |
|-------|-----------|----------------------|
| **Procesos de Negocio** | Taller 1 — Modelado BPMN | Proceso de cotización y pedido industrial: desde la solicitud del cliente hasta la facturación. Actores: cliente, ventas externas, ventas internas, operaciones y finanzas. |
| **Información / Datos** | Taller 2 — ERD y diagrama de contexto | Modelo lógico de datos con 12 entidades principales. Flujo completo: cotización → pedido → orden de compra → inventario → remisión → factura. Tres bodegas modeladas. |
| **Aplicaciones / Sistemas** | Taller 5 — Arquitectura de infraestructura | Ecosistema de cinco sistemas: ERP LN (Infor), Dynamics 365, Azure, facturación electrónica y Order Track. Integraciones activas y pendientes documentadas. |
| **Seguridad** | Taller 4 — Análisis STRIDE | Ocho amenazas analizadas. Incidente real de 2022 (ataque cibernético, una semana sin sistemas) documentado como riesgo históricamente confirmado. |
| **Cumplimiento Normativo** | Taller 3 — Evaluación de cumplimiento | Checklist de 20 criterios. Normativas evaluadas: Ley 1581, ISO 9001, SARLAFT, Resolución 0312. |
| **Análisis de Riesgos** | Guía metodológica — Matriz de riesgos | 15 riesgos identificados y priorizados por dominio (negocio, procesos, datos, aplicaciones, infraestructura, gobierno TI). |
| **Arquitectura Objetivo** | TO-BE | Propuesta de integración de sistemas, automatización de Reorder Point, plan de contingencia local y gobierno de TI. |
| **Hoja de Ruta** | Roadmap | 18 iniciativas en tres fases a 12 meses. Fase 1: sin cambios tecnológicos. Fase 2: integraciones con Houston. Fase 3: gobierno y escalabilidad. |
| **Integración de Vistas** | Taller 7 — Tablero integrado | Todas las capas conectadas en un tablero único que evidencia la dependencia de Houston como punto de control transversal y la "capa informal" de Excel y correos. |

---

## 🧩 Hallazgos Clave

**Hallazgo 1 — El problema no es tecnológico, es de arquitectura y gobierno.**  
Bray Controls Andina tiene infraestructura sólida (Azure, ERP LN, Dynamics 365), pero sus sistemas no están integrados entre sí. La brecha no está en las herramientas sino en que nadie completó las integraciones ni definió quién toma decisiones tecnológicas a nivel local.

**Hallazgo 2 — Existe un incidente de seguridad real no gestionado localmente.**  
En 2022, un ataque cibernético dejó a la empresa sin acceso a sistemas durante una semana completa. La respuesta fue gestionada 100% desde Houston. No existe plan de contingencia local ni protocolo documentado. Los riesgos del análisis STRIDE pasaron de teóricos a históricamente confirmados.

**Hallazgo 3 — Una sola persona sostiene el proceso más crítico de inventario.**  
El Reorder Point — que determina cuándo y cuánto se compra — lo define y carga manualmente una sola persona en un archivo Excel sin integración al ERP LN. Si esa persona no está disponible, la planeación de compras se detiene.

**Hallazgo 4 — El SMI representa un riesgo financiero activo de ~$4M USD.**  
Aproximadamente el 30% del inventario total corresponde a Slow Moving Inventory sin política formal de disposición, con capital inmovilizado indefinidamente.

**Hallazgo 5 — La fragmentación tecnológica crea una "capa informal" de operación.**  
Excel y correos de Outlook actúan como integradores humanos entre sistemas que deberían estar conectados automáticamente. Esta capa no aparece en ningún diagrama oficial, pero es la que sostiene la operación diaria.

---

## 🚀 Recomendaciones Principales

**Inmediatas (0-3 meses, sin cambios tecnológicos):**
- Documentar el plan de contingencia local ante caída del ERP, con roles y tiempos de respuesta.
- Documentar el proceso de Reorder Point y capacitar a un segundo responsable.
- Designar un responsable local de protección de datos (cumplimiento Ley 1581).
- Acordar SLA formal de respuesta con IT corporativo de Houston.

**Mediano plazo (3-6 meses, coordinación con Houston):**
- Completar la integración pendiente entre ERP LN y sistema de facturación electrónica.
- Migrar el Reorder Point del Excel al ERP LN.
- Activar Order Track en todas las áreas (kickoff ya programado).
- Implementar MFA en todas las cuentas corporativas.

**Largo plazo (6-12 meses):**
- Establecer gobierno de TI local con roles, procesos y SLA formalizados.
- Ampliar dashboards Power BI para visibilidad de inventario y SMI.
- Extender el modelo a Bray Ecuador (subsidiaria ya constituida).

---

## 📊 Estado de los entregables

| Entregable | Estado |
|-----------|--------|
| Ficha de caracterización del cliente | ✅ Completado |
| Modelado de procesos AS-IS (BPMN) | ✅ Completado |
| Modelo de información y ERD | ✅ Completado |
| Evaluación de cumplimiento normativo + checklist | ✅ Completado |
| Análisis de seguridad STRIDE + Excel | ✅ Completado |
| Análisis de arquitectura de infraestructura | ✅ Completado |
| Análisis de riesgos empresariales | ✅ Completado |
| Arquitectura TO-BE | ✅ Completado |
| Roadmap de transformación | ✅ Completado |
| Plan de gobierno de TI local | ✅ Completado |
| Integración de vistas (Taller 7) | ✅ Completado |

---

## 💡 Reflexión Final

Este proyecto demostró que la arquitectura empresarial es una disciplina de síntesis, no solo de análisis. Bray Controls Andina tiene equipos capaces, sistemas sólidos y procesos que funcionan — pero sin una visión arquitectónica que los conecte, opera por debajo de su potencial y con riesgos que no ve.

El mayor aprendizaje del equipo fue que los problemas más importantes de una organización no aparecen en un solo diagrama. Aparecen cuando se ponen todos los diagramas juntos y se observan las inconsistencias entre ellos. La "capa informal" de Excel y correos que descubrimos al integrar las vistas no estaba en ningún entregable individual — solo fue visible cuando vimos todo al tiempo.

La solución que proponemos no requiere una transformación radical. Requiere completar lo que está a medio hacer, documentar lo que ya existe y establecer el gobierno local que le permita a Bray Controls Andina tomar decisiones tecnológicas con autonomía y criterio.

---

*Este resumen ejecutivo forma parte de la entrega final del Taller 8 del curso AREM — Arquitectura Empresarial — Universidad de La Sabana.*
