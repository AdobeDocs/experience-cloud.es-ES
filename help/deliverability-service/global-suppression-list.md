---
title: Lista de supresión global
description: Descubra la lista de supresión global
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: b66e2525694c771ebb7ac5190b7259ef5658d81a
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 2%

---

# Lista de supresión global {#global-suppression-list}

Una lista de supresión consiste en las direcciones de correo electrónico que los clientes desean excluir de sus envíos, ya que el envío a estos contactos podría dañar su reputación y las tasas de envío. Actualmente, Adobe mantiene una lista actualizada de direcciones de correo electrónico incorrectas conocidas que han demostrado ser perjudiciales para la participación y la reputación de correo electrónico, y garantiza que los correos electrónicos no se entreguen a ellas. Esta lista se administra en una lista de supresión global que es común a todos los clientes de Adobe. Las direcciones y los nombres de dominio contenidos en la lista de supresión global están ocultos. En los informes de envío solo se indica el número de destinatarios excluidos.

Ahora es posible administrar la lista de supresión global desde una interfaz disponible internamente. Esta lista solo la mantendrán los consultores de capacidad de envío. La lista de supresión global puede incluir direcciones de correo electrónico o de dominio.

## Acceso a la lista de supresión global

Para acceder a la lista detallada de direcciones de correo electrónico y dominios excluidos, vaya a **[!UICONTROL Lista de supresión global]**.

>[!CAUTION]
>
>Los permisos para ver, exportar y administrar la lista de supresión global dependen de la lista de distribución a la que esté asignado. Más información

Se muestran dos pestañas: **[!UICONTROL Correo electrónico]** y **[!UICONTROL Dominio]**.

Los filtros están disponibles para ayudarle a examinar la lista.

## Añadir direcciones y dominios

Actualmente, hay dos formas en que las direcciones se añaden a la lista de supresión global:

* Lista seleccionada por el equipo de entrega.
* Lista proporcionada por el proveedor de servicios de terceros Blackbox.

Puede añadir direcciones de correo electrónico o dominios [uno a la vez](#add-one-address-or-domain), o [en modo por lotes](#upload-csv-file) mediante la carga de un archivo CSV.

Para ello, seleccione la **[!UICONTROL Añadir correo electrónico o dominio]** y siga uno de los métodos siguientes.

### Añadir una dirección o dominio {#add-one-address-or-domain}

1. Seleccione el **[!UICONTROL Uno por uno]** opción.

1. Elija el tipo de dirección: **[!UICONTROL Correo electrónico]** o **[!UICONTROL Dirección de dominio]**.

1. Introduzca la dirección de correo electrónico o el dominio que desea excluir del envío.

   >[!NOTE]
   >
   >Asegúrese de introducir una dirección de correo electrónico válida (como abc@company.com) o un dominio (como abc.company.com).

1. Especifique un motivo si es necesario.

   >[!NOTE]
   >
   >Todos los caracteres imprimibles ASCII comprendidos entre 32 y 126 están permitidos en este campo. La lista completa de filtros se encuentra en [esta página](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} por ejemplo.

1. Clic **[!UICONTROL Enviar]** para confirmar.

### Cargar un archivo CSV {#upload-csv-file}

1. Seleccione el **[!UICONTROL Cargar CSV]** opción.

1. Descargue la plantilla CSV para utilizar, que incluye las columnas y el formato siguientes:

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```

   >[!CAUTION]
   >
   >No cambie los nombres de las columnas en la plantilla CSV.
   >
   >El tamaño del archivo no debe exceder 1 MB.

1. Rellene la plantilla CSV con las direcciones de correo electrónico o los dominios que desee añadir a la lista de supresión.

   >[!NOTE]
   >
   >Todos los caracteres ASCII comprendidos entre 32 y 126 están permitidos en **Comentario** columna. La lista completa de filtros se encuentra en [esta página](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} por ejemplo.

1. Una vez finalizado, arrastre y suelte el archivo CSV y haga clic en **[!UICONTROL Enviar]** para confirmar.

>[!NOTE]
>
>Una vez completada la carga, compruebe su estado en la interfaz para asegurarse de que se ha realizado correctamente. [Descubra cómo](#recent-uploads)

### Comprobar estado de cargas recientes {#recent-uploads}

Haga clic en **[!UICONTROL Cargas recientes]** para comprobar el estado de los archivos CSV más recientes cargados.

Los estados posibles son:

* **[!UICONTROL Pendiente]**: se está procesando la carga del archivo.
* **[!UICONTROL Error]**: Error en el proceso de carga del archivo debido a un problema técnico o a un error de formato de archivo.
* **[!UICONTROL Completar]**: el proceso de carga del archivo se ha completado correctamente.

Durante la carga, si algunas direcciones no tienen el formato correcto, no se añaden a la lista de supresión global.

En ese caso, cuando la carga se haya completado, se asocia a un informe. Puede descargarlo para comprobar los errores encontrados.

## Eliminación de direcciones

Para quitar una dirección de la lista de supresión global, utilice el **[!UICONTROL Eliminar]** botón.

>[!CAUTION]
>
>Los consultores no pueden eliminar las direcciones o dominios agregados automáticamente por el proveedor de servicios de terceros Blackbox a través de la interfaz. Esto solo se puede hacer mediante un ticket de backend.
