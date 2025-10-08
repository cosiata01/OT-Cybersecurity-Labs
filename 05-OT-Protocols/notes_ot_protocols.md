# 🧩 Section 5 — OT Protocols & Communications  
**Curso:** Fundamentals of OT (ICS/SCADA) Cybersecurity  
**Autora:** Victoria García Rodríguez  
**Repositorio:** [OT-Cybersecurity-Labs](https://github.com/cosiata01/OT-Cybersecurity-Labs)  
**Ubicación:** `/01-Fundamentals-OT/05-OT-Protocols/notes_ot_protocols.md`  
**Estado:** ✅ Completo  

---

## 📘 Recapitulación: Sensores

Existen dos tipos principales de sensores utilizados en entornos OT:

### 1️⃣ Sensores digitales  
- Generan **valores discretos** (binarios): 0 o 1 lógico (encendido/apagado).  
- Su salida se representa como un **bit** si la transmisión es serial.  
- Son **no continuos**, por ejemplo: un interruptor o un detector de presencia.

### 2️⃣ Sensores analógicos  
- Producen una **señal continua** (voltaje o corriente variable).  
- Representan magnitudes físicas que cambian suavemente con el tiempo, como:
  - Temperatura 🌡️  
  - Velocidad ⚙️  
  - Presión  
  - Desplazamiento o deformación  
- Su salida cambia de forma gradual y continua.

---

## 📊 Lectura o supervisión de valores

La **lectura o supervisión** proviene de los **dispositivos de entrada** (discretos o analógicos).  
Cada valor leído se denomina **etiqueta** (*tag*).



- El **sensor** mide la temperatura.  
- El **PLC** convierte la señal en bits.  
- El **HMI** recibe y muestra el valor.  
- Si el operador realiza una acción (p. ej. cambiar un setpoint), el HMI envía una orden al PLC a través de un **protocolo OT**.

---

## 🧭 Escritura de valores

Supongamos que el HMI solicita al PLC reducir una variable, como el nivel de agua.  
El flujo sería:


- El HMI envía la orden en bits.  
- El PLC, mediante su **lógica de control**, traduce y ejecuta la acción.  
- El actuador responde físicamente (por ejemplo, cerrando una válvula).  

La lógica del PLC define cómo actuar, mientras que el HMI solo envía comandos simples.

---

## ⚙️ Protocolos industriales (OT Protocols)

Los **protocolos OT** son los lenguajes que permiten la comunicación entre sensores, PLCs, HMIs, SCADAs y otros dispositivos industriales.

> ⚠️ Muchos fueron diseñados **sin seguridad integrada** (sin autenticación, cifrado ni control de acceso), lo que los hace *inseguros por diseño*.

### 🔧 Tipos de protocolos según la industria

| Categoría | Protocolos comunes |
|------------|--------------------|
| Automatización de procesos | CIP, Modbus, DNP3, Ethernet/IP, HART, PROFINET, GE SRTP |
| Control de sistemas industriales | OPC, OPC UA, OMG DDS, MTConnect, Modbus |
| Gestión de sistemas | BCnet, LonTalk, Modbus, ZigBee |
| Automatización eléctrica | DNP3, IEC 60870-5, IEC 61850, ICCP |
| Lectura automática de medidores | IEC 61107, ZigBee, Modbus |
| Industria automotriz | CAN, FlexRay, LIN |

Algunos son **abiertos**, otros son **propietarios** (cerrados, de un fabricante específico).

Los estándares son definidos por organismos como el **IETF**, responsables de publicar las especificaciones técnicas (RFC – *Request for Comments*).

---

## 🔐 Seguridad en los protocolos OT

En general, estos protocolos **no incluyen mecanismos nativos** de:
- Autenticación  
- Autorización  
- Encriptación  

Esto implica que deben protegerse mediante **segmentación de red**, **VPNs**, **firewalls industriales**, y **monitoreo pasivo**.

---

## 🔌 Introducción a Modbus

### 🏗️ Origen
- Diseñado en **1979** por **Modicon** (hoy parte de Schneider Electric).  
- Es un **estándar abierto** ampliamente adoptado y mantenido por la **Modbus Organization**.  

### 💡 Propósito
Permite la **comunicación eficiente** entre dispositivos industriales bajo un modelo **maestro-esclavo** (en RTU) o **cliente-servidor** (en TCP).

### 📡 Capa OSI
Opera en la **capa 7 – Aplicación** del modelo OSI.  
Usa tres tipos de mensajes principales (*Protocol Data Units – PDUs*):
1. **Solicitud Modbus** (*Request*)  
2. **Respuesta Modbus** (*Response*)  
3. **Respuesta de excepción** (*Exception Response*)

---

## 🔁 Tipos de comunicación Modbus

### 🧩 Modbus RTU (antiguo)
- Comunicación **serial** (RS-232, RS-422, RS-485).  
- Formatos: **ASCII** (antiguo) y **RTU** (moderno).  
- Modelo **maestro–esclavo**:
  - Maestro → HMI  
  - Esclavo → PLC  
- Limitado en velocidad y distancia.

### 🌐 Modbus TCP (moderno)
- Comunicación mediante **Ethernet** y **TCP/IP**.  
- Modelo **cliente–servidor**:
  - Cliente → HMI  
  - Servidor → PLC  
- Usa el **puerto TCP 502**.  
- Maneja errores a nivel TCP, sin necesidad del chequeo CRC de RTU.

> ⚠️ Los modelos **RTU y TCP son incompatibles**.  
> Un dispositivo que hable RTU no puede comunicarse directamente con otro que use TCP/IP.

---

## 🧮 Direccionamiento de memoria en Modbus

Cada dato en un PLC Modbus se guarda en una **dirección de memoria**, agrupada en bloques de **16 bits (2 bytes)** llamados *registros*.

| Tipo de dato | Rango típico | Tamaño | Descripción | Acceso |
|---------------|--------------|---------|--------------|---------|
| **Coils (Bobinas)** | 00001–09999 | 1 bit | Salidas digitales (ON/OFF) | Lectura y escritura |
| **Discrete Inputs** | 10001–19999 | 1 bit | Entradas de sensores | Solo lectura |
| **Input Registers** | 30001–39999 | 16 bits | Entradas analógicas | Solo lectura |
| **Holding Registers** | 40001–49999 | 16 bits | Variables o salidas analógicas | Lectura y escritura |

### 🔍 Ejemplo práctico

| Dirección | Tipo | Descripción | Valor | Tamaño |
|------------|------|--------------|--------|--------|
| 00001 | Coil | Bomba encendida/apagada | 1 (ON) | 1 bit |
| 10001 | Discrete Input | Sensor de nivel bajo | 0 (OFF) | 1 bit |
| 30001 | Input Register | Temperatura (°C ×10) | 225 → 22.5 °C | 16 bits |
| 40001 | Holding Register | Setpoint temperatura (°C ×10) | 230 → 23.0 °C | 16 bits |

👉 Cuando el maestro (HMI/SCADA) lee el registro `30001`, obtiene la temperatura medida.

---

## 🧱 Estructura del mensaje Modbus

Un mensaje Modbus incluye:

- **ID del dispositivo**
- **Código de función** (tipo de operación)
- **Dirección de memoria**
- **Datos** (si aplica)
- **Verificación de errores** (en RTU)

### 🧩 Modbus RTU Frame


El **CRC** valida que el mensaje no se haya corrompido.

### 🌐 Modbus TCP Frame


- No usa CRC (lo maneja TCP).  
- Puerto reservado: **502**.  
- Longitud total máxima: **256 bytes**.  

---

## 🧠 Estructura MBAP (Modbus Application Header)

| Campo | Tamaño | Descripción |
|--------|---------|-------------|
| Transaction ID | 2 bytes | Identifica la solicitud |
| Protocol ID | 2 bytes | Siempre 0 (cualquier otro valor = error) |
| Length | 2 bytes | Número de bytes del mensaje |
| Unit ID | 1 byte | Dirección del dispositivo destino |

El resto del mensaje pertenece al **PDU (Protocol Data Unit)**.

---

## 🧩 Estructura PDU (Protocol Data Unit)

| Campo | Tamaño | Descripción |
|--------|---------|-------------|
| Function Code | 1 byte | Operación solicitada |
| Data | Variable | Dirección de memoria, valores, etc. |

---

## 💻 Ejemplo de solicitud Modbus TCP

> Lectura de temperatura desde el PLC con Unit ID 10 y dirección 30100.

| Campo | Valor |
|-------|-------|
| Unit ID | 10 |
| Function Code | 04 (Read Input Registers) |
| Dirección | 30100 |

El HMI (cliente) envía la solicitud → el PLC (servidor) responde con el valor del registro.

---

## 🧩 Conclusión

Modbus es el **protocolo más utilizado en la industria** por su simplicidad y soporte universal, pero también uno de los más **vulnerables**, ya que carece de seguridad nativa.  
Comprender su estructura y funcionamiento es fundamental para aplicar medidas de **ciberseguridad OT**, como segmentación, monitoreo pasivo y detección de anomalías en redes industriales.

---

📦 **Próximo paso:** Implementar el laboratorio práctico [`Lab01 — Simulación Modbus HMI ↔ PLC`](./lab01_modbus_vm_setup/README.md)
