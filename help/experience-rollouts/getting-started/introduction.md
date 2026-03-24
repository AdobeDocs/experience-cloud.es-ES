---
title: Introducción a los despliegues de experiencias
description: Descubra cómo los lanzamientos de Adobe Experience proporcionan un sistema de versiones controladas para implementar funciones de forma progresiva en audiencias de destino.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Introducción a los despliegues de experiencias {#introduction}

Los lanzamientos de experiencias de Adobe son un sistema de versiones controladas que permite a los equipos implementar funciones hasta la producción, manteniendo un control preciso sobre quién las ve y cuándo. Una función puede estar en producción e invisible para los usuarios finales (y luego activarse progresivamente para una audiencia de destino) sin necesidad de volver a implementarla.

## Del desarrollo a la producción {#dev-to-prod}

Los despliegues de experiencias admiten el recorrido completo de una función desde su primera fase de desarrollo hasta la disponibilidad general:

1. **Pruebas para desarrolladores**: un desarrollador crea un indicador de características, implementa su código en cualquier entorno y realiza pruebas únicamente en su propia sesión. Ningún otro usuario se ve afectado y no se requiere bifurcación.

2. **Vista previa segmentada**: un propietario de producto vincula una audiencia al indicador de características, lo que hace que la característica esté disponible para un subconjunto definido de usuarios (por ejemplo, participantes de la versión beta o una región específica) para su validación y comentarios.

3. **Despliegue gradual**: La característica se abre progresivamente a una audiencia más amplia (1%, 10%, 50%, 100%) con la capacidad de pausar, ajustar o desactivar la característica en cualquier paso.

4. **Disponibilidad general**: una vez completada la validación, la característica estará disponible para todos los usuarios.

## Funcionalidades principales {#capabilities}

Experience Rollouts es una plataforma de administración de funciones que proporciona lo siguiente:

* **Indicadores de características**: active o desactive cualquier característica en tiempo de ejecución para una audiencia de destino, sin volver a implementar el código.

* **Segmentación de audiencia**: controla quién ve una característica mediante datos de perfil de usuario, reglas basadas en porcentajes, direcciones de correo electrónico, dominios de correo electrónico, direcciones IP o atributos contextuales.

* **Grupos de características**: agrupe varios indicadores de características relacionados en las aplicaciones y adminístrelos como una sola unidad, para que la misma audiencia vea una experiencia coherente.

* **Versiones**: coordine despliegues grandes entre equipos mediante la agrupación de indicadores de características de varios equipos y aplicaciones en un único evento de lanzamiento.

* **Despliegues graduales**: Fase de entrega de funciones incrementalmente para reducir el riesgo, recopilar comentarios y administrar la carga back-end.

* **Interruptor inactivo**: desactive cualquier característica inmediatamente si se detecta un problema, sin cambiar el código ni volver a implementarlo.
