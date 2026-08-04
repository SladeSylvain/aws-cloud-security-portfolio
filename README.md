# ☁️ Hands-On AWS Cloud & Security Engineering Portfolio

[![AWS Certified Cloud Practitioner](https://img.shields.io/badge/AWS-Cloud%20Practitioner-orange?logo=amazon-aws&style=flat-square)](https://aws.amazon.com/)
[![Focus](https://img.shields.io/badge/Focus-Cloud%20Architecture%20%26%20SecOps-blue?style=flat-square)]()
[![Status](https://img.shields.io/badge/Status-8%20Labs%20Completed-success?style=flat-square)]()

Bienvenido a mi repositorio de proyectos de arquitectura, operaciones y seguridad en **Amazon Web Services (AWS)**. 

Este espacio no es solo teoría de certificación: contiene **8 laboratorios prácticos documentados con evidencia de despliegue, scripts y análisis forense**. Aquí demuestro resolución de problemas reales en redes virtuales (VPC), almacenamiento de objetos, bases de datos relacionales/NoSQL, automatización de infraestructura e investigación de incidentes de seguridad (DFIR).

---

## 🎯 Resumen de Capacidades Técnicas

- **Redes & Aislamiento (VPC):** Diseño de arquitecturas Multi-AZ, subredes públicas/privadas, tablas de enrutamiento, Internet Gateways y NAT Gateways.
- **Seguridad & Incident Response:** Análisis forense con CloudTrail, inspección profunda de paquetes (Suricata IDS/IPS), gestión de identidades (IAM) y Security Groups.
- **Cómputo & Automatización:** Despliegue e inicialización de instancias EC2 mediante scripts `User Data` (*cloud-init*) y administración remota SSH-less con AWS Systems Manager (SSM).
- **Almacenamiento & Bases de Datos:** Gestión de buckets S3 (Bucket Policies, AWS CLI), conectividad multi-capa con RDS (MySQL) y modelado NoSQL eficiente en DynamoDB (Query vs Scan).

---

## 🛠️ Matriz de Laboratorios y Casos de Uso Reales

A continuación se detalla la documentación técnica de cada escenario implementado:

| # | Laboratorio / Proyecto | Problema Real / Escenario Resuelto | Servicios & Herramientas | Enlace a Documentación |
|---|---|---|---|---|
| **01** | **VPC Multi-AZ Architecture** | Diseño de red tolerante a fallos para aislar servicios críticos en subredes privadas con salida controlada a Internet. | VPC, Subnets, NAT Gateway, IGW, Route Tables | [📄 Ver Documento](./01-vpc-multi-az-architecture.md) |
| **02** | **Network Firewall & Suricata Rules** | Inspección profunda de paquetes y filtrado de tráfico saliente para mitigar exfiltración de datos y conexiones no autorizadas. | AWS Network Firewall, Suricata IDS/IPS, SSM | [📄 Ver Documento](./02-network-firewall-suricata.md) |
| **03** | **DynamoDB NoSQL Optimization** | Optimización de costos y latencia en bases de datos NoSQL mediante consultas indexadas (`Query`) frente a escaneos globales masivos (`Scan`). | Amazon DynamoDB, CloudWatch | [📄 Ver Documento](./03-dynamodb-nosql-database.md) |
| **04** | **RDS Database Multi-Tier Connectivity** | Diagnóstico y resolución de fallos de conectividad en arquitecturas de 2 capas (Web <-> DB) ajustando reglas de Security Group. | Amazon RDS (MySQL), EC2, VPC | [📄 Ver Documento](./04-rds-database-connectivity.md) |
| **05** | **Systems Manager Operations & Automation** | Administración de flota EC2 a escala, ejecución de comandos remotos sin puertos SSH abiertos y gestión de variables en Parameter Store. | AWS Systems Manager (Session Manager, Run Command) | [📄 Ver Documento](./05-systems-manager-automation.md) |
| **06** | **EC2 Automated Web Server Provisioning** | Automatización del ciclo de vida de servidores Apache desplegados en VPCs personalizadas usando scripts de arranque (*User Data*). | Amazon EC2, User Data, Amazon VPC | [📄 Ver Documento](./06-ec2-webserver-automation.md) |
| **07** | **S3 Object Storage & Security Governance** | Gobierno de acceso a almacenamiento masivo de objetos, configuración de políticas públicas en JSON e interacción vía AWS CLI. | Amazon S3, AWS CLI, S3 Bucket Policies | [📄 Ver Documento](./07-s3-object-storage-lab.md) |
| **08** | **AWS Incident Response & CloudTrail DFIR** | Investigación forense tras un ataque de *defacement*: correlación de trazabilidad de IPs (SSH vs llamadas API) y remediación de credenciales comprometidas. | AWS CloudTrail, IAM, Amazon S3, Linux CLI | [📄 Ver Documento](./08-aws-incident-response-cloudtrail.md) |

---

## 🔍 Destacado Técnico: Caso de Investigación de Incidentes (Lab 08)

 Uno de los retos más complejos del portafolio consistió en identificar la causa raíz de un compromiso en un servidor web:

> **El Aprendizaje Clave:** Durante la auditoría se identificó que el atacante ingresó por SSH utilizando su dirección IP pública real. Sin embargo, las acciones maliciosas posteriores en la nube (llamadas a la API de AWS) quedaron registradas en **CloudTrail** con la IP privada de la propia instancia EC2, dado que las instrucciones se ejecutaron *inside-instance*. 
> 
> Esta diferenciación entre el **plano del sistema operativo** y el **plano de control/API de AWS** permitió aislar las credenciales IAM comprometidas (`chaos`), revocar sus Access Keys y restaurar la integridad del servicio.

---

**## 👨‍💻 Sobre Mí


- **Alexander Luis Carvajal Pizarro**
- **Formación:** Cloud Engineering (AWS) & Full Stack Development
- **Ubicación:** Santiago, Chile
- **Especialidad:** Infraestructura Cloud AWS, automatización de operaciones, desarrollo web y respuesta a incidentes (SecOps).
- **Contacto:** [LinkedIn](https://www.linkedin.com/in/tu-perfil) | [alexander.carvajal.pizarro@gmail.com](mailto:alexander.carvajal.pizarro@gmail.com)**
**
