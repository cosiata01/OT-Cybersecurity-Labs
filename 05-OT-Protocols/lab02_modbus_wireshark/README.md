# 🧪 Lab02 — Captura y análisis de tráfico Modbus TCP con Wireshark

## 🎯 Objetivo
Capturar y analizar el tráfico Modbus TCP entre un HMI/cliente y un PLC/esclavo, identificando los campos clave de los mensajes y entendiendo cómo viaja la información en una red OT.

## 🛠️ Requisitos previos
- Lab01 completado: simulación de comunicación Modbus TCP (ModScan ↔ ModSim)
- Dos máquinas virtuales Windows 10 conectadas en la misma red
- Wireshark instalado en la máquina cliente
- Conocimiento básico de Modbus TCP

## ⚙️ Procedimiento
1. Configurar red entre cliente y servidor.
2. Iniciar simulación Modbus (ModSim y ModScan).
3. Capturar tráfico en Wireshark.
4. Enviar solicitudes Modbus y observar respuestas.
5. Guardar la captura en `captures/lab02_capture.pcapng`.
6. Documentar hallazgos en `notes_lab02_results.md`.

## 📁 Estructura recomendada
- `screenshots/` → capturas de Wireshark
- `captures/` → archivos `.pcapng`
- `configs/` → configuración de laboratorio

## 🔗 Referencias
- [Wireshark Modbus dissector](https://wiki.wireshark.org/Modbus)
- [Modbus TCP specification](https://modbus.org/specs.php)
