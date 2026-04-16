---
title: ¿Qué es un indicador de funcionalidad?
description: Descubra cuáles son los indicadores de características y cómo le permiten activar o desactivar las características de la aplicación durante la ejecución sin tener que volver a implementarlas.
hide: true
exl-id: c4ed4ab5-0d73-4697-b05c-476d6e4010ce
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# ¿Qué es un indicador de funcionalidad? {#what-is-a-feature-flag}

Un indicador de características es un mecanismo que permite activar o desactivar las características de la aplicación durante la ejecución, sin volver a implementar el código.

Los indicadores de características desvinculan la **implementación de código** de la **disponibilidad de características**. Puede enviar código nuevo a producción con la función oculta tras un indicador y, a continuación, activarla cuando esté listo, para todos los usuarios o para un subconjunto de destino.

Esta separación reduce significativamente el riesgo. Los desarrolladores pueden crear y enviar contenido de forma continua con una interrupción mínima, mientras que los equipos de productos conservan el control total sobre cuándo y a quién se vuelve visible una función.

>[!NOTE]
>
>En Marcas, una marca de característica es la unidad atómica más importante de control de características. Se puede usar solo para segmentar una sola característica o combinado con otras marcas en un [grupo de características](feature-groups-to-control-multiple-features.md).

<!-- -->
