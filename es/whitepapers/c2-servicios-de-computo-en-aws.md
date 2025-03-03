# Capítulo 2: Servicios de Cómputo en AWS

## Resumen Ejecutivo

Los servicios de cómputo constituyen el núcleo fundamental de la plataforma Amazon Web Services (AWS), proporcionando los recursos computacionales necesarios para ejecutar aplicaciones de cualquier escala y complejidad. Este whitepaper explora en detalle los principales servicios de cómputo ofrecidos por AWS, desde máquinas virtuales tradicionales hasta modelos sin servidor y contenedores, analizando sus características, casos de uso óptimos y consideraciones para su implementación. Entender estos servicios es esencial para diseñar arquitecturas eficientes y rentables en la nube.

## Amazon EC2: Elastic Compute Cloud

Amazon EC2 es el servicio de computación más conocido de AWS, ofreciendo capacidad de cómputo redimensionable en la nube. EC2 proporciona máquinas virtuales (instancias) que pueden configurarse con diferentes sistemas operativos y recursos computacionales.

### Tipos de Instancias

EC2 ofrece una amplia variedad de tipos de instancias optimizadas para diferentes casos de uso:

- **Instancias de uso general (T3, M5, M6):** Balance entre recursos de computación, memoria y red
- **Instancias optimizadas para cómputo (C5, C6):** Alta proporción de CPU a memoria
- **Instancias optimizadas para memoria (R5, R6, X1):** Gran capacidad de memoria
- **Instancias optimizadas para almacenamiento (I3, D2):** Alto rendimiento de E/S y almacenamiento
- **Instancias aceleradas (P3, G4, Inf1):** Aceleradores de hardware (GPU, FPGA) para cargas específicas
- **Instancias HPC (Hpc6a):** Para computación de alto rendimiento

### Modelos de Compra

AWS ofrece diferentes opciones para adquirir instancias EC2, permitiendo optimizar costos según las necesidades:

- **Instancias bajo demanda:** Pago por hora/segundo sin compromisos
- **Instancias reservadas:** Descuentos significativos por compromisos de 1-3 años
- **Savings Plans:** Compromiso de uso por hora a cambio de tarifas reducidas
- **Instancias spot:** Capacidad EC2 no utilizada con descuentos de hasta 90%
- **Hosts dedicados:** Servidores físicos dedicados

### Amazon EC2 Auto Scaling

Permite ajustar automáticamente la capacidad de EC2 según las condiciones definidas:

- **Escalado dinámico:** Responde a cambios en la demanda
- **Escalado predictivo:** Programa cambios de capacidad
- **Grupos de Auto Scaling:** Gestiona conjuntos de instancias como una unidad lógica
- **Integraciones:** CloudWatch, EventBridge, Application Load Balancer

### Opciones de Almacenamiento

EC2 ofrece múltiples opciones de almacenamiento:

- **Amazon EBS (Elastic Block Store):** Volúmenes persistentes independientes de la instancia
- **Almacenamiento de instancias:** Almacenamiento efímero físicamente conectado al host
- **Amazon EFS/FSx:** Almacenamiento de archivos compartidos
- **S3/S3 Glacier:** Almacenamiento de objetos para datos no estructurados

## AWS Lambda: Computación sin Servidor

AWS Lambda permite ejecutar código sin aprovisionar ni administrar servidores, pagando solo por el tiempo de computación consumido.

### Características Principales

- **Ejecución basada en eventos:** Se activa en respuesta a eventos
- **Escalado automático:** Gestiona automáticamente la capacidad
- **Modelo de precios:** Pago solo por milisegundos de ejecución
- **Arquitectura sin estado:** Cada ejecución es independiente
- **Límites de tiempo:** Hasta 15 minutos por ejecución

### Lenguajes Soportados

Lambda soporta múltiples lenguajes de programación:
- Node.js, Python, Java, Go, .NET Core, Ruby
- Contenedores personalizados

### Integraciones y Modelos de Despliegue

- **Integraciones nativas:** API Gateway, S3, DynamoDB, SNS, SQS, etc.
- **AWS SAM:** Framework para desarrollar aplicaciones sin servidor
- **AWS CDK:** Definición de infraestructura usando lenguajes familiares

### Patrones de Arquitectura

- **Procesamiento de eventos asíncronos**
- **Backends de aplicaciones web/móviles**
- **Procesamiento en tiempo real**
- **ETL y procesamiento de datos**

## Contenedores en AWS

Los contenedores proporcionan un método estándar para empaquetar código, configuraciones y dependencias de una aplicación.

### Amazon Elastic Container Service (ECS)

Servicio de orquestación de contenedores completamente gestionado:

- **Tipos de lanzamiento:** EC2 y Fargate (sin servidor)
- **Definiciones de tareas:** Especificación de contenedores
- **Servicios ECS:** Mantenimiento de instancias de tareas en el tiempo
- **Integraciones:** ALB, CloudWatch, IAM, ECR

### Amazon Elastic Kubernetes Service (EKS)

