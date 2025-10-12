# 🧪 Lab03 — Simulación SCADA con Winlog Lite y WinSim64

**Módulo:** Fundamentals of OT Cybersecurity — Sección 3: *SCADA Systems*  
**Autora:** Victoria García Rodríguez  
**Repositorio:** [OT-Cybersecurity-Labs](https://github.com/cosiata01/OT-Cybersecurity-Labs)  
**Ubicación:** `/01-Fundamentals-OT/05-OT-Protocols/lab03_winloglite_winsim64/`  
**Estado:** ✅ Finalizado  

---

## 🎯 Objetivo del laboratorio

Implementar una **simulación funcional de un sistema SCADA** utilizando **Winlog Lite** como plataforma de supervisión y **WinSim64** como simulador de PLC, estableciendo comunicación a través del protocolo **Modbus TCP**.

El propósito es comprender cómo un sistema SCADA se comunica con un PLC para:
- Leer y visualizar datos de proceso (*Input Registers*).  
- Controlar señales de campo (*Coils*) mediante la interfaz HMI.  

---

## 🏗️ Entorno de laboratorio

| Componente | Rol | Sistema operativo | Herramienta | Función |
|-------------|-----|-------------------|--------------|----------|
| VM1 | Estación SCADA (HMI) | Windows 10 | **Winlog Lite** | Interfaz HMI y supervisión de datos |
| VM2 | PLC simulado | Windows 10 | **WinSim64** | Simulador de dispositivo Modbus TCP |
| Red | Host-Only | Subred `192.168.143.0/24` | Comunicación TCP en puerto 502 |

---

## ⚙️ Pasos realizados

1️⃣ **Configuración del entorno**
- Instalación de **Winlog Lite** y **WinSim64** en máquinas Windows 10.  
- Configuración de la red *Host-Only* con IPs estáticas:
  - SCADA (HMI): `192.168.143.10`  
  - PLC simulado: `192.168.143.20`  

2️⃣ **Creación del proyecto SCADA**
- Se creó un proyecto nuevo en **Winlog Lite** usando una **plantilla base**.  
- Se configuró el driver de comunicación **Modbus TCP/IP Client**.  
- Dirección IP del servidor Modbus: `192.168.143.20`.

3️⃣ **Configuración de etiquetas (tags)**
- 🟢 **Tag 1:** *Coil — Encendido/Apagado*  
  - Tipo: `Coil (0x)`  
  - Función: Control manual desde HMI.  
- ⚙️ **Tag 2:** *Input Register — Lectura de presión*  
  - Tipo: `Input Register (3x)`  
  - Función: Lectura continua desde el simulador WinSim64.  

4️⃣ **Simulación y prueba**
- En **WinSim64** se activaron las variables correspondientes.  
- En **Winlog Lite**, las etiquetas mostraron cambios en tiempo real.  
- Se verificó comunicación estable y actualización visual instantánea en la interfaz HMI.  

---

## 📊 Resultados y observaciones

✅ Comunicación exitosa entre SCADA (cliente Modbus) y PLC simulado (servidor).  
✅ Visualización en tiempo real de variables industriales.  
✅ Control de una coil y lectura de un registro analógico funcionando correctamente.  

💡 Este laboratorio representa una **simulación completa del flujo OT**:  
PLC → Datos de campo → Comunicación Modbus TCP → SCADA (Winlog Lite).  

---

## 🎥 Evidencia en video

> 🔗 **Video del laboratorio:** *https://www.youtube.com/watch?v=LcMEE81f7BE*  
>  
> 📺 **Título:**  
> `Lab03 — Simulación SCADA con Winlog Lite y WinSim64 (Modbus TCP)`  
---
