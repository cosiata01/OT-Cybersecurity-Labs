# 🧪 Lab01 — Simulación de comunicación Modbus TCP (HMI ↔ PLC)

**Módulo:** Fundamentals of OT Cybersecurity — Sección 5: *OT Protocols & Communications*  
**Autora:** Victoria García Rodríguez  
**Repositorio:** [OT-Cybersecurity-Labs](https://github.com/cosiata01/OT-Cybersecurity-Labs)  
**Ubicación:** `/01-Fundamentals-OT/05-OT-Protocols/lab01_modbus_vm_setup/`  
**Estado:** 🧩 En desarrollo  

---

## 🎯 Objetivo del laboratorio

Simular la comunicación industrial **Modbus TCP** entre dos máquinas virtuales Windows 10, representando:

| Rol | Descripción | Herramienta utilizada |
|------|--------------|-----------------------|
| 🖥️ HMI (Maestra / Cliente Modbus) | Envía peticiones de lectura y escritura a registros del PLC | **ModScan** |
| ⚙️ PLC (Esclavo / Servidor Modbus) | Responde solicitudes y mantiene los registros Modbus simulados | **ModSim** |

El propósito es **observar y comprender el flujo de datos Modbus TCP** en un entorno controlado, verificando la interacción entre el cliente (HMI) y el servidor (PLC).

---

## 🏗️ Entorno de laboratorio

| Componente | Rol | Sistema Operativo | IP asignada | Herramienta principal |
|-------------|-----|-------------------|--------------|------------------------|
| VM1 | HMI (Cliente / Maestra) | Windows 10 | `192.168.143.10` | ModScan |
| VM2 | PLC (Servidor / Esclava) | Windows 10 | `192.168.143.20` | ModSim |
| Red | Host-Only | Sin acceso a Internet | Subred `192.168.143.0/24` | Comunicación TCP en puerto 502 |

---

## ⚙️ Pasos realizados

1️⃣ **Configuración de red**
- Se creó una red *Host-Only* en VirtualBox para ambas máquinas.  
- Se asignaron IPs estáticas:
  - HMI → `192.168.143.10`  
  - PLC → `192.168.143.20`  
- Se comprobó conectividad básica con `ping`.

2️⃣ **Instalación y ejecución de herramientas**
- En la máquina **PLC** (esclava): instalación y ejecución de **ModSim** (servidor Modbus TCP).  
- En la máquina **HMI** (maestra): instalación y ejecución de **ModScan** (cliente Modbus TCP).  

3️⃣ **Prueba de comunicación**
- Desde ModScan (HMI), se configuró la conexión TCP al servidor ModSim (`192.168.143.20:502`).  
- Se visualizaron correctamente los registros Modbus leídos/escritos en tiempo real.  

---

## 📊 Resultados y observaciones

✅ Comunicación estable entre ambas VMs.  
✅ Respuesta correcta a lecturas y escrituras Modbus.  
💡 Se confirmó el comportamiento típico del protocolo:  
   - Peticiones *Read Holding Registers (0x03)*.  
   - Respuestas del servidor con los valores simulados.  

---

## 🎥 Evidencia en video

> 🔗 **Video del laboratorio:** https://youtu.be/TT2ecsnqckk  
---