Servicio gestionado de Kubernetes:

- **Kubernetes gestionado:** Control plane completamente gestionado
- **Conformidad:** 100% compatible con K8s open source
- **Despliegue flexible:** EC2, Fargate, on-premises (con EKS Anywhere)
- **Integraciones:** IAM, VPC, CloudWatch, ECR

### AWS Fargate

Modelo de computación sin servidor para contenedores:

- **Sin administración de infraestructura:** Enfoque en las aplicaciones
- **Escalado preciso:** Asignación de recursos a nivel de tarea
- **Seguridad mejorada:** Aislamiento de cargas de trabajo
- **Compatible:** Funciona con ECS y EKS

### Amazon Elastic Container Registry (ECR)

Registro de contenedores completamente gestionado:

- **Almacenamiento seguro:** Para imágenes de contenedores
- **Integración con IAM:** Control de acceso granular
- **Escaneo de seguridad:** Detección de vulnerabilidades
- **Replicación cross-region:** Para disponibilidad global

## AWS App Runner

Servicio completamente gestionado para desplegar aplicaciones web y APIs:

- **Simplicidad:** Despliegue con un solo clic desde código o imagen
- **Totalmente gestionado:** Compilación, despliegue y operaciones
- **Auto-scaling:** Ajuste automático según tráfico
- **Integraciones:** VPC, CloudWatch, ECR, GitHub

## Comparación y Selección de Servicios

### Criterios de Selección

- **Nivel de administración requerido:** De completamente gestionado a control total
- **Flexibilidad vs. simplicidad**
- **Modelo de precios y optimización de costos**
- **Requisitos de rendimiento y escalabilidad**
- **Integraciones necesarias con otros servicios**

### Escenarios y Recomendaciones

| Escenario | Servicio Recomendado | Razón |
|-----------|----------------------|-------|
| Cargas de trabajo tradicionales | EC2 | Control completo sobre el entorno |
| Microservicios | ECS/EKS con Fargate | Orquestación sin administración de servidores |
| Procesamiento por eventos | Lambda | Modelo sin servidor, pago por uso |
| Aplicaciones web estándar | App Runner | Simplicidad de despliegue y gestión |
| Picos pronunciados de tráfico | Lambda o Fargate | Escalado automático sin provisión previa |
| Cargas de trabajo predecibles | EC2 con instancias reservadas | Optimización de costos |

## Arquitecturas Híbridas

Muchas organizaciones implementan arquitecturas que combinan diferentes servicios de cómputo:

- **Patrones comunes:**
  - EC2 para bases de datos + Lambda para APIs
  - Contenedores para microservicios + Lambda para integración
  - Núcleo en EC2 + procesamiento por lotes en Spot

- **Consideraciones de diseño:**
  - Comunicación entre servicios
  - Gestión centralizada
  - Monitoreo unificado
  - Seguridad coherente

## Mejores Prácticas

### Optimización de Rendimiento

- Selección adecuada del tipo de instancia/servicio
- Monitoreo y ajuste continuos
- Optimización de código e imágenes
- Distribución geográfica adecuada

### Seguridad

- Principio de privilegio mínimo con IAM
- Encriptación en tránsito y en reposo
- Segmentación de redes con VPC
- Análisis regular de vulnerabilidades

### Optimización de Costos

- Dimensionamiento adecuado
- Instancias reservadas o Savings Plans para cargas predecibles
- Uso de Spot para cargas tolerantes a fallos
- Monitoreo y alertas de costos

### Alta Disponibilidad

- Diseño multi-AZ
- Auto-scaling
- Estrategias de recuperación ante fallos
- Pruebas de resiliencia

## Tendencias Futuras

- Expansión de modelos sin servidor
- Mayor rendimiento con procesadores personalizados (Graviton)
- Integración más profunda con ML/IA
- Computación de borde/edge computing

## Conclusión

Los servicios de cómputo de AWS proporcionan un amplio espectro de opciones para ejecutar cualquier tipo de aplicación en la nube. La elección entre EC2, Lambda, contenedores o servicios completamente gestionados debe basarse en los requisitos específicos de cada aplicación, considerando factores como el control necesario, el modelo de operación, los requisitos de rendimiento y las consideraciones de costos.

La tendencia general en AWS es hacia servicios que reduzcan la carga operativa, permitan centrarse en el desarrollo de aplicaciones y optimicen automáticamente los recursos. Independientemente del servicio elegido, seguir las mejores prácticas de arquitectura en la nube garantizará que las aplicaciones sean seguras, rentables y altamente disponibles.

## Referencias y Recursos Adicionales

- [Documentación oficial de Amazon EC2](https://aws.amazon.com/ec2/)
- [Guía para desarrolladores de AWS Lambda](https://docs.aws.amazon.com/lambda/)
- [Guía de usuario de Amazon ECS](https://docs.aws.amazon.com/ecs/)
- [Guía de usuario de Amazon EKS](https://docs.aws.amazon.com/eks/)
- [AWS Compute Blog](https://aws.amazon.com/blogs/compute/)
