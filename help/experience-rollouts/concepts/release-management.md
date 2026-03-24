---
title: Administración de versiones en despliegues de experiencias
description: Descubra cómo la administración de versiones en Despliegues de Experience coordina la entrega de funciones de varios equipos a través de implementaciones oscuras, pruebas de producción e implementaciones graduales.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---


# Administración de versiones en despliegues de experiencias {#release-management}

Una versión principal típica implica varios equipos y varias aplicaciones, cada una con sus propias cronologías y dependencias de implementación. Los despliegues de experiencia proporcionan un modelo de administración de versiones que permite a los equipos trabajar de forma independiente sin dejar de ofrecer una versión coordinada y controlada a los usuarios finales.

## Funcionalidades clave {#capabilities}

### Implementaciones oscuras {#dark-deployments}

Los equipos ya no necesitan cronometrar la implementación de su código con una fecha de lanzamiento específica. El código se puede implementar en producción con indicadores de funciones en cualquier momento. Los usuarios finales no verán ningún cambio hasta que se active la versión. Los equipos pueden desplegarse a su propio ritmo, seguros de que nada se expone prematuramente.

### Pruebas en producción {#testing-in-production}

Una vez que el código se implementa en producción (implementación oscura), los despliegues de experiencia pueden abrir las funciones a probadores internos y equipos de control de calidad. Esto permite realizar pruebas completas con el entorno de producción y los datos de producción reales, sin ningún riesgo de exponer los cambios a los usuarios finales.

### Despliegue gradual {#gradual-rollout}

Cuando una versión está lista para su lanzamiento, no tiene que ser todo o nada. Los despliegues de experiencias permiten controlar el despliegue de forma progresiva, empezando por un pequeño porcentaje de usuarios, monitorizando los comentarios y el rendimiento, y ampliando la audiencia con el paso del tiempo. Esto reduce la presión sobre los sistemas back-end y proporciona a los equipos tiempo para responder a cualquier problema antes de la exposición completa.

### Activación coordinada {#coordinated-activation}

Varios equipos desarrollan características de forma independiente, cada uno detrás de sus propios indicadores de características. Una vez que todos los equipos están listos, los Despliegues de experiencias proporcionan un único punto de control para activar todos los indicadores en equipos y aplicaciones de forma simultánea o gradual, de modo que la versión se ponga en marcha como una experiencia unificada.

## Consulte también {#see-also}

* [Concepto de administración de versiones](concept-of-release-management.md)
* [Grupos de funciones para controlar varias funciones](feature-groups-to-control-multiple-features.md)
* [Despliegue gradual](gradual-rollout.md)
