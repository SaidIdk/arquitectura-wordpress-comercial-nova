# Matriz de Accesos y Endurecimiento de Seguridad - Comercial Nova

Para cumplir con el principio de mínimo privilegio y garantizar la seguridad del portal corporativo, la infraestructura en AWS se segmentó utilizando Grupos de Seguridad (Security Groups) específicos para controlar el tráfico entrante y saliente.

## 1. Grupo de Seguridad del Servidor Web (EC2)
Este grupo controla los accesos directos hacia la instancia de cómputo que aloja la aplicación:

| Tipo de Tráfico | Puerto | Protocolo | Origen / Destino | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| **Entrada (Inbound)** | 80 | TCP (HTTP) | `0.0.0.0/0` | Permite el acceso público de usuarios y clientes de Comercial Nova al portal web. |
| **Entrada (Inbound)** | 22 | TCP (SSH) | `0.0.0.0/0` | Habilitado temporalmente para la administración segura, inyección del stack de software y depuración en la terminal. |
| **Salida (Outbound)** | Todos | Todos | `0.0.0.0/0` | Permite que el servidor descargue actualizaciones de paquetes del sistema operativo y dependencias de WordPress. |

## 2. Aislamiento y Contingencia de la Capa de Datos
Durante el despliegue en la infraestructura cloud, la comunicación externa entre subredes restringidas generó un bloqueo de red interna (*Gateway Timeout* en el puerto `3306`). 

Como **estrategia de endurecimiento de seguridad y plan de contingencia inmediato**, se implementó el motor de base de datos relacional de manera local (`localhost`). Esto mitigó los riesgos de exposición en la red al cerrar completamente el puerto 3306 hacia internet, aislando los datos críticos del negocio dentro de la propia instancia de aplicación.
