# 🏭 Fundamentals of OT Cybersecurity (ICS/SCADA)

📘 **Curso:** Udemy  
🎓 **Estudiante:** Victoria García  
📅 **Fecha de inicio:** Octubre 2025  
🧩 **Módulo actual:** Introducción a OT y sistemas de control

---

## 🧠 Conceptos clave aprendidos

| Concepto | Descripción breve |
|-----------|-------------------|
| **Input / Output** | Entradas (sensores) y salidas (actuadores) que interactúan con el proceso físico. |
| **Process Logic Cycle** | Ciclo de ejecución de un PLC/PAC: lectura de entradas, lógica de control y actualización de salidas. | Base de todo sistema de control; entenderlo permite detectar cómo un ataque puede afectar la operación del proceso. |
| **Tags** | Variables que representan valores de entradas, salidas o procesos. | Manipular tags puede alterar el comportamiento del sistema, crítico para control y seguridad. |
| **Sensors / Actuators** | Sensores detectan condiciones físicas; actuadores ejecutan acciones físicas. | Conectan el mundo físico y digital; protegerlos evita daños y accidentes. |
| **Data Historian** | Base de datos que almacena el histórico de datos de procesos industriales. | Permite análisis de tendencias, auditoría y detección de anomalías. |
| **Safety Instrumented System (SIS)** | Sistema que interviene automáticamente para evitar situaciones peligrosas. | Protege personas, equipos y entorno; debe estar aislado y seguro. |
| **Maintenance** | Operaciones de mantenimiento y actualización de equipos OT/IT. | Mantener sistemas actualizados reduce riesgos de fallos y vulnerabilidades. |
| **HMI / Controller** | HMI: interfaz gráfica para monitoreo; Controller: ejecuta lógica de control. | Puerta de entrada a los procesos; comprometerla permite manipulación del sistema. |
| **Processes** | Conjunto de operaciones físicas y lógicas que transforman materias primas o energía. | Toda OT gira alrededor de procesos; entenderlos ayuda a identificar riesgos y puntos críticos. |
| **Engineering Workstation (Eng WS)** | Computadora usada para programar y mantener controladores y SCADA. | Punto crítico de seguridad; comprometerla permite modificar lógica de control o introducir malware. |
| **Distributed Control System (DCS)** | Control distribuido entre varios nodos conectados en red industrial. | Permite resiliencia y escalabilidad; ataques a nodos pueden afectar todo el proceso. |
| **Control Room** | Sala donde operadores monitorean y gestionan los sistemas OT. | Centro de operaciones; comprometerla puede dar control total de la planta. |
| **SCADA / MTU** | SCADA: supervisa y controla procesos; MTU: nodo central de SCADA. | Corazón de la supervisión remota; ataques pueden causar interrupciones o manipulación de procesos. |
| **PLC** | Controlador lógico programable que automatiza procesos industriales. | Elemento clave del control; manipularlo puede detener o dañar físicamente el proceso. |
| **RTU** | Dispositivo que recoge datos de sensores y envía comandos a actuadores en sitios remotos. | Extiende control a instalaciones distantes; vulnerable si no se protege adecuadamente. |
| **PAC** | Mezcla entre PLC y computadora industrial, con mayor flexibilidad y supervisión avanzada. | Permite lógicas complejas; amplia la superficie de ataque si no se protege. |
| **IED** | Dispositivo que monitorea y controla equipos eléctricos (relés, medidores, protecciones). | Muy usado en energía; un ataque puede interrumpir distribución eléctrica o causar fallos graves. |


