---
title: Indicadores de características para habilitar y deshabilitar características
description: Descubra cómo los indicadores de funcionalidades en los Despliegues de experiencias le permiten controlar la disponibilidad de las funcionalidades, administrar las dependencias y reducir el riesgo de implementación.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# Indicadores de características para habilitar y deshabilitar características {#feature-flags}

Los indicadores de características permiten activar o desactivar las características de la aplicación durante la ejecución sin volver a implementar el código. También separan las implementaciones de código de la disponibilidad de funciones: el nuevo código se puede implementar en producción detrás de un indicador y se activa solo cuando esté listo.

Esta práctica reduce significativamente el riesgo. Los desarrolladores pueden desarrollar con agilidad y confianza, mientras que los equipos de productos conservan el control sobre el tiempo y la audiencia de cada lanzamiento de funciones.

## Administrar dependencias durante el desarrollo {#manage-dependencies}

Los indicadores de funciones ayudan a administrar las dependencias al realizar pruebas en ciclos de desarrollo rápidos. Los desarrolladores invierten menos tiempo en resolver conflictos de combinación y refactorización, y más tiempo en ofrecer funciones.

Dado que la disponibilidad de las funciones se controla fuera del código, se pueden desarrollar varias funciones en paralelo, sin ramificaciones complejas. Las funciones individuales pueden moverse hacia delante o hacia atrás de forma independiente, sin afectar a otras funciones en curso.

## Implementaciones oscuras {#dark-deployments}

Dado que las decisiones de habilitar y deshabilitar se toman fuera de la base de código, puede implementar el código en producción manteniendo la función invisible para los usuarios finales. Esto se denomina **implementación oscura**.

Las implementaciones oscuras le permiten insertar el código de forma segura en el entorno de producción, probarlo en el entorno en directo en condiciones reales e implementarlo cuando lo desee, no cuando la programación de implementación lo obligue a hacerlo.

## Despliegue gradual {#gradual-rollout}

Cuando esté listo para el lanzamiento, puede usar una marca de características para realizar un **despliegue gradual**: abra la característica para el 1% de los usuarios, mida los comentarios y el rendimiento, y luego incremente progresivamente.

Este enfoque gradual le proporciona un control más estricto sobre la experiencia que ofrece y un bucle de comentarios más rápido con los usuarios reales, para que sus equipos puedan responder rápidamente antes de una versión completa.

## Interruptor de apagado {#kill-switch}

Si una versión no sale según lo planeado (comentarios desfavorables, un error o un problema de rendimiento), puedes desactivar la característica inmediatamente usando el indicador de características como **interruptor de desactivación**. No es necesario cambiar el código ni volver a implementarlo.

## Ciclo de indicador de funcionalidad {#lifecycle}

Un indicador de funcionalidad en los despliegues de experiencia sigue este ciclo de vida típico:

1. Un desarrollador crea un indicador de funciones y lo prueba de forma aislada, sin exponerlo a otros usuarios.
2. El propietario de un producto vincula una audiencia al indicador, lo que hace que la función sea visible para un conjunto definido de usuarios externos.
3. El indicador se agrega opcionalmente a un [grupo de características](feature-groups-to-control-multiple-features.md) que se va a administrar junto con los indicadores relacionados.
4. El indicador se agrega opcionalmente a una [versión](release-management.md) para la coordinación entre equipos.
