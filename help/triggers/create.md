---
title: Crear y administrar Experience Cloud Triggers
description: Descubra la IU de Adobe Experience Cloud Triggers
hide: true
hidefromtoc: true
source-git-commit: ce0faf9fab45c931feb666ac0c77f5ab5c231746
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 25%

---

# Crear un Trigger de Experience Cloud {#create-triggers}

>[!NOTE]
>
> La nueva interfaz de usuario para Déclencheur Experience Cloud ofrece una experiencia intuitiva para administrar los comportamientos de los consumidores y personalizar las experiencias de los usuarios. Para volver a la interfaz anterior, haga clic en el botón **[!UICONTROL Vaya al modo clásico]** botón.

Cree un activador y configure sus condiciones. Por ejemplo, puede especificar los criterios de las reglas de un Trigger durante una visita, por ejemplo, métricas como Abandonos del carro de compras, o dimensiones como el nombre del producto. Cuando se cumplen las reglas, se ejecuta el Trigger.

1. En el Experience Cloud, seleccione el menú avanzado y, a continuación, los Déclencheur.

   ![](assets/triggers_7.png)

1. En la página de inicio de su Déclencheur, haga clic en **[!UICONTROL Crear Déclencheur]** y, a continuación, especifique el tipo de déclencheur.

   Hay tres tipos de déclencheur disponibles:

   * **[!UICONTROL Abandono]**: Puede crear un déclencheur que se active cuando un visitante vea un producto, pero no agregue nada al carro de compras.

   * **[!UICONTROL Acción]**: Puede crear déclencheur, por ejemplo, para que se activen después de que se registren en el boletín informativo, de suscripciones por correo electrónico o cuando se soliciten tarjetas de crédito (confirmaciones). Si tiene un comercio minorista, puede crear un Trigger para visitantes que se suscriben a un programa de fidelidad. Si se dedica al sector de los medios de comunicación y el entretenimiento, cree Triggers para visitantes que vean un determinado programa y que podrían estar interesados en responder a una encuesta.

   * **[!UICONTROL Inicio de sesión y Fin de sesión]**: Cree un déclencheur para los eventos de inicio y fin de sesión.

   ![](assets/triggers_1.png)

1. Agregue un **[!UICONTROL Nombre]** y **[!UICONTROL Descripción]** a su déclencheur.

1. Seleccione Analytics **[!UICONTROL Grupo de informes]** para este déclencheur. Esta configuración identifica los datos de sistema de informes que se van a utilizar.

   [Más información sobre el grupo de informes](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite.html).

1. Elija la **[!UICONTROL Déclencheur después de que no haya acción para]** periodo de validez.

1. En el **[!UICONTROL La visita debe incluir]** y **[!UICONTROL La visita no debe incluir]** , puede definir criterios o comportamientos del visitante que desee o no quiera que se produzcan. Puede especificar **Y** o **O** en o entre condiciones, según los criterios que determine.

   Por ejemplo, las reglas de un Trigger sencillo de abandono del carro de compras podrían ser:

   * **[!UICONTROL La visita debe incluir]**: `Carts (metric) Is greater or equal to 1` para dirigirse a visitantes que tengan al menos un artículo en el carro de compras.
   * **[!UICONTROL La visita no debe incluir]**: `Checkout (metric) Exists.` para eliminar a los visitantes que compraron los artículos en sus carros de compras.

   ![](assets/triggers_2.png)

1. Haga clic en **[!UICONTROL Contenedor]** para crear y guardar reglas, condiciones o filtros que definan un déclencheur. Para que los eventos se produzcan al mismo tiempo, debe colocarlos en el mismo contenedor.

   Cada contenedor procesa de forma independiente en el nivel de visita, lo que significa que si dos contenedores se unen con la variable **[!UICONTROL Y]** , las reglas solo se cumplirán cuando dos visitas cumplan los requisitos.

1. En el **[!UICONTROL Metadatos]** , haga clic en **[!UICONTROL + Dimension]** para elegir una dimensión de Campaign determinada o variables que sean relevantes para el comportamiento de un visitante.

   ![](assets/triggers_3.png)

1. Haga clic en **[!UICONTROL Guardar]**.

1. Seleccione el **[!UICONTROL Déclencheur]** de la lista para acceder al informe detallado de su déclencheur.

   ![](assets/triggers_4.png)

1. Desde la vista detallada de su déclencheur, puede acceder a los informes sobre la cantidad de Déclencheur disparados. Si es necesario, puede editar el déclencheur con el icono de lápiz.

   ![](assets/triggers_5.png)
