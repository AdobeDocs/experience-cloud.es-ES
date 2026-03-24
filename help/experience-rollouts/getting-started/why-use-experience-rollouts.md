---
title: Razones para utilizar los despliegues de experiencias
description: Conozca los casos de uso clave de los lanzamientos de experiencias de Adobe, desde las pruebas selectivas de funciones hasta las versiones coordinadas de varias aplicaciones.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 1%

---


# Razones para utilizar los despliegues de experiencias {#why-use}

Los despliegues de experiencias son la herramienta adecuada siempre que necesite controlar quién ve una función y cuándo lo hace, ya sea realizando pruebas en desarrollo, validando con un subconjunto de usuarios o coordinando una versión de gran tamaño en varios equipos.

## Casos de uso comunes {#use-cases}

**Pruebas selectivas durante el desarrollo**
Pruebe una función con su propia sesión, mientras que otros desarrolladores continúan su trabajo sin verse afectados. No se requiere bifurcación de código complejo.

**Despliegue escalonado con comentarios del usuario**
Primero publique una función para un grupo pequeño de usuarios. Recopile comentarios, aborde problemas y amplíe la audiencia gradualmente antes de una versión completa.

**Despliegue gradual en producción**
Abra una nueva función progresivamente: 1 %, 10 %, 50 % y, a continuación, 100 % de los usuarios. Monitorice el rendimiento y la respuesta del usuario en cada paso. Si algo sale mal, apáguelo inmediatamente.

**Administración de carga back-end**
Despliegue gradual a fin de evitar picos de tráfico repentinos en los servicios back-end, en lugar de exponer a todos los usuarios a una nueva función a la vez.

**Versiones coordinadas de varias aplicaciones**
Habilite una función simultáneamente en varias aplicaciones y equipos para un conjunto específico de usuarios. Los despliegues de experiencias garantizan la coherencia en toda la superficie de lanzamiento.

**Versiones diferidas**
Implemente el código en producción con antelación y, a continuación, active la función en un momento preciso (por ejemplo, al inicio de un evento de lanzamiento de producto) sin ningún cambio de código de última hora.

**Interruptor inactivo**
Si se descubre un problema después del lanzamiento, desactive la función instantáneamente sin necesidad de una revisión o una nueva implementación.
