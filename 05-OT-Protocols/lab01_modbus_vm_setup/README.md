# 🧪 Lab01 — Simulación Modbus HMI ↔ PLC
**Módulo:** Fundamentals of OT Cybersecurity — *Sección 5: OT Protocols & Communications*
**Autora:** Victoria García Rodríguez
**Repositorio:** [OT-Cybersecurity-Labs](https://github.com/cosiata01/OT-Cybersecurity-Labs)
**Ubicación:** `/01-Fundamentals-OT/05-OT-Protocols/lab01_modbus_vm_setup/`
**Estado:** 🧩 En desarrollo

---

## 🎯 Objetivo del laboratorio
Simular la comunicación industrial **Modbus TCP** entre dos máquinas virtuales, representando:

- 🖥️ **HMI (Human-Machine Interface)** → cliente Modbus
- ⚙️ **PLC (Programmable Logic Controller)** → servidor Modbus

El propósito es observar el **flujo de datos y registros Modbus** (lectura y escritura) en un entorno controlado.

---

## 🏗️ Entorno de laboratorio
| Componente | Rol | Sistema operativo | Herramienta principal |
|------------|-----|-----------------|--------------------|
| VM1        | HMI (cliente) | Ubuntu / Debian | `modbus-cli`, `QModMaster`, o `ScadaBR` |
| VM2        | PLC (servidor) | Ubuntu / Debian / Windows | `ModbusPal`, `OpenPLC`, o `ModRSsim2` |
| Red        | Interna / Host-Only | IP fija | Comunicación TCP en puerto 502 |

---

## ⚙️ Pasos generales

### 1️⃣ Configurar la red virtual
- Crear una red **Host-Only** o **Interna** (sin acceso a Internet).
- Asignar IPs estáticas a ambas VMs (por ejemplo):
    - HMI → `192.168.56.10`
    - PLC → `192.168.56.11`

### 2️⃣ Instalar las herramientas
- En la VM del PLC: instalar y ejecutar **ModbusPal** (Java) o **OpenPLC** como servidor Modbus.
- En la VM del HMI: instalar **QModMaster** o **modbus-cli** para enviar solicitudes.

### 3️⃣ Probar la conectividad
```bash
ping 192.168.56.11
