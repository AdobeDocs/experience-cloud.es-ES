---
title: ¿Qué es un indicador de funcionalidad?
description: Descubra cuáles son los indicadores de características y cómo le permiten activar o desactivar las características de la aplicación durante la ejecución sin tener que volver a implementarlas.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# ¿Qué es un indicador de funcionalidad? {#what-is-a-feature-flag}

Un indicador de características es un mecanismo que permite activar o desactivar las características de la aplicación durante la ejecución, sin volver a implementar el código.

Los indicadores de características desvinculan la **implementación de código** de la **disponibilidad de características**. Puede enviar código nuevo a producción con la función oculta tras un indicador y, a continuación, activarla cuando esté listo, para todos los usuarios o para un subconjunto de destino.

Esta separación reduce significativamente el riesgo. Los desarrolladores pueden crear y enviar contenido de forma continua con una interrupción mínima, mientras que los equipos de productos conservan el control total sobre cuándo y a quién se vuelve visible una función.

>[!NOTE]
>
>En los despliegues de experiencias, un indicador de funcionalidad es la unidad atómica más importante de control de funciones. Se puede usar por sí solo para segmentar una sola característica o combinarlo con otras marcas en un [grupo de características](feature-groups-to-control-multiple-features.md) o [versión](release-management.md).
