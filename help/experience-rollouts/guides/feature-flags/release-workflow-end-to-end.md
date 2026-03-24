---
title: Flujo de trabajo de la versión de extremo a extremo
description: Conozca el flujo de trabajo completo para administrar una versión coordinada en los lanzamientos de Adobe Experience, desde la definición de indicadores de funcionalidades hasta la puesta en marcha.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---


# Flujo de trabajo de la versión de extremo a extremo {#release-workflow}

En esta página se describe la secuencia completa de actividades relacionadas con una versión coordinada gestionada por un Administrador de versiones.

## &#x200B;1. Definición de indicadores de funcionalidades por aplicación {#define-flags}

Cada equipo de productos asigna un **Propietario de la versión del producto** que inicia sesión en la consola Despliegues de experiencias y crea indicadores de características para las aplicaciones que poseen. A continuación, el equipo de productos implementa la lógica condicional en su código, colocando las funciones detrás de estos indicadores.

## &#x200B;2. Creación de la versión {#create-release}

La creación de una nueva versión requiere una solicitud de soporte; no es completamente automática. Póngase en contacto con la asistencia de Experience Rollouts para crear la versión. Proporcione el nombre de la versión, el equipo propietario, el entorno de destino, el objetivo, las aplicaciones participantes y la duración esperada.

Una vez confirmado el lanzamiento, el Release Manager abre la consola y completa la configuración del lanzamiento.

## &#x200B;3. Añadir indicadores de funcionalidades a la versión {#add-flags}

Para cada aplicación añadida a la versión, el propietario de la versión del producto de la aplicación inicia sesión y agrega los indicadores de funciones relevantes a la versión. Estos indicadores representan las funciones que se activarán con la versión.

## &#x200B;4. Configuración de la audiencia {#configure-audience}

El Administrador de versiones selecciona la audiencia para la versión como, por ejemplo, el 1 % de los usuarios de un país específico, todos los usuarios con un dominio de correo electrónico específico o una lista de ID de usuario específicos. Una vez configurada, el Administrador de versiones guarda y publica la versión, que la activa para la audiencia especificada.

## &#x200B;5. Expandir y administrar el despliegue {#expand}

Una vez publicada la versión, el Administrador de versiones puede ajustar las reglas de audiencia para expandir el despliegue gradualmente, supervisar problemas y utilizar los controles de estado de la versión para administrar el ciclo de vida. Consulte [Estados de la versión](release-states.md) para obtener más información.

## Puntos clave {#key-points}

* Todas las aplicaciones participantes implementan su código en producción de forma independiente detrás de indicadores de funciones: no se necesita un tiempo de implementación coordinado.
* La versión es el único punto de control que activa todos los indicadores simultáneamente en todos los equipos.
* La segmentación de audiencia para las versiones de se basa en los atributos del token de autenticación (país, correo electrónico, ID de usuario, porcentaje).

## Consulte también {#see-also}

* [Solicitar una versión](request-a-release.md)
* [Actualizar reglas de audiencia de lanzamiento](update-release-audience-rules.md)
* [Estados de versión](release-states.md)
