# 🚀 Proyecto Final SIS313: Implementación de Correo Corporativo de Alta Disponibilidad

**Asignatura:** SIS313 – Infraestructura, Plataformas Tecnológicas y Redes  
**Semestre:** 2/2025  
**Docente:** Ing. Marcelo Quispe Ortega  

---

## 👥 Miembros del Equipo (Grupo)

| Nombre Completo | Rol en el Proyecto | Contacto (GitHub / Email) |
|-----------------|-------------------|----------------------------|
| **Coraite Yanaje Luz Clara** | Maestro – Alta Disponibilidad (Keepalived, Nginx, RAID 10) | [lcoraiteyanaje-ship-it](https://github.com/lcoraiteyanaje-ship-it) |
| **Muraña Pizarro Nayda Thatiana** | Servidor Esclavo – Replicación BD, Backup | [thatiana2](https://github.com/thatiana2) |
| **Ríos Lizarazu Joaquin** | Base de Datos + Seguridad + Monitoreo | *(pendiente GitHub / Email)* |

---

# I. Objetivo del Proyecto

El objetivo principal de este proyecto es implementar un **sistema de correo corporativo** con Alta Disponibilidad que garantice:

- funcionamiento continuo ante fallas del servidor,
- replicación automática de datos críticos,
- tiempos mínimos de interrupción,
- protección contra spam y malware,
- una infraestructura segura, escalable y confiable.

Este proyecto asegura que el servicio de correo institucional continúe funcionando incluso ante fallas graves, permitiendo que la comunicación organizacional no se detenga.

---

# II. Justificación e Importancia

El correo electrónico es uno de los **servicios más críticos** dentro de universidades, empresas e instituciones.  
Su caída implica:

- pérdida de comunicación,
- retraso en trámites importantes,
- riesgo de pérdida de información,
- impacto en docentes, estudiantes y personal administrativo.

Este proyecto:

✔ elimina puntos únicos de falla (SPOF)  
✔ garantiza continuidad operacional  
✔ replica y protege información del correo  
✔ permite failover automático  
✔ refuerza la seguridad con estándares modernos  

En conclusión, la solución permite un sistema de correo **robusto, seguro y tolerante a fallos**.

---

# III. Tecnologías y Conceptos Implementados

## 3.1 Tecnologías Clave Utilizadas

| Tecnología | Rol dentro del Proyecto |
|-----------|--------------------------|
| **iRedMail / Mailcow** | Suite principal del servicio de correo |
| **Postfix (MTA)** | Envío y recepción de correos |
| **Dovecot (IMAP/POP3)** | Entrega y acceso al buzón |
| **MariaDB** | Base de datos del sistema |
| **NGINX** | Webmail y panel administrativo |
| **RAID 10 (mdadm)** | Redundancia y rendimiento en discos |
| **Keepalived + VRRP** | Alta Disponibilidad con IP Virtual |
| **ClamAV / SpamAssassin** | Filtros anti-virus / anti-spam |
| **UFW / TLS / DKIM / SPF / DMARC** | Seguridad y autenticación del dominio |

---

## 3.2 Temas de la Asignatura Aplicados (T1 - T6)

| Tema SIS313 | Aplicación en el sistema de correo |
|-------------|-----------------------------------|
| 🟢 **T1 — Continuidad Operacional** | Eliminación de SPOF y redundancia completa en servicios críticos |
| 🟢 **T2 — Alta Disponibilidad (HA)** | Failover automático con Keepalived + VRRP |
| 🟢 **T3 — Servicios Distribuidos** | Maestro–Esclavo, servidores paralelos |
| 🟢 **T4 — Servicios Complejos** | SMTP, IMAP, POP3, Webmail, paneles de administración |
| 🟢 **T5 — Seguridad y Hardening** | TLS, DKIM, SPF, DMARC, SpamAssassin, ClamAV |
| 🟢 **T6 — Automatización y DRP** | Scripts, replicación automática, failover automático |

---

# IV. Diseño de la Infraestructura y Topología

## 4.1 Diseño General

| VM / Host | Rol | IP | Red Lógica | SO |
|-----------|-----|----|------------|----|
| **VM-MAESTRO** | Servidor principal | *(variable)* | Red 1 | Ubuntu 22.04 |
| **VM-ESCLAVO** | Servidor de respaldo + BD réplica | *(variable)* | Red 1 | Ubuntu 22.04 |
| **VM-MONITOR** | Seguridad y métricas | *(variable)* | Red 2 | Ubuntu 22.04 |

### Componentes incluidos:
- IP Virtual (VIP) para failover inmediato  
- BD replicada (Maestro → Esclavo)  
- RAID 10 en Maestro y Esclavo  
- Monitoreo y seguridad en nodo especial (Monitor)  
- Filtros de spam y virus distribuidos  

---

# V. Estrategia Adoptada

### 🟦 1. **Alta Disponibilidad (HA)**
- Keepalived configurado en Maestro y Esclavo  
- VRRP asignando una IP Virtual  
- Scripts de salud revisan Postfix, Dovecot y Nginx  

### 🟧 2. **Replicación de Base de Datos (MariaDB)**
- Replicación Maestro → Esclavo  
- Persistencia en RAID 10  

### 🟩 3. **RAID 10**
Proporciona:
- redundancia en discos,
- alto rendimiento en lecturas/escrituras,
- seguridad ante fallos de hardware.

### 🟨 4. **Hardening y Seguridad**
Incluye:
- TLS obligatorio  
- Configuración SPF  
- Firmas DKIM  
- Políticas DMARC  
- Antivirus (ClamAV)  
- Antispam (SpamAssassin)  

---

# VI. Guía de Implementación y Puesta en Marcha

## 6.1 Pre-requisitos

- 3 máquinas virtuales  
- Ubuntu Server 22.04  
- Conectividad entre todas las VMs  
- Paquetes esenciales instalados:

## 📦 Repositorio

Este README corresponde al proyecto final del curso **SIS313 – Infraestructura, Plataformas Tecnológicas y Redes**.

