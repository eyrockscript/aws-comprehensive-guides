Capítulo 5: # Seguridad y Cumplimiento en AWS

## Resumen Ejecutivo

En la era digital actual, la seguridad en la nube se ha convertido en una prioridad estratégica para organizaciones de todos los tamaños. Amazon Web Services (AWS) ofrece un conjunto integral de servicios de seguridad y cumplimiento diseñados para proteger datos, aplicaciones e infraestructura en la nube. Este whitepaper explora los principales conceptos, servicios y mejores prácticas de seguridad en AWS, proporcionando una guía completa para implementar arquitecturas seguras y cumplir con requisitos regulatorios. Comprender estos aspectos es fundamental para cualquier organización que busque aprovechar los beneficios de la nube mientras mantiene una postura de seguridad robusta.

## Modelo de Responsabilidad Compartida

El modelo de responsabilidad compartida es un concepto fundamental para entender la seguridad en AWS.

### División de Responsabilidades

- **Responsabilidad de AWS:** Seguridad "DE" la nube
  - Infraestructura física (centros de datos)
  - Hardware y software de virtualización
  - Redes físicas y virtuales
  - Servicios gestionados como S3, DynamoDB, RDS

- **Responsabilidad del Cliente:** Seguridad "EN" la nube
  - Configuración de servicios AWS
  - Gestión de datos
  - Controles de acceso e identidad
  - Seguridad de aplicaciones
  - Configuración de sistemas operativos
  - Parches y actualizaciones

### Variaciones según el Servicio

El nivel de responsabilidad varía según el tipo de servicio:

- **IaaS (Ej. EC2):** Mayor responsabilidad del cliente
- **PaaS (Ej. Elastic Beanstalk):** Responsabilidad compartida
- **SaaS (Ej. WorkMail):** Mayor responsabilidad de AWS

## AWS Identity and Access Management (IAM)

IAM es el servicio fundamental para controlar el acceso seguro a recursos AWS.

### Componentes Principales

- **Usuarios:** Identidades para personas o servicios
- **Grupos:** Colecciones de usuarios para asignación de permisos
- **Roles:** Conjunto de permisos temporales asumibles
- **Políticas:** Documentos JSON que definen permisos
- **Proveedores de identidad:** Integración con directorios externos

### Prácticas Recomendadas

- **Privilegio mínimo:** Otorgar solo los permisos necesarios
- **MFA:** Implementar autenticación multifactor
- **Rotación de credenciales:** Cambio regular de contraseñas y claves
- **Análisis de acceso:** Revisión periódica de permisos
- **AWS Organizations:** Administración centralizada de múltiples cuentas
- **Políticas basadas en condiciones:** Restricciones adicionales (IP, hora, MFA)

### AWS IAM Identity Center (SSO)

Servicio para administrar centralmente el acceso a múltiples cuentas AWS y aplicaciones.

- Integración con proveedores de identidad corporativos
- Experiencia de inicio de sesión único
- Gestión centralizada de permisos
- Monitoreo de actividad de usuario

## Protección de Infraestructura

### VPC (Virtual Private Cloud) y Seguridad de Red

- **Grupos de seguridad:** Firewalls stateful a nivel de instancia
- **Network ACLs:** Firewalls stateless a nivel de subred
- **Route tables:** Control de tráfico entre subredes
- **Aislamiento de subredes:** Separación de recursos críticos
- **VPC Endpoints:** Acceso privado a servicios AWS
- **VPC Flow Logs:** Registro de tráfico IP para análisis

### AWS Shield y Protección DDoS

- **Shield Standard:** Protección básica gratuita
- **Shield Advanced:** Protección avanzada, equipo de respuesta
- **Prácticas DDoS resilientes:**
  - Arquitectura distribuida
  - Auto Scaling
  - CloudFront para absorción de ataques
  - Route 53 para DNS resiliente

### AWS WAF (Web Application Firewall)

- Protección contra vulnerabilidades web comunes (OWASP Top 10)
- Reglas personalizables y administradas
- Integración con CloudFront, ALB, API Gateway, AppSync
- Bot control y prevención de fraude

