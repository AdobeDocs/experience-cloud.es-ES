---
title: Creación de una dimensión de perfil
description: Obtenga información sobre cómo crear una dimensión de perfil basada en datos de perfil.
audience: reporting
content-type: reference
level: Intermediate
exl-id: a12dc772-13c7-45ff-9fbf-3dfdd3801eae
source-git-commit: 5da9b29c424f019f3dafc127a41e974017af494c
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 3%

---

# Creación de una dimensión de perfil{#creating-a-custom-profile-dimension}

Los informes también se pueden crear y administrar en función de los datos de perfil creados durante la extensión del esquema de destinatario.

* [Paso 1: Ampliación del esquema de destinatario](##extend-schema)
* [Paso 2: Vincular el nuevo campo personalizado](#link-custom)
* [Paso 3: Creación de un informe dinámico para filtrar los destinatarios con la dimensión de perfil](#create-report)

## Paso 1: Ampliación del esquema de destinatario {#extend-schema}

Para añadir un nuevo campo de perfil, debe ampliar el esquema, siga los pasos a continuación:

1. Vaya a la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** en el explorador.

   ![](assets/custom_field_1.png)

1. Identifique el esquema de destinatario personalizado y selecciónelo. Si todavía no ha ampliado el esquema integrado nms:recipient, consulte [este procedimiento](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Añada el campo personalizado al editor de esquemas.

   Por ejemplo, para agregar un campo personalizado de Fidelidad en el esquema de destinatarios:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Haga clic en **[!UICONTROL Guardar]**.

1. A continuación, identifique el esquema broadLogRcp personalizado y selecciónelo. Si todavía no ha ampliado el esquema integrado de registro de envío, consulte [este procedimiento](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Añada el mismo campo personalizado que el esquema Recipient al editor de esquemas.

   ![](assets/custom_field_3.png)

1. Haga clic en **[!UICONTROL Guardar]**.

1. Para aplicar las modificaciones realizadas en los esquemas, inicie el Asistente para la actualización de bases de datos mediante **[!UICONTROL Herramientas]** > **[!UICONTROL Avanzadas]** > **[!UICONTROL Actualizar la estructura de la base de datos]** y ejecute Actualizar la estructura de la base de datos. [Más información](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

El nuevo campo de perfil ya está listo para que lo utilicen y seleccionen los destinatarios.

## Paso 2: Vincular el nuevo campo personalizado {#link-custom}

>[!NOTE]
>
> Solo puede agregar hasta 20 campos personalizados al informe dinámico.

Ahora que se ha creado el campo de perfil, es necesario vincularlo a la dimensión de creación de informes dinámica correspondiente.

Antes de ampliar el registro con nuestro campo de perfil, asegúrese de que se aceptó la ventana PII para poder enviar datos PII al informe dinámico. Para obtener más información, consulte esta [página](pii-agreement.md).

1. Vaya a la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** > **[!UICONTROL Additional reporting field]** en el explorador.

   ![](assets/custom_field_5.png)

1. Haga clic en **[!UICONTROL Nuevo]** para crear su dimensión de informes dinámicos correspondiente.

1. Seleccione **[!UICONTROL Editar expresión]** y examine el esquema Destinatario para encontrar el campo de perfil creado anteriormente.

   ![](assets/custom_field_6.png)

1. Haga clic en **[!UICONTROL Finalizar]**.

1. Escriba su dimensión **[!UICONTROL Label]**, visible en el sistema de informes dinámico, y haga clic en **[!UICONTROL Guardar]**.

   ![](assets/custom_field_7.png)

El campo de perfil ahora está disponible como dimensión de perfil en los informes. Para eliminar la dimensión de perfil, puede seleccionarla y hacer clic en el icono **[!UICONTROL Eliminar]**.

Ahora que el esquema de destinatario se ha ampliado con este campo de perfil y se ha creado la dimensión personalizada, puede empezar a segmentar destinatarios en las entregas.

## Paso 3: Creación de un informe dinámico para filtrar los destinatarios con la dimensión de perfil {#create-report}

Después de realizar la entrega, puede desglosar los informes usando la dimensión de perfil.

1. En la ficha **[!UICONTROL Informes]**, seleccione un informe predeterminado o haga clic en el botón **[!UICONTROL Crear]** para comenzar uno desde cero.

   ![](assets/custom_field_8.png)

1. En la categoría **[!UICONTROL Dimension]**, haga clic en **[!UICONTROL Perfil]** y, a continuación, arrastre y suelte la dimensión de perfil en la tabla de forma libre.

   ![](assets/custom_field_9.png)

1. Arrastre y suelte cualquier métrica para empezar a filtrar los datos.

1. Arrastre y suelte una visualización en el espacio de trabajo si es necesario.

