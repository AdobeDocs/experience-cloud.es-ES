---
title: Actualizar reglas de audiencia de lanzamiento
description: Obtenga información sobre cómo configurar y actualizar los criterios de audiencia para una versión en los lanzamientos de Adobe Experience, incluidos los tipos de reglas compatibles y cómo combinarlos.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---


# Actualizar reglas de audiencia de lanzamiento {#update-release-audience-rules}

## Acceso a la configuración de audiencia {#access}

Para empezar a configurar quién recibe la versión, vaya a la configuración de audiencia en la consola:

1. Abra la versión en la consola Despliegues de experiencias.
2. Vaya a la ficha **Audiencia**.
3. Habilite la opción junto a **Reglas de audiencia**.
4. Seleccione si desea agregar **reglas de inclusión** (que deberían recibir la versión) o **reglas de exclusión** (que no deberían recibir la versión).

## Criterios de audiencia admitidos {#criteria}

### Tipo de ID {#id-type}

Usuarios de Target según su tipo de cuenta (por ejemplo, cuentas personales o empresariales).

### País {#country}

Usuarios de Target según su país registrado.

### ID de usuario {#user-id}

Segmente a usuarios concretos por su identificador de usuario único (GUID).

### Dirección de correo electrónico {#email}

Usuarios de Target por su dirección de correo electrónico exacta. Para agregar varias direcciones de correo electrónico a la vez, selecciona **in** en la lista desplegable de operadores (en lugar de **is**) y, a continuación:

* Escriba una lista de direcciones separadas por comas en el cuadro de texto o
* Cargar un archivo de `.txt` con una dirección por línea, o
* Cargar un archivo de `.csv` con la lista de direcciones

Si la lista es muy grande, divídala en lotes más pequeños.

### Dominio de correo electrónico {#email-domain}

Segmente a todos los usuarios cuya dirección de correo electrónico pertenezca a un dominio específico (por ejemplo, `yourcompany.com`).

### IP del cliente {#client-ip}

Usuarios de destino según su dirección IP de cliente.

### Porcentaje {#percentage}

Oriente a un porcentaje aleatorio de todos los usuarios, incluidos los no autenticados.

### Porcentaje (solo autenticado) {#percentage-auth}

Oriente un porcentaje aleatorio de usuarios autenticados solamente. Se excluyen los usuarios no autenticados.

## Combinación de varias reglas {#combining-rules}

Puede combinar varios criterios de audiencia utilizando la lógica AND/OR.

**Ejemplos:**

* Para segmentar solamente cuentas de empresa de un dominio específico, combine la regla **ID type** con la regla **Email domain** usando AND.
* Para dirigirse al 10% de los usuarios de un país específico, combine la regla **País** con la regla **Porcentaje**.

Utilice los iconos **+/-** para agregar o quitar condiciones. Para duplicar una condición, seleccione el icono de duplicado situado junto a una regla existente. Para lógica anidada compleja, habilite **Lógica anidada** e introduzca una expresión válida en el cuadro de texto.

## Consulte también {#see-also}

* [Solicitar una versión](request-a-release.md)
* [Flujo de trabajo de la versión de extremo a extremo](release-workflow-end-to-end.md)
* [Estados de versión](release-states.md)
