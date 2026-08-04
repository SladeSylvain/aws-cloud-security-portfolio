# 🔍 Investigación de Incidentes de Seguridad en AWS con CloudTrail

## 📋 Resumen del Proyecto
Análisis forense y respuesta ante incidentes (DFIR) tras la detección de un ataque de *defacement* en un sitio web alojado en Amazon EC2. La investigación requirió correlacionar eventos a nivel de sistema operativo (autenticación SSH) con trazabilidad a nivel de API mediante **AWS CloudTrail**, logrando identificar las credenciales comprometidas, el vector de entrada y aplicar las acciones de remediación en IAM y S3.

---

## 🎯 Objetivos e Implementación Técnica
- **Análisis de Vectores de Entrada:** Inspección de Security Groups (`WebSecurityGroup`) y configuraciones de SSH (`/etc/ssh/sshd_config`) para entender el acceso remoto inicial.
- **Trazabilidad de Registro de Eventos (CloudTrail):** Extracción y descompresión de archivos de registros JSON (`.json.gz`) generados por CloudTrail en S3 (`monitoring1234`).
- **Atribución y Correlación de IP:** Diferenciación técnica entre la IP pública de origen del atacante (vía SSH) y las llamadas a la API de AWS ejecutadas *inside-instance* utilizando el rol o credenciales de la instancia.
- **Remediación y Remoción de Amenazas:** Desactivación y posterior eliminación de las credenciales de acceso compromised/maliciosas (`AKIA...`) vinculadas al usuario `chaos` en **AWS IAM**.

---

## 📸 Evidencias de la Investigación Forense

### 1. Detección del Incidente (*Defacement*)
![Defaced Website](images/1783024861510.jpeg)
*Modificación no autorizada del sitio web "Café" mediante la alteración de activos estáticos.*

### 2. Inspección del Vector de Red (Security Groups)
![Security Group Audit](images/1783024861204.jpeg)
*Revisión de las reglas de entrada permitiendo tráfico SSH (Puerto 22) y HTTP (Puerto 80).*

### 3. Aprovisionamiento de Registro Centralizado (CloudTrail)
![S3 Bucket Monitoring](images/1783024860766.jpeg)
*Configuración del bucket `monitoring1234` para la persistencia de eventos de auditoría.*

### 4. Análisis de Logs Locales y Audits SSH
![SSH Config Analysis](images/1783024860915.jpeg)
*Auditoría de archivos de configuración y logs de autenticación en la instancia Linux.*

### 5. Extracción y Descompresión de Eventos CloudTrail
![CloudTrail Logs Inspection](images/1783024860792.jpeg)
*Inspección de archivos `.json.gz` para rastrear las llamadas a las API de AWS.*

### 6. Ejecución de Consultas vía AWS CLI
![CLI CloudTrail Queries](images/1783024861278.jpeg)
*Correlación de llamadas de API y llamadas `sts:GetCallerIdentity` ejecutadas desde el servidor.*

### 7. Remediación en IAM (Contención de la Amenaza)
![IAM User Deletion](images/1783024860964.jpeg)
*Revocación de la Access Key `AKIA264DIW3UDQWGORML` y eliminación del usuario comprometido `chaos`.*

### 8. Recuperación e Integridad del Servicio
![Restored Website](images/1783024860710.jpeg)
*Restablecimiento del servicio y verificación del sitio web operando normalmente.*

---

## 🛠️ Servicios y Herramientas Utilizadas
- **AWS CloudTrail** (Auditoría de API y registros de eventos)
- **AWS IAM** (Gestión de identidades, Access Keys e Incident Response)
- **Amazon EC2 & Security Groups** (Aislamiento y auditoría de red)
- **Amazon S3** (Almacenamiento de logs de auditoría)
- **Linux Security Tools** (Análisis de logs SSH y CLI)
