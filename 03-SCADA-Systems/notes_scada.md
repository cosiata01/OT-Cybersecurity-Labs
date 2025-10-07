# Sección 3 — Supervisory Control and Data Acquisition (SCADA)

**Definición breve:**  
SCADA es un sistema de supervisión y adquisición de datos para monitorizar y controlar procesos distribuidos (plantas, redes eléctricas, agua, transporte). Su objetivo es recopilar datos de campo, mostrar estado a operadores y permitir envío de comandos cuando sea necesario.

## Componentes principales
- **HMI:** Interfaz de operadores para visualización y control.  
- **SCADA Server / MTU (Master Terminal Unit):** Unidad central que recopila datos, almacena historiales y coordina órdenes.  
- **RTU / PLC / PAC / IED:** Dispositivos de campo que leen sensores y accionan actuadores.  
- **Data Historian:** Base de datos de tiempos históricos (trazas, tendencias, alarmas).  
- **Engineering Workstation:** Estación para programación y mantenimiento.

## SCADA vs DCS (resumen)
- **SCADA:** orientado a monitorización y control distribuido en áreas geográficamente separadas; tolera latencia; suele trabajar con RTUs y conexiones no siempre constantes.  
- **DCS:** sistema de control más integrado dentro de una sola planta/proceso, con control distribuido de bucle cerrado y comunicaciones de baja latencia.

## Alarmas
- Las alarmas se configuran por condiciones críticas (no todos los eventos son alarma).  
- Ciclo: detección → clasificación → notificación (email/SMS) → respuesta → cierre.  
- Importante diseñar prioridades y procedimientos para evitar "alarm floods".

## Conectividad y comportamiento off-line
- Puede usar VSAT, radio, celulares o fibra.  
- Modelos store-and-forward: si se pierde conexión, el MTU/RTU puede almacenar eventos y sincronizar cuando vuelve la conexión.

## Consideraciones de seguridad (breve)
- Segmentar la red (DMZ, firewalls) y limitar accesos remotos.  
- Hardenizar servidores MTU/HMI y controlar el acceso a Engineering Workstations.  
- Monitorizar tráfico industrial (Wireshark, Zeek) y capturar protocolos (Modbus, OPC-UA, DNP3).  
- Planificar patches y pruebas cuidadosamente (no aplicar cambios sin testing en OT).

**Última actualización:** 07 Octubre 2025
