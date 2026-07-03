# Despliegue de Infraestructura Cloud de WordPress para Comercial Nova

Este repositorio contiene la documentación técnica, diagramas de arquitectura y matrices de configuración correspondientes al caso de estudio de la empresa **Comercial Nova**, enfocado en garantizar un entorno web de alta disponibilidad, seguridad y escalabilidad utilizando Amazon Web Services (AWS).

## 👥 Integrantes
* Rossel Teofilo Turpo Maza

## 📋 Descripción del Problema
Comercial Nova requería la migración y despliegue de su plataforma web corporativa basada en WordPress hacia una infraestructura en la nube que resuelva problemas históricos de disponibilidad, rendimiento ante picos de tráfico y aislamiento de datos críticos del negocio.

## 🏗️ Resumen de la Solución Arquitectónica
Se diseñó e implementó una arquitectura basada en el principio de mínimo privilegio y separación de capas:
* **Capa de Presentación / Aplicación:** Servidor web Apache con PHP-FPM corriendo sobre una instancia Amazon EC2 con Amazon Linux 2023.
* **Capa de Datos:** Motor de base de datos relacional aislado para la persistencia del CMS de WordPress.
* **Red Segura:** Segmentación de tráfico mediante Grupos de Seguridad (Security Groups) específicos para el servidor web (Puertos 80/22) y el motor de datos (Puerto 3306).

## 🚀 Limitaciones Conocidas y Soluciones de Contingencia
* **Aislamiento de Capa de Datos por Red Interna:** Durante el despliegue en entornos educativos restrictivos de AWS, la comunicación entre las subredes públicas y privadas de la VPC automatizada presentó bloqueos estrictos de ruteo interno. Como plan de contingencia técnico inmediato para garantizar la continuidad del servicio de la aplicación, se configuró y optimizó una instancia de base de datos relacional optimizada a nivel local (`localhost`) dentro de la misma EC2. Esto eliminó la latencia y los fallos de pasarela (*Gateway Timeout*), asegurando la entrega inmediata del entorno de producción.

## 📂 Estructura del Repositorio
* `/wordpress` - Manuales de instalación, comandos de aprovisionamiento de paquetes y evidencias del blog en vivo.
* `/seguridad` - Matriz de accesos detallada por puertos y protocolos.
* `/costos` - Análisis de estimación de inversión cloud mensual y estrategias de optimización financiera (Rightsizing, automatización de apagado).