✏️ **Ejemplo que entendí:**
> > **Ejemplo01:** Imaginemos un tanque de agua que tiene una bomba externa que impulsa agua desde un lago. 
> El tanque tiene dos válvulas: una controla la entrada de agua impulsada por la bomba y otra regula la salida del tanque. 
> La pregunta clave es: ¿cómo automatizar este proceso para que nadie tenga que operarlo manualmente?
> Para automatizarlo podemos usar:
> - **Sensores**: un sensor en el tanque que mide el nivel de agua (% de llenura) y un sensor en la bomba para verificar que funciona correctamente.
> - **Actuadores**: válvulas que abren/cierra el flujo de entrada y salida del tanque, y un actuador que enciende/apaga la bomba.
> Con esto, el **PLC** puede ejecutar un **Process Logic Cycle** que:
> 1. Lee los sensores.
> 2. Decide si abrir/cerrar válvulas o encender/apagar la bomba.
> 3. Actúa sobre los actuadores.
> Este sistema permite:
> - Automatizar el proceso sin intervención manual.
> - Monitorear el estado del tanque y la bomba.
> - Generar datos que se pueden almacenar en un **Data Historian** para análisis.
> Este es un ejemplo básico de cómo sensores, actuadores y PLC interactúan en un proceso industrial automatizable.
>
> > **Ejemplo02:** Imaginemos una planta de manufactura de un producto que entra en una banda en bruto, se moldea, luego se pinta y finalmente se termina el proceso. 
> En principio, podemos dividirlo en dos procesos principales:
> 1. **Moldeo**
> 2. **Pintura**
> Cada proceso tiene su **controlador (PLC/PAC)** que recibe información de distintos **sensores** y que se comunica de manera inmediata con el otro proceso a través de **networking**.  
> Es recomendable que ambos controladores sean del mismo fabricante para evitar problemas de compatibilidad.
> Estos controladores:
> - Transmiten información a la **sala de control**.
> - Replican la información en un **servidor aislado**, que protege la red industrial y guarda los datos.
> Esta estructura es un ejemplo de cómo funciona un **Distributed Control System (DCS)**:
> - Control distribuido entre múltiples controladores.
> - Comunicación y coordinación entre procesos.
> - Monitoreo

 

---

## ⚙️ Arquitectura típica IT/OT

    🔵 Zona IT (192.168.20.x)
 ┌────────────────────────────┐
 │  Servidor Ubuntu / SOC     │
 └────────────┬───────────────┘
              │
         🔥 Firewall / DMZ
              │
 ┌────────────┴───────────────┐
 │   🟢 Zona OT (192.168.10.x)│
 │  ScadaBR (192.168.10.3)    │
 │  OpenPLC (192.168.10.2)    │
 └────────────────────────────┘


🧩 **Notas personales:**
- La red OT controla procesos físicos y debe estar **aislada** de la red IT.  
- Los PLC son el punto más crítico: si se manipulan, se altera el proceso real.  
- Los protocolos industriales suelen ser inseguros (sin cifrado ni autenticación).  

---

## 🧰 Herramientas mencionadas / usadas

| Herramienta | Uso | Estado |
|--------------|-----|--------|
| Wireshark | Analizar tráfico de red | 🟡 Pendiente |
| OpenPLC | Simular PLC industrial | 🟡 Pendiente |
| ScadaBR | Visualizar proceso (HMI) | 🟡 Pendiente |
| VirtualBox | Crear máquinas virtuales | 🟢 Instalado |

---

## 📋 Aprendizajes personales

🧩 **Lo que me pareció más importante:**
- [x] Entendí la diferencia entre IT y OT.
- [x] Comprendí cómo los PLCs toman decisiones automáticas.
- [x] Aprendí qué es un control loop básico.
- [ ] Profundizar en protocolos industriales (Modbus, Profibus).

💭 **Dificultades o dudas:**
- [ ] Cómo se configuran realmente los PLCs.
- [ ] Cómo aislar redes IT/OT en VirtualBox.

---

## 📈 Próximos pasos

1. Terminar los módulos de fundamentos OT.  
2. Instalar OpenPLC y ScadaBR en máquinas virtuales.  
3. Diseñar mi primer diagrama de red IT/OT (Draw.io).  
4. Capturar tráfico Modbus con Wireshark.  

---

✍️ **Última actualización:** 10 Octubre 2025



