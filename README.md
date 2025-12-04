# Documento-de-proyecto-final-
# 🚀 Proyecto Final SIS313: Implementación de Correo Corporativo de Alta Disponibilidad

**Subtítulo:** Plataforma de Correo Empresarial con Alta Disponibilidad, Replicación y Failover  
**Asignatura:** SIS313 – Infraestructura, Plataformas Tecnológicas y Redes  
**Semestre:** 2/2025  
**Docente:** Ing. Marcelo Quispe Ortega  

---

## 👥 Integrantes del Proyecto
| Nombre | Rol |
|-------|------|
| **Coraite Yanaje Luz Clara** | Maestro (Alta Disponibilidad – Keepalived, Nginx, RAID 10) |
| **Muraña Pizarro Nayda Thatiana** | Esclavo (Replicación Maestro–Esclavo + Backup) |
| **Ríos Lizarazu Joaquin** | Base de Datos + Monitoreo (ClamAV, SpamAssassin, Hardening, Métricas) |

---

## 🎯 Objetivo del Proyecto

Implementar una plataforma de **correo corporativo empresarial** basada en iRedMail/Mailcow que garantice:

- Alta Disponibilidad mediante **VRRP y failover automático**  
- Eliminación de puntos únicos de falla (SPOF)  
- Replicación Maestro–Esclavo de la base de datos  
- Tolerancia de fallos en discos con **RAID 10**  
- Seguridad reforzada: TLS/SSL, SPF, DKIM, DMARC  
- Protección Anti-Spam/Anti-Virus usando ClamAV y SpamAssassin  

### 🔎 Problema / Justificación
El correo institucional es un servicio crítico. Una falla puede dejar incomunicada a toda la organización. El sistema anterior presentaba **SPOF**, falta de redundancia y vulnerabilidades.

### 🧩 Solución Propuesta
Implementar una arquitectura redundante compuesta por:

✔ Maestro – Esclavo con replicación  
✔ Keepalived + VRRP para IP Virtual  
✔ RAID 10 para tolerancia a fallos  
✔ Hardening avanzado  
✔ Anti-Spam y Anti-Virus  
✔ Monitoreo y métricas  

---

## 🛠️ Tecnologías Implementadas

### ⭐ Software Principal
- **iRedMail / Mailcow** – Suite completa de correo
- **Postfix** → MTA  
- **Dovecot** → IMAP/POP3  
- **Nginx** → Webmail y panel administrativo  

### 🖥️ Servidores y Sistema Operativo
- **Ubuntu Server 22.04 LTS**  
- Máquinas virtuales: Maestro, Esclavo, Monitor  

### 🗄️ Base de Datos
- **MariaDB** (usuarios, dominios, configuraciones)

### 🔒 Seguridad
- **ClamAV**, **SpamAssassin**  
- Certificados SSL/TLS  
- Registros: SPF, DKIM, DMARC  
- Firewall y buenas prácticas de hardening  

### 🔁 Alta Disponibilidad
- **Keepalived (VRRP)**  
- Scripts de salud para Postfix, Dovecot y Nginx  
- IP Virtual (VIP) compartida por Maestro/Esclavo  

### 💾 Almacenamiento
- **RAID 10** con `mdadm`  
- Montaje automático con `/etc/fstab`

---

## 🧠 Temas de SIS313 Aplicados

### 🔹 T1 — Continuidad Operacional
- Eliminación de SPOF  
- Redundancia total del servicio crítico  

### 🔹 T2 — Alta Disponibilidad
- Failover con Keepalived  
- Replicación de BD  
- RAID 10  

### 🔹 T4 — Servicios Complejos
- Configuración SMTP/IMAP/POP3  
- Optimización Postfix y Dovecot  

### 🔹 T5 — Seguridad y Hardening
- TLS/SSL  
- SPF, DKIM y DMARC  
- Anti-Spam y Anti-Virus  
- Firewall y buenas prácticas  

---

## 🌐 Arquitectura del Sistema

La infraestructura se compone de tres máquinas:

### 🟢 **VM Maestro**
- iRedMail/Mailcow  
- Postfix + Dovecot + Nginx  
- Keepalived (MASTER)  
- RAID 10  

### 🔵 **VM Esclavo**
- Replicación BD  
- Keepalived (BACKUP)  
- RAID 10  

### 🟡 **VM Monitor**
- Monitoreo (Prometheus/Grafana)  
- Validación SPF/DKIM/DMARC  
- Seguridad y registros  

### Componentes Clave
- IP Virtual (VIP)  
- Scripts de salud  
- BD replicada  
- Buzones sincronizados  
- Hardening en todas las capas  

---

## ⚙️ Estrategia de Implementación

### 1️⃣ RAID 10
- Creado con `mdadm`  
- Configurado para montaje automático  

### 2️⃣ Instalación de Servicios de Correo
- Instalación iRedMail/Mailcow  
- Configuración Postfix, Dovecot, Nginx  
- Integración de Anti-Spam/Anti-Virus  

### 3️⃣ Alta Disponibilidad
- Keepalived MASTER/BACKUP  
- VRRP + IP Virtual  
- Scripts de monitoreo de salud  

### 4️⃣ Hardening y Monitoreo
- SPF, DKIM, DMARC  
- ClamAV + SpamAssassin  
- Prometheus + Grafana  

---

## ✔️ Pruebas y Validación

| Prueba | Resultado |
|--------|-----------|
| Failover con VRRP | Migración exitosa < 5 s |
| Replicación BD | Datos coherentes tras failover |
| Anti-virus (EICAR) | Bloqueado correctamente |
| SPF/DKIM/DMARC | Validación exitosa |

---

## 🏁 Conclusiones

- El sistema de correo ahora cuenta con **Alta Disponibilidad real**.  
- Se eliminaron puntos únicos de falla a nivel de servicio, BD y discos.  
- La plataforma es segura, tolerante a fallos y preparada para operación continua.  
- Las herramientas implementadas permiten monitoreo y respuesta rápida ante incidentes.  

### 📚 Lecciones Aprendidas
- Los scripts de salud en Keepalived son esenciales para un failover fiable.  
- RAID 10 mejora rendimiento y resiliencia.  
- La replicación y sincronización adecuada evita corrupción de datos.  

---

## 📦 Repositorio

Este README corresponde al proyecto final del curso **SIS313 – Infraestructura, Plataformas Tecnológicas y Redes**.

