---
title: Uso del contexto en las reglas de audiencia
description: Obtenga información sobre cómo utilizar variables de contexto en reglas de audiencia para indicadores de funcionalidades y grupos de funcionalidades en Despliegues de experiencias de Adobe.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Uso del contexto en las reglas de audiencia {#context-in-audience-rules}

Las variables de contexto son valores proporcionados por la aplicación cliente durante la ejecución. Permiten segmentar usuarios en función de información dinámica a nivel de sesión, como el idioma activo del usuario, el tipo de dispositivo o el estado de la aplicación, criterios que no forman parte del perfil persistente del usuario.

Las variables de contexto son relevantes para los clientes web, de escritorio y móviles.

## Funcionamiento de las variables de contexto {#how-context-works}

La aplicación pasa variables de contexto a los despliegues de experiencia al evaluar un indicador de funcionalidad. En la consola se definen reglas que comprueban estos valores, y la plataforma los utiliza en el momento de la evaluación para determinar si el usuario cumple los requisitos.

Si define condiciones en las secciones **Perfil** y **Contexto** de las reglas de audiencia, todas las condiciones de perfil se combinan con todas las condiciones de contexto mediante la lógica AND.

## Tipos de variables de contexto {#variable-types}

### Tipo predefinido (lista) {#predefined-type}

Una variable de contexto con un conjunto fijo de valores permitidos, como una lista de idiomas o países.

Operadores disponibles: **Is**, **Is not equal to**, **Exists**, **In**

### Tipo entero {#integer-type}

Variable de contexto que contiene un valor numérico.

Operadores disponibles: **Mayor que**, **Mayor o igual que**, **Es**, **Menor que**, **Menor o igual que**

### Tipo de cadena {#string-type}

Variable de contexto que contiene un valor de texto de forma libre.

Operadores disponibles: **Is**, **Is not equal to**

## Añadir una variable de contexto {#adding-context-variable}

Para agregar una variable de contexto a una regla de audiencia:

1. Abra la marca de características o el grupo de características en la consola.
2. Vaya a la ficha **Audiencia**.
3. En **Contexto**, agregue una nueva condición.
4. Seleccione la variable de contexto, el operador y el valor.

Si la variable de contexto que necesita no aparece en la lista, puede crear una nueva de forma automática desde la sección de administración de variables de contexto de la consola.

>[!NOTE]
>
>Cuando las variables de contexto se incluyen en los criterios de audiencia, la calculadora de audiencias **Audience Calculator** no devuelve un recuento estimado, ya que los valores de contexto se determinan durante la ejecución y no se pueden predecir con antelación.

## Consulte también {#see-also}

* [Audiencia en indicadores y grupos de características](audience-in-feature-flags-and-feature-groups.md)
* [Agregar reglas de porcentaje en criterios de audiencia](adding-percentage-rules.md)
* [Regla de audiencia con variable de contexto IP de cliente](clientip-rule.md)
