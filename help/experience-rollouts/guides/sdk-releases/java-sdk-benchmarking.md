---
title: pruebas comparativas de SDK
description: Revise los resultados de las pruebas comparativas de Java SDK para los lanzamientos de Adobe Experience, incluidas las mediciones del tiempo de respuesta en distintos números de indicadores de funciones en condiciones de carga típicas.
source-git-commit: 8b8b5db1a28af3a3ac29aecf26482f70eb84c714
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 7%

---


# pruebas comparativas de SDK {#sdk-benchmarking}

El SDK de Java de despliegues de experiencia está diseñado para ofrecer a los equipos de integración una estimación fiable de los recursos y los tiempos de respuesta que se pueden esperar cuando SDK se ejecuta dentro de su infraestructura.

## Entorno de prueba {#test-environment}

La evaluación comparativa se realizó en una aplicación de arranque de primavera con la siguiente configuración fija:

* **Núcleos de CPU:** 8
* **Memoria JVM:** 4096 MB

## Suposiciones de prueba {#test-assumptions}

Las siguientes condiciones se mantuvieron constantes en todas las ejecuciones de referencia:

* Indicadores de funcionalidad probados: de 8 a 128
* Variables de contexto por indicador de característica: 2 (tipo `STRING`, longitud 36 caracteres)
* Carga media: 15 000 solicitudes por minuto (RPM)
* Hilos activos: 100

## Resultados {#results}

La tabla siguiente muestra el tiempo de respuesta del percentil 99.99 para las llamadas a `getFeatures()` a medida que aumenta el número de indicadores de características:

| Número de indicadores de funcionalidad | Variables de contexto por indicador | Tiempo de respuesta (ms, p99.99) |
|---|---|---|
| 8 | 2 | &lt; 0.5 |
| 16 | 2 | &lt; 0.5 |
| 32 | 2 | &lt; 0.5 |
| 64 | 2 | &lt; 1 |
| 128 | 2 | &lt; 1 |

## Interpretación de los resultados {#interpretation}

Los puntos de referencia anteriores representan el rendimiento en las condiciones de ensayo específicas descritas. Dado que SDK se ejecuta dentro de la infraestructura de la aplicación, los tiempos de respuesta reales variarán en función de factores específicos del entorno:

* CPU disponible y número de núcleos
* Tamaño de pila de JVM y comportamiento de recopilación de basura
* Disponibilidad de subprocesos y cambio de contexto
* Carga actual del sistema en el momento de la solicitud

Utilice estas cifras como línea de base de planificación en lugar de como objetivos de rendimiento garantizados para su entorno de producción.

## Consulte también {#see-also}

* [Guía de integración de Java SDK](java/java-sdk-integration-guide.md)
* [Notas de la versión de Java SDK](java/java-sdk-release-notes.md)
* [SDK](../integrate/sdks.md)
