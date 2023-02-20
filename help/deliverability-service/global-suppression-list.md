---
title: Lista global de supresión
description: Descubra la lista de supresión global
hide: true
source-git-commit: a946cfb1027896f6e45aaf88d25ad7114d6b5ac6
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 2%

---

# Lista global de supresión {#global-suppression-list}

Una lista de supresión consiste en direcciones de correo electrónico que los clientes desean excluir de sus envíos, ya que el envío a estos contactos podría dañar su reputación de envío y las tasas de envío. Actualmente, Adobe mantiene una lista actualizada de las direcciones de correo electrónico incorrectas conocidas que se han demostrado perjudiciales para la participación y la reputación del correo, y garantiza que los correos electrónicos no se envíen a ellas. Esta lista se administra en una lista global de supresión que es común en todos los clientes de Adobe. Las direcciones y los nombres de dominio contenidos en la lista de supresión global están ocultos. En los informes de envío solo se indica el número de destinatarios excluidos.

Ahora es posible administrar la lista de supresión global desde una interfaz disponible internamente. Esta lista la mantendrán únicamente los consultores de entregas. La lista de supresión global puede incluir direcciones de correo electrónico o de dominio.

## Acceso a la lista de supresión global

Para acceder a la lista detallada de direcciones de correo electrónico y dominios excluidos, vaya a **[!UICONTROL Lista de supresión global]**.

>[!CAUTION]
>
>Los permisos para ver, exportar y administrar la lista de supresión global dependen de la lista de distribución a la que esté asignado. Más información

Se muestran dos pestañas: **[!UICONTROL Correo electrónico]** y **[!UICONTROL Dominio]**.

Los filtros están disponibles para ayudarle a navegar por la lista.

## Adición de direcciones y dominios

Actualmente hay dos formas de agregar direcciones a la lista de supresión global:

* Lista depurada por el equipo de entrega.
* Lista proporcionada por el proveedor de servicios de terceros Blackbox.

Puede añadir direcciones de correo electrónico o dominios [de una en una](#add-one-address-or-domain)o [en modo masivo](#upload-csv-file) mediante la carga de un archivo CSV.

Para ello, seleccione la **[!UICONTROL Añadir correo electrónico o dominio]** , siga uno de los métodos que se describen a continuación.

### Añadir una dirección o un dominio {#add-one-address-or-domain}

1. Seleccione el **[!UICONTROL Uno por uno]** .

1. Elija el tipo de dirección: **[!UICONTROL Dirección de correo electrónico]** o **[!UICONTROL Dirección del dominio]**.

1. Introduzca la dirección de correo electrónico o el dominio que desea excluir de la entrega.

   >[!NOTE]
   >
   >Asegúrese de introducir una dirección de correo electrónico válida (como abc@company.com) o un dominio (como abc.company.com).

1. Especifique un motivo si es necesario.

   >[!NOTE]
   >
   >En este campo se permiten todos los caracteres imprimibles ASCII comprendidos entre 32 y 126. La lista completa se encuentra en [esta página](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} por ejemplo.

1. Haga clic en **[!UICONTROL Submit]** para confirmar.

### Cargar un archivo CSV {#upload-csv-file}

1. Seleccione el **[!UICONTROL Cargar CSV]** .

1. Descargue la plantilla CSV para usar, que incluye las columnas y el formato siguiente:

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```
   >[!CAUTION]
   >
   >No cambie los nombres de las columnas en la plantilla CSV.
   >
   >El tamaño del archivo no debe superar los 1 MB.

1. Complete la plantilla CSV con las direcciones de correo electrónico o los dominios que desee agregar a la lista de supresión.

   >[!NOTE]
   >
   >Se permiten todos los caracteres ASCII comprendidos entre 32 y 126 en la variable **Comentario** para abrir el Navegador. La lista completa se encuentra en [esta página](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} por ejemplo.

1. Una vez finalizado, arrastre y suelte el archivo CSV y, a continuación, haga clic en **[!UICONTROL Submit]** para confirmar.

>[!NOTE]
>
>Una vez finalizada la carga, asegúrese de que se haya realizado correctamente comprobando su estado desde la interfaz. [Descubra cómo](#recent-uploads)

### Comprobar el estado de las cargas recientes {#recent-uploads}

Haga clic en el **[!UICONTROL Cargas recientes]** para comprobar el estado de los archivos CSV más recientes que ha cargado.

Los estados posibles son:

* **[!UICONTROL Pendiente]**: Se está procesando la carga de archivos.
* **[!UICONTROL Error]**: Error en el proceso de carga del archivo debido a un problema técnico o a un error de formato de archivo.
* **[!UICONTROL Completar]**: El proceso de carga de archivos se completó correctamente.

Durante la carga, si algunas direcciones no tienen el formato correcto, no se añaden a la lista de supresión global.

En ese caso, cuando se completa la carga, se asocia a un informe. Puede descargarlo para comprobar los errores encontrados.

## Eliminar direcciones

Para eliminar una dirección de la lista de supresión global, utilice el **[!UICONTROL Eliminar]** botón.

>[!CAUTION]
>
>Los consultores no pueden eliminar las direcciones o dominios añadidos automáticamente por el proveedor de servicios de terceros Blackbox a través de la interfaz. Esto se puede hacer solo mediante un ticket back-end.

