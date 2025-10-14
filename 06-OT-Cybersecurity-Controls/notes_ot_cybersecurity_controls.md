# 🛡️ Sección 6 — OT Cybersecurity Controls

📘 **Tema:** Controles y estrategias de ciberseguridad en entornos OT (Operational Technology).  
🎯 **Objetivo:** Comprender los principales mecanismos de defensa, monitoreo y cumplimiento aplicables en sistemas industriales.

---

## 🧭 Principio clave

> **"No se puede proteger lo que no se entiende."**

El primer paso para proteger un entorno OT es **comprender y mapear todos sus activos**, relaciones y comportamientos normales. A partir de esta visibilidad, se pueden aplicar controles adecuados y sostenibles.

---

## 🧩 Descubrimiento de activos

El descubrimiento es el proceso de identificar todos los **activos conectados o inactivos** en la red OT.  
Incluye hardware, servidores, estaciones de trabajo, HMIs, software y licencias.

### Etapas del descubrimiento:
1. **Inventario inicial:** Localizar todos los dispositivos y aplicaciones conectadas.  
2. **Relaciones:** Analizar cómo se comunican entre sí.  
3. **Clasificación:** Categorizar activos según su función, criticidad y exposición.  
4. **Visibilidad:** Mantener monitoreo constante para detectar nuevos dispositivos.

---

## 🌐 Descubrimiento de red (sin agente)

En OT se prefiere el **escaneo pasivo** frente al escaneo activo típico de IT.

- Se utiliza un **puerto espejo (SPAN)** en un switch para capturar tráfico sin interferir con la operación.  
- Permite construir una **línea base de tráfico (baselining)** para detectar anomalías.  
- No se envían paquetes ni se modifican datos, garantizando **seguridad operacional**.  
- Idealmente se ejecuta durante varias semanas para observar patrones estables.

> 🔎 En entornos OT, la predictibilidad del tráfico facilita la detección temprana de cambios sospechosos.

---

## 🗺️ Descubrimiento visual de red

La visualización de la red OT ayuda a:
- Entender **qué dispositivos** están conectados y **cómo** se comunican.  
- Detectar conexiones no autorizadas.  
- Establecer una **línea base visual** del entorno.

### Pasos recomendados:
a) Realizar inventario de dispositivos.  
b) Analizar flujos y conversaciones entre ellos.  
c) Representar gráficamente las relaciones (diagramas, mapas de red, topologías).

---

## 💻 Endpoint Security

La protección de los **endpoints** (estaciones, HMIs, servidores) es esencial.

Soluciones comunes:
- Antivirus y antimalware.  
- Sistemas EDR (detección y respuesta).  
- Prevención de intrusos en el endpoint.  
- Escaneo de vulnerabilidades y gestión de parches.

### Requisitos específicos para OT:
- Certificación **OEM** del proveedor.  
- Capacidad de operación **offline**.  
- Enfoque de **lista blanca** (solo ejecutar software autorizado).  
- Kernel y drivers seguros.  
- Protección contra explotación.  
- Funcionamiento autónomo.  
- Monitoreo continuo sin interferir en la producción.

---

## 👥 Identidad y gestión de accesos (IAM)

La gestión de identidades en OT debe garantizar que solo personal autorizado interactúe con los sistemas.

Controles recomendados:
- **Active Directory** o sistema equivalente para autenticación centralizada.  
- **Control de acceso basado en roles (RBAC)**.  
- **Autenticación multifactor (MFA)**.  
- **Single Sign-On (SSO)** cuando sea viable.  
- **Registro de auditoría:** usuarios, horarios, origen y acciones.  
- **Alertas** ante intentos de acceso fallidos o inusuales.

---

## 🚨 Detección de intrusos (IDS)

Los **IDS (Intrusion Detection Systems)** son ideales en OT por su naturaleza **pasiva**.

- Basan su funcionamiento en el **baselining** del tráfico.  
- Permiten validar cumplimiento de políticas de seguridad.  
- Detectan desviaciones en protocolos industriales y valores anómalos.  
- Su despliegue debe ser **robusto y adaptable** a entornos de campo.

---

## 🔥 Prevención de intrusos y NGFW (IPS)

Los **IPS (Intrusion Prevention Systems)** actúan activamente bloqueando conexiones.

### Recomendaciones:
- Minimizar latencia en operaciones críticas.  
- Implementar listas blancas de protocolos y equipos.  
- Verificar conformidad de protocolos OT.  
- Desplegar con **modo bypass** de respaldo.  
- Mantener segmentación de red y control de límites.  

> ⚙️ Las IPS deben equilibrar seguridad y disponibilidad. En OT, la continuidad del proceso siempre tiene prioridad.

---

## 🔐 Control de acceso a la red (NAC)

El **Network Access Control** permite controlar qué dispositivos pueden conectarse.

Características deseables:
- Fácil automatización.  
- Sin agentes (agentless).  
- Validación de políticas antes del acceso.  
- Gestión centralizada.  
- Integración con sistemas existentes (IAM, SIEM).  
- Visibilidad total de los activos conectados.

---

## 🌍 Acceso remoto seguro

El acceso remoto debe ser **limitado, autenticado y auditado**.

Buenas prácticas:
- Duración definida (inicio/fin).  
- Autenticación multifactor.  
- Verificación de cumplimiento antes de acceso.  
- VPN cifrada y segmentada.  
- Acceso limitado a activos o redes específicas.  
- Grabación y registro de sesiones.

---

## ⚙️ Componentes OT no seguros por diseño

Aspectos críticos a tener en cuenta:

- **Diseño del HMI:** integrarlo con autenticación y mínimos privilegios.  
- **Código y ciclo de vida del PLC:** considerar seguridad en el desarrollo.  
- **Vida útil de los dispositivos:** evitar equipos fuera de soporte.  
- **Conciencia del operador:** formar en seguridad OT.  
- **Brecha OT–IT:** reducirla mediante colaboración y políticas comunes.  
- **Cumplimiento ≠ Seguridad:** la conformidad no siempre garantiza protección.

---

## 📋 Consideraciones sobre la conformidad OT

Aspectos a documentar y evaluar en proyectos OT:

- Regulaciones y leyes nacionales (privacidad y seguridad).  
- Integración con sistemas y marcos existentes (SOC, IR).  
- Requisitos de documentación y auditorías.  
- Procesos de pruebas (FAT, SAT, ATP).  
- Gestión de cambios y mantenimiento remoto.  
- Lista aprobada de proveedores (OS, SW, HW).  
- Contratos, escalamiento y puntos de contacto.  
- Planes de formación y transferencia de conocimiento.  
- Documentación de **excepciones de seguridad** justificadas.

---

## 🧩 Conclusión

El fortalecimiento de la ciberseguridad OT requiere una visión integral:  
desde el inventario y visibilidad, hasta la gestión de identidades, segmentación, detección de anomalías y cumplimiento regulatorio.

> 🏁 La defensa en profundidad no es una única solución, sino un **ecosistema de controles coordinados** que garantizan la continuidad operativa y la seguridad industrial.
