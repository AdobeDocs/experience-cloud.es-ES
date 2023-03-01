---
title: Lista de supresión global
description: Descubra la lista de supresión global
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: b66e2525694c771ebb7ac5190b7259ef5658d81a
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 100%

---

# Lista de supresión global {#global-suppression-list}

Una lista de supresión consta de las direcciones de correo electrónico que los clientes desean excluir de las entregas, ya que el envío a estos contactos podría dañar la reputación de envío y las tasas de entrega. Actualmente, Adobe mantiene una lista actualizada de direcciones conocidas de correo electrónico que son incorrectas y que han resultado ser perjudiciales para la participación y la reputación de la campaña de correo, y garantiza que los correos electrónicos no se envíen a dichas direcciones. Esta lista se administra en una lista de supresión global que es común para todos los clientes de Adobe. Las direcciones y los nombres de dominio contenidos en la lista de supresión global están ocultos. En los informes de envío solo se indica el número de destinatarios excluidos.

Ahora es posible administrar la lista de supresión global desde una interfaz que está disponible de forma interna. Esta lista la mantendrán únicamente los consultores de entrega. La lista de supresión global puede incluir direcciones de correo electrónico o de dominio.

## Acceso a la lista de supresión global

Para acceder a la lista detallada de direcciones de correo electrónico y dominios excluidos, vaya a **[!UICONTROL Lista de supresión global]**.

>[!CAUTION]
>
>Los permisos para ver, exportar y administrar la lista de supresión global dependen de la lista de distribución a la que esté asignado. Más información

Se muestran dos pestañas: **[!UICONTROL Correo electrónico]** y **[!UICONTROL Dominio]**.

Hay filtros a su disposición para ayudarle a navegar por la lista.

## Adición de direcciones y dominios

Actualmente, hay dos formas de añadir direcciones a la lista de supresión global:

* Lista depurada por el equipo de entrega.
* Lista proporcionada por el proveedor de servicios de terceros Blackbox.

Puede añadir direcciones de correo electrónico o dominios [de una en una](#add-one-address-or-domain) o [en modo masivo](#upload-csv-file) mediante la carga de un archivo CSV.

Para ello, seleccione el botón **[!UICONTROL Añadir correo electrónico o dominio]** y siga uno de los métodos que se describen a continuación.

### Adición de una dirección o un dominio {#add-one-address-or-domain}

1. Seleccione la opción **[!UICONTROL De uno en uno]**.

1. Elija el tipo de dirección: **[!UICONTROL Dirección de correo electrónico]** o **[!UICONTROL Dirección del dominio]**.

1. Introduzca la dirección de correo electrónico o el dominio que desea excluir del envío.

   >[!NOTE]
   >
   >Asegúrese de introducir una dirección de correo electrónico válida (como abc@compañía.com) o un dominio (como abc.compañía.com).

1. Especifique una razón, si es necesario.

   >[!NOTE]
   >
   >En este campo se permiten todos los caracteres imprimibles ASCII comprendidos entre 32 y 126. La lista completa se encuentra en [esta página](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}, por ejemplo.

1. Haga clic en **[!UICONTROL Enviar]** para confirmar.

### Cargar un archivo CSV {#upload-csv-file}

1. Seleccione la opción **[!UICONTROL Cargar CSV]**.

1. Descargue la plantilla CSV que debe utilizar, que incluye las columnas y el formato que se indican a continuación:

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```

   >[!CAUTION]
   >
   >No cambie los nombres de las columnas en la plantilla CSV.
   >
   >El tamaño del archivo no debe superar 1 MB.

1. Complete la plantilla CSV con las direcciones de correo electrónico y/o los dominios que desea añadir a la lista de supresión.

   >[!NOTE]
   >
   >Se permiten todos los caracteres ASCII comprendidos entre 32 y 126 en la columna **Comentario**. La lista completa se encuentra en [esta página](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}, por ejemplo.

1. Una vez completada, arrastre y suelte el archivo CSV y, a continuación, haga clic en **[!UICONTROL Enviar]** para confirmar.

>[!NOTE]
>
>Una vez finalizada la carga, asegúrese de que se haya realizado correctamente comprobando su estado desde la interfaz. [Descubra cómo](#recent-uploads)

### Comprobar el estado de las cargas recientes {#recent-uploads}

Haga clic en el botón **[!UICONTROL Cargas recientes]** para comprobar el estado de los archivos CSV más recientes que ha cargado.

Los estados posibles son:

* **[!UICONTROL Pendiente]**: se está procesando la carga de archivo.
* **[!UICONTROL Error]**: error en el proceso de carga del archivo debido a un problema técnico o a un error de formato de archivo.
* **[!UICONTROL Completado]**: el proceso de carga de archivos se ha completado correctamente.

Durante la carga, si algunas direcciones no tienen el formato correcto, no se añadirán a la lista de supresión global.

En ese caso, cuando se completa la carga, se asocia a un informe. Puede descargarlo para comprobar los errores encontrados.

## Quitar direcciones

Para quitar una dirección de la lista de supresión global, utilice el botón **[!UICONTROL Eliminar]**.

>[!CAUTION]
>
>Los consultores no pueden eliminar las direcciones o dominios añadidos automáticamente por el proveedor de servicios de terceros Blackbox a través de la interfaz. Esto solo se puede conseguir mediante una incidencia backend.
