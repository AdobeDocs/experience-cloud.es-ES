---
title: Analytics
description: Obtenga información sobre cómo habilitar y utilizar el panel de análisis integrado en Banderas para rastrear el rendimiento de los indicadores de funcionalidades y medir el impacto en el despliegue.
hide: true
exl-id: edddca99-f263-461b-a16f-b46ee7c15f6c
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---

# Analytics {#analytics}

Marcas proporciona análisis integrados para marcas de características, grupos de características, grupos de características de equipos cruzados y versiones. Utilice el panel de análisis para comprender cuántos usuarios participan en el despliegue y cómo se comparan la variante y los grupos de control. También puede exportar datos de indicadores a su entorno de informes preferido para analizarlos junto con el resto de los datos de Adobe.

## Habilitar análisis {#enable}

Analytics debe estar habilitado en dos niveles:

1. **Nivel de aplicación** — Póngase en contacto con el soporte técnico de Marcas para habilitar Analytics para su aplicación.
2. **Nivel de indicador de funcionalidad**: una vez que Analytics esté habilitado para su aplicación, marque la casilla de verificación **Activar Analytics** en la pestaña **Detalles básicos** de cada indicador de característica que desee rastrear.

>[!NOTE]
>
>De forma predeterminada, Analytics puede habilitar hasta 20 indicadores de características por aplicación. Póngase en contacto con el servicio de asistencia si necesita aumentar este límite.

## Ver el panel de análisis {#dashboard}

Una vez habilitado el análisis, todas las marcas de características, los grupos de características y las versiones de la aplicación empezarán a rastrear los datos. Para acceder al panel, seleccione **Resultados** en el indicador de características, el grupo de características o la versión que desee analizar.

Se muestra el panel:

* **Participantes**: número total de usuarios aptos para la función (variante + grupo de control combinados)
* **Grupo de control**: número de usuarios asignados al grupo de control (usuarios que recibieron la experiencia predeterminada)
* **Gráfico de nivel de día**: gráficos de líneas diarios que muestran la inscripción en la variante y el grupo de control a lo largo del tiempo; los marcadores indican cuándo se actualizó la configuración del indicador de funcionalidad
* **Análisis de nivel de variante**: recuento acumulado de usuarios inscritos en el grupo de control y en cada variante

Para los grupos de características y las versiones, seleccione la lista desplegable **Resultados** para elegir una aplicación y ver los análisis de esa aplicación. Analytics solo está disponible para aplicaciones que lo tienen habilitado.

## Consulte también {#see-also}

* [Creación de la primera marca de funcionalidad](create-your-first-feature-flag.md)
* [Pruebas A/B con indicadores de funcionalidades](a-b-testing.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)

<!-- -->
