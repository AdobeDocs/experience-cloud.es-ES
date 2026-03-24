---
title: Resumen de los entornos
description: Obtenga información acerca de los entornos de fase y producción en los Despliegues de experiencias de Adobe y cuándo utilizarlos.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# Resumen de los entornos {#environments}

Los despliegues de experiencias proporcionan entornos independientes para que pueda validar los indicadores de funcionalidades antes de promocionar los cambios a los usuarios activos.

## Entornos disponibles {#available-environments}

| Entorno | Objetivo |
|---|---|
| **Fase** | Pruebas y validación. Utilice este entorno para configurar y probar los indicadores de características antes de habilitarlos en Producción. |
| **Producción** | Despliegues en directo. Los indicadores de funciones configurados aquí se evalúan en función de la base de usuarios real. |

>[!IMPORTANT]
>
>Los cambios realizados en Fase no se transfieren automáticamente a Producción. Los indicadores de funcionalidades y las reglas de audiencia deben configurarse por separado en cada entorno.

## Selección de un entorno {#selecting}

Después de iniciar sesión en la consola Despliegues de experiencia, seleccione el entorno del conmutador de entornos en la parte superior de la interfaz. Asegúrese de que está trabajando en el entorno correcto antes de crear o modificar indicadores de características.

## Prácticas recomendadas {#best-practices}

Siga estas recomendaciones para evitar errores de configuración y proteger la audiencia de producción:

* Cree y pruebe siempre primero los indicadores de características en **Stage**.
* Valide las reglas de audiencia, los despliegues porcentuales y la lógica de segmentación en Fase antes de duplicar en Producción.
* Use [flujo de trabajo entre entornos](../cross-environment/cross-environment-concept.md) para ver y administrar el estado del indicador entre entornos.

## Consulte también {#see-also}

* [Inicie sesión en la consola de](log-in-to-the-console.md)
* [Asociar entornos a una aplicación](../cross-environment/associate-environments.md)
* [Visualización de indicadores de funcionalidades en entornos](../cross-environment/view-feature-flags-across-environments.md)
