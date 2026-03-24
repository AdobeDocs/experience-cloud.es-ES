---
title: Analytics
description: Obtenga información sobre cómo habilitar y utilizar el tablero de análisis integrado en los lanzamientos de Adobe Experience para rastrear el rendimiento del indicador de funciones y medir el impacto en el despliegue.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 1%

---


# Analytics {#analytics}

Los despliegues de experiencias proporcionan análisis integrados para indicadores de funcionalidades, grupos de funcionalidades, grupos de funcionalidades entre equipos y versiones. Utilice el panel de análisis para comprender cuántos usuarios participan en el despliegue y cómo se comparan la variante y los grupos de control.

## Habilitar análisis {#enable}

Analytics debe estar habilitado en dos niveles:

1. **Nivel de aplicación**: póngase en contacto con el equipo de asistencia de Experience Rollouts para habilitar Analytics para su aplicación.
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
