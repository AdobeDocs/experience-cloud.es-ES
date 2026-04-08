---
title: Uso del contexto en las reglas de audiencia
description: Obtenga información sobre cómo utilizar variables de contexto en reglas de audiencia para indicadores de funcionalidades y grupos de funcionalidades en Despliegues de experiencias de Adobe.
exl-id: 0367f475-9209-4d53-86b4-a739a73a23a7
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Uso del contexto en las reglas de audiencia {#context-in-audience-rules}

Las variables de contexto son valores proporcionados por la aplicación cliente durante la ejecución. Permiten segmentar usuarios en función de información dinámica a nivel de sesión, como el idioma activo del usuario, el tipo de dispositivo o el estado de la aplicación.

Las variables de contexto son relevantes para los clientes web y móviles.

## Funcionamiento de las variables de contexto {#how-context-works}

La aplicación pasa variables de contexto a los despliegues de experiencia al evaluar un indicador de funcionalidad. En la consola se definen reglas que comprueban estos valores, y la plataforma los utiliza en el momento de la evaluación para determinar si el usuario cumple los requisitos.

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

## Consulte también {#see-also}

* [Audiencia en indicadores y grupos de características](audience-in-feature-flags-and-feature-groups.md)
* [Agregar reglas de porcentaje en criterios de audiencia](adding-percentage-rules.md)
