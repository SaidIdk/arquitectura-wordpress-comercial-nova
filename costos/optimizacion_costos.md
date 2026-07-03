# Plan de Análisis y Optimización de Costos Cloud

Basado en el despliegue actual de la infraestructura para Comercial Nova, se proponen tres estrategias técnicas concretas para maximizar la eficiencia del gasto y optimizar la inversión en la nube:

## 1. Rightsizing de Instancias de Cómputo
* **Acción:** Cambiar la familia de instancias EC2 actuales a tipos basados en procesadores AWS Graviton (ej. `t4g.micro`).
* **Justificación:** Los procesadores Graviton ofrecen hasta un 40% mejor rendimiento por cada dólar invertido en comparación con las arquitecturas tradicionales x86, lo que reduce el costo directo de cómputo mensual manteniendo la fluidez del CMS.

## 2. Implementación de Políticas de Horarios de Apagado (Instance Scheduling)
* **Acción:** Configurar automatizaciones mediante AWS Lambda para automatizar el encendido y apagado de la instancia de desarrollo.
* **Horario propuesto:** Apagado automático de lunes a viernes a las 20:00 horas y encendido a las 08:00 horas, manteniéndola inactiva los fines de semana.
* **Justificación:** Reduce las horas de facturación de la instancia EC2 en aproximadamente un 60% mensual, evitando pagar por recursos de cómputo cuando el equipo técnico no está laborando.

## 3. Automatización del Ciclo de Vida del Almacenamiento (Amazon S3)
* **Acción:** Definir reglas de ciclo de vida en los buckets de almacenamiento persistente destinados a los respaldos diarios del sitio web y la base de datos.
* **Estrategia:** Configurar la transición automática de archivos de respaldo hacia clases de almacenamiento de menor costo como *S3 Standard-Infrequent Access (IA)* a los 30 días, y posterior depuración o movimiento a *Amazon Glacier* a los 90 días.
* **Justificación:** Minimiza drásticamente el costo por GB almacenado de datos históricos que rara vez necesitan ser consultados.
