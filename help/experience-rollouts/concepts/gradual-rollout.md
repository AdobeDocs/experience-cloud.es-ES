---
title: Despliegue gradual
description: Descubra cómo las implementaciones graduales en Despliegues de experiencias le permiten implementar por fases las funciones en producción de forma segura, con comentarios en tiempo real y un riesgo mínimo.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 2%

---


# Despliegue gradual {#gradual-rollout}

Un despliegue gradual implementa una nueva función en la producción de forma gradual, en lugar de habilitarla para todos los usuarios a la vez. Este método reduce el riesgo, ayuda a administrar la carga del back-end y crea un bucle de retroalimentación estrecho antes del lanzamiento completo.

## Ventajas {#benefits}

**Red de seguridad**
Al realizar primero el lanzamiento en una audiencia pequeña, puede realizar un seguimiento de los comentarios y supervisar el comportamiento en la producción antes de ampliarlo. Si aparecen problemas, el impacto es limitado y la función se puede desactivar inmediatamente, sin cambiar el código ni volver a implementar.

**Administración de carga back-end**
Abrir una función a todos los usuarios simultáneamente puede causar picos repentinos en la carga del servidor. Un despliegue gradual distribuye el aumento del tráfico a lo largo del tiempo, lo que permite que la infraestructura se escale sin problemas.

**Comentarios en tiempo real**
Cada fase del despliegue presenta los comentarios de los usuarios reales. Los equipos pueden actuar en función de esos comentarios (refinar la experiencia, corregir casos excepcionales o ajustar la mensajería) antes de la siguiente fase.

## Funcionamiento {#how-it-works}

Los despliegues de experiencias proporcionan reglas de segmentación granulares para aumentar la exposición del usuario paso a paso. Un despliegue gradual típico puede seguir este patrón:

1. Habilitar la característica para **1%** de usuarios
2. Monitorizar métricas de comentarios y rendimiento
3. Expandir a **10%**, después a **25%**, después a **50%**
4. Alcance de **100%** una vez que se establezca la confianza

En cada paso, una sola acción puede pausar el despliegue o desactivar la función por completo si algo sale mal.

## Consulte también {#see-also}

* [Indicadores de características para habilitar y deshabilitar características](feature-flags-to-enable-disable-features.md)
* [Administración de versiones](release-management.md)
