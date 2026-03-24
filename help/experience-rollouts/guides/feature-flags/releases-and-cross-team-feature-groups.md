---
title: Versiones y grupos de funciones entre equipos
description: Conozca la diferencia entre las versiones y los grupos de funciones entre equipos en los Despliegues de Adobe Experience y cuándo utilizar cada uno para despliegues coordinados de varios equipos.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---


# Versiones y grupos de funciones entre equipos {#releases-and-cross-team}

Tanto las versiones como los grupos de funciones entre equipos admiten despliegues coordinados en varios equipos y aplicaciones. La elección correcta depende de los requisitos de almacenamiento en caché, las necesidades de segmentación de audiencia y cuánto control desee sobre el proceso.

## Grupos de funciones entre equipos {#cross-team-feature-groups}

Un grupo de funciones entre equipos le permite agrupar indicadores de funciones de aplicaciones propiedad de equipos diferentes y administrarlos con criterios de audiencia enriquecidos.

Características principales:

* **Autoservicio**: no se requiere ninguna solicitud de soporte técnico para crear uno
* **Segmentación de audiencia enriquecida**: admite el conjunto completo de criterios de audiencia (atributos de perfil, variables de contexto, despliegue de porcentaje)
* **No hay límite** en el número que puedes crear
* **Sin almacenamiento en caché**: las evaluaciones de indicadores de características requieren una llamada de API; no se admite el almacenamiento en caché en el nivel de SDK

Para obtener instrucciones de creación detalladas, consulte [Crear un grupo de características entre equipos](create-cross-team-feature-group.md).

## Versiones {#releases}

Una versión está diseñada para inicios grandes y coordinados donde se requiere almacenamiento en caché a nivel de SDK. Las versiones utilizan la segmentación de audiencia basada en token de autenticación.

Características principales:

* **Requiere una solicitud de soporte técnico** — Las versiones no son de autoservicio completo; póngase en contacto con el soporte técnico de los despliegues de experiencia para crear una
* **Almacenamiento en caché de SDK**: todos los datos de la versión se almacenan localmente en la caché del servidor SDK, lo que reduce las llamadas a la API
* **Criterios de audiencia limitados**: las reglas de audiencia se basan en tokens de autenticación (país, correo electrónico, ID de usuario, porcentaje, etc.)
* **Versiones activas limitadas**: puede existir un número finito de versiones activas a la vez; planee cerrar o aprobar las versiones en un plazo de tres meses

## Comparación {#comparison}

| | Grupo de funciones entre equipos | Versión |
|---|---|---|
| Autoservicio | ✓ | Requiere solicitud de soporte |
| Criterios de audiencia enriquecidos | ✓ | Limitado |
| Prueba A/B | ✗ | ✗ |
| Almacenamiento en caché de SDK | ✗ | ✓ |
| Límite activo | Sin límite | Limitado |

## Recomendación {#recommendation}

Si su caso de uso implica una segmentación de audiencia enriquecida y administración de autoservicio, use un **grupo de características entre equipos**. Si los servicios back-end requieren almacenamiento en caché en el nivel de SDK y los criterios de audiencia más simples de las versiones son suficientes, use **release**.

## Consulte también {#see-also}

* [Funciones, grupos de funciones y versiones](features-feature-groups-releases.md)
* [Crear un grupo de funciones entre equipos](create-cross-team-feature-group.md)
* [Solicitar una versión](request-a-release.md)