### AWS Network Firewall

- Firewall de red administrado para VPCs
- Inspección de tráfico con estado
- Filtrado de dominios y URLs
- Prevención de intrusiones
- Integración con servicios de terceros

## Protección de Datos

### Encriptación en AWS

- **En reposo:**
  - AWS KMS (Key Management Service)
  - CloudHSM (Hardware Security Module)
  - Encriptación a nivel de servicio (S3, EBS, RDS)

- **En tránsito:**
  - TLS/SSL
  - VPN
  - API endpoints HTTPS
  - AWS Certificate Manager

- **Gestión de claves:**
  - Rotación automática
  - Control de acceso granular
  - Auditoría de uso

### Amazon Macie

- Descubrimiento y clasificación de datos sensibles
- Alertas sobre configuraciones de acceso de riesgo
- Monitoreo continuo de datos en S3
- Informes detallados de exposición de datos

### AWS Config

- Evaluación, auditoría y registro de configuraciones
- Reglas de conformidad predefinidas y personalizadas
- Seguimiento de cambios históricos
- Remediación automática

## Detección de Amenazas y Respuesta a Incidentes

### Amazon GuardDuty

- Servicio de detección de amenazas continuo
- Análisis inteligente utilizando ML
- Monitorización de:
  - Logs de CloudTrail (API calls)
  - VPC Flow Logs (tráfico de red)
  - DNS logs (exfiltración de datos)
  - Actividad de Kubernetes

### AWS Security Hub

- Visión centralizada del estado de seguridad
- Agregación de alertas de múltiples servicios
- Comprobación automatizada de estándares:
  - AWS Foundational Security Best Practices
  - CIS AWS Foundations Benchmark
  - PCI DSS
- Flujos de trabajo de remediación

### Amazon Detective

- Análisis profundo de eventos de seguridad
- Visualizaciones interactivas de comportamiento
- Investigación de causas raíz
- Correlación de múltiples fuentes de datos

### AWS CloudTrail

- Registro y monitoreo de actividad de la cuenta
- Histórico de eventos de API
- Detección de actividad inusual
- Evidencia para cumplimiento y auditoría

## Gestión de Vulnerabilidades

### Amazon Inspector

- Evaluación automatizada de vulnerabilidades
- Escaneo de instancias EC2 y contenedores
- Análisis de configuración de red
- Priorización de hallazgos basada en criticidad

### AWS Systems Manager

- Gestión de parches a escala
- Inventario de software y configuración
- Automatización de tareas de seguridad
- Gestión de conformidad

## Gobernanza y Cumplimiento

### AWS Artifact

- Portal de conformidad y auditoría
- Acceso a certificaciones y documentación
- Reports de seguridad (SOC, PCI, ISO)
- Acuerdos de confidencialidad y uso

### AWS Audit Manager

- Mapeo de controles a estándares
- Recopilación continua de evidencia
- Informes para auditorías
- Marcos de cumplimiento predefinidos y personalizados

### Certificaciones y Programas de Conformidad

AWS mantiene numerosas certificaciones:
- SOC 1/2/3
- PCI DSS
- ISO 9001/27001/27017/27018
- FedRAMP
- HIPAA
- GDPR
- FIPS 140-2
- Y muchas más específicas por país e industria

## Seguridad de Aplicaciones

### AWS Secrets Manager

- Gestión centralizada de secretos
- Rotación automática programada
- Integración con RDS, DocumentDB, Redshift
- Control de acceso granular

### AWS Parameter Store

- Almacenamiento jerárquico de configuración
- Integración con KMS para cifrado
- Gestión de versiones
- Historial de cambios

### AWS Lambda Security

- Permisos basados en roles IAM
- Entorno aislado de ejecución
- Encriptación en tránsito y reposo
- VPC integration para mayor aislamiento

### Amazon Cognito

- Gestión de identidades para aplicaciones
- Autenticación y autorización
- Federación con proveedores sociales e empresar
