---
title: Introducción a las marcas
description: Descubra cómo Marcas en Adobe Target proporciona un sistema de versiones controladas para implementar funciones de forma progresiva en audiencias de destino.
hide: true
exl-id: befe7899-096d-4f74-a5a2-35b1fc3cbc58
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Introducción a las marcas {#introduction}

>[!AVAILABILITY]
>
>Marcas se encuentra actualmente en Beta y está disponible para los clientes de Adobe Target. Póngase en contacto con su representante de Adobe para solicitar acceso.

Las marcas en Adobe Target son un sistema de versión controlada que permite a los equipos implementar funciones hasta la producción, manteniendo un control preciso sobre quién las ve y cuándo. Una función puede estar en producción e invisible para los usuarios finales (y luego activarse progresivamente para una audiencia de destino) sin necesidad de volver a implementarla.

## Del desarrollo a la producción {#dev-to-prod}

Flags admite el recorrido completo de una función desde su primera fase de desarrollo hasta su disponibilidad general:

1. **Pruebas para desarrolladores**: un desarrollador crea un indicador de características, implementa su código en cualquier entorno y realiza pruebas únicamente en su propia sesión. Ningún otro usuario se ve afectado y no se requiere bifurcación.

2. **Vista previa segmentada**: un propietario de producto vincula una audiencia al indicador de características, lo que hace que la característica esté disponible para un subconjunto definido de usuarios (por ejemplo, participantes de la versión beta o una región específica) para su validación y comentarios.

3. **Despliegue gradual**: La característica se abre progresivamente a una audiencia más amplia (1%, 10%, 50%, 100%) con la capacidad de pausar, ajustar o desactivar la característica en cualquier paso.

4. **Disponibilidad general**: una vez completada la validación, la característica estará disponible para todos los usuarios.

## Funcionalidades principales {#capabilities}

Banderas es una plataforma de administración de funciones que proporciona lo siguiente:

* **Indicadores de características**: active o desactive cualquier característica en tiempo de ejecución para una audiencia de destino, sin volver a implementar el código.

* **Segmentación de audiencia**: controla quién ve una característica mediante datos de perfil de usuario, reglas basadas en porcentajes, direcciones de correo electrónico, dominios de correo electrónico, direcciones IP o atributos contextuales.

* **Grupos de características**: agrupe varios indicadores de características relacionados en las aplicaciones y adminístrelos como una sola unidad, para que la misma audiencia vea una experiencia coherente.

* **Versiones**: coordine despliegues grandes entre equipos mediante la agrupación de indicadores de características de varios equipos y aplicaciones en un único evento de lanzamiento.

* **Despliegues graduales**: Fase de entrega de funciones incrementalmente para reducir el riesgo, recopilar comentarios y administrar la carga back-end.

* **Interruptor inactivo**: desactive cualquier característica inmediatamente si se detecta un problema, sin cambiar el código ni volver a implementarlo.

* **Compatibilidad con AEP SDK**: Las marcas se implementan a través de AEP Web SDK y AEP Mobile SDK, lo que permite una evaluación coherente de las marcas en las aplicaciones web y móviles.

<!-- -->
