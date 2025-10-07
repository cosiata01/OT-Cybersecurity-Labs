# Sección 4 — Operational Technology (OT) vs Information Technology (IT)

## ¿Qué es OT?
OT = hardware y software que detectan, controlan o automatizan procesos físicos: SCADA, DCS, PLC, RTU, SIS, y sistemas ciberfísicos (BMS, transporte, salud).

## Términos relacionados
- **ICS / IACS:** Industrial Control Systems / Industrial Automation and Control Systems — engloba SCADA y DCS.  
- **SIS:** Safety Instrumented System — sistema de seguridad que actúa para evitar condiciones peligrosas.  
- **Cyber-Physical Systems:** sistemas que integran componentes físicos y software de control.

## Diferencias clave (tabla breve)

| Aspecto | IT | OT |
|---|---:|---:|
| Prioridad | Confidencialidad | Seguridad operativa / Disponibilidad |
| Parches / Actualizaciones | Frecuentes | Limitadas; pruebas offline necesarias |
| Cifrado | Uso habitual | Poco usado (impacto en latencia) |
| Pen-testing | Rutinario | Riesgoso; planificado y con controles |
| Efecto de fallos | Pérdida de datos | Interrupción de producción / daños físicos |
| Legacy | Menos | Mucho hardware legacy en producción |
| Objetivo de seguridad | CIA (Confidencialidad primero) | Disponibilidad y seguridad operativa primero |

## Modelo Purdue (recordatorio)
- **Nivel 0:** Dispositivos de campo (sensores, actuadores)  
- **Nivel 1:** Controladores (PLC, RTU, DCS controllers)  
- **Nivel 2:** Supervisión (HMI, SCADA, estaciones)  
- **Nivel 3:** MES (Manufacturing Execution System)  
- **Nivel 4:** ERP (Enterprise Resource Planning)  
- **Nivel 5:** Red corporativa / servicios IT

**Zonas y medidas:** DMZ para la convergencia IT↔OT; segmentación entre niveles; microsegmentación para aislar dispositivos críticos.

## Air-gapped: ¿es suficiente?
- El aislamiento físico ayuda, pero no garantiza seguridad: vectores comunes incluyen USB infectados, phishing a ingenieros, acceso remoto mal gestionado.  
- Tras la pandemia, la necesidad de acceso remoto aumentó los riesgos en OT.

## Conclusión breve
OT y IT persiguen objetivos distintos y requieren políticas y controles diferentes. Para proteger OT es imprescindible: segmentación, control de accesos, monitoreo continuo, y procedimientos de parcheo/actualización específicos.

**Última actualización:** 07 Octubre 2025
