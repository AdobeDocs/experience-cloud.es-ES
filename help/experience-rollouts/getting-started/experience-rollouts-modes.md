---
title: Modos de despliegues de experiencia
description: Obtenga información acerca de los dos modos de segmentación de funciones en los Despliegues de experiencias de Adobe (segmentación por usuarios y por organizaciones) y cuándo usar cada uno.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 3%

---


# Modos de despliegues de experiencia {#modes}

Los despliegues de experiencias proporcionan dos modos de segmentación de funciones distintos. Cada una tiene un propósito diferente de control de versiones y está diseñada para un tipo específico de aplicación o caso de uso.

>[!TIP]
>
>Elija el modo en función de lo que esté controlando: sesiones de usuario individuales o ámbito de organización y entorno.

## Segmentación a nivel de usuario {#user-level}

### Información general {#user-level-overview}

La segmentación por usuarios permite el despliegue de funciones en el nivel de usuario individual. Admite una segmentación precisa de usuarios específicos, probadores internos, usuarios limitados y despliegues graduales basados en porcentajes.

Este modo es más adecuado para las aplicaciones que necesitan variar la experiencia en función de quién ha iniciado sesión.

### Cuándo usar {#user-level-when}

Utilice el direccionamiento a nivel de usuario cuando desee:

* Habilitar una función para usuarios específicos
* Ejecución de experimentos A/B
* Realice pruebas en condiciones normales con un grupo pequeño antes de un despliegue más amplio
* Implementar gradualmente una función según el porcentaje de usuarios
* Ajustar la experiencia en función de atributos de usuario individuales (como dominio de correo electrónico o datos de perfil)

### Limitaciones {#user-level-limitations}

La segmentación a nivel de usuario no está diseñada para los siguientes casos:

* No controla las funciones a nivel de organización, entorno o región
* No está diseñado para la activación de funciones en todo el inquilino o la activación de derechos

## Segmentación a nivel de organización y entorno {#org-level}

### Información general {#org-level-overview}

La segmentación a nivel de organización permite el despliegue de funciones en la organización, el entorno y la región. Controla la disponibilidad de funciones en organizaciones completas o entornos de implementación específicos, en lugar de hacerlo para usuarios individuales.

Este modo está diseñado para funciones de acceso a nivel empresarial y despliegues específicos del entorno.

### Cuándo usar {#org-level-when}

Utilice la segmentación a nivel de organización cuando desee:

* Habilitar una función para toda una organización
* Control de la disponibilidad de las funciones por entorno (por ejemplo, fase o producción)
* Realización de un despliegue regional
* Funciones de puerta basadas en derechos o nivel de suscripción

### Limitaciones {#org-level-limitations}

La segmentación a nivel de organización y entorno no está diseñada para los siguientes escenarios:

* No admite segmentación basada en perfiles de usuario enriquecidos
* No admite el despliegue basado en porcentajes en el nivel de usuario individual
* No destinado a experimentación o pruebas A/B

## Comparación {#comparison}

| Dimensión | Segmentación a nivel de usuario | Segmentación a nivel de organización y entorno |
|---|---|---|
| Ámbito de control | Usuario individual | Organización, entorno y región |
| Base de segmentación | Perfil de usuario y atributos | Organización y contexto de entorno |
| Despliegue porcentual | Sí | No |
| Prueba A/B | Sí | No |
| Acceso a Enterprise | No | Sí |

## Elección del modo correcto {#choosing}

* Si su pregunta es *&quot;¿Qué usuarios deben ver esta característica?&quot;* → Usar **direccionamiento a nivel de usuario**
* Si su pregunta es *&quot;¿Qué organizaciones o entornos deben tener esta característica?&quot;* → Usar **organización y direccionamiento a nivel de entorno**
