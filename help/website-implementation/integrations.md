---
title: Implementación de integraciones de Experience Cloud con Launch
description: Descubra cómo validar las integraciones de Audiencias, A4T y Atributos del cliente en su implementación de Adobe Experience Cloud. Esta lección forma parte del tutorial Implementación de Experience Cloud en sitios web con Launch.
seo-description: null
seo-title: Implementación de integraciones de Experience Cloud con Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Integraciones de Experience Cloud

En esta lección, revisará las integraciones clave entre las soluciones que acaba de implementar. La buena noticia es que al completar las lecciones anteriores, ya ha implementado los aspectos de código de las integraciones! No es necesario que realice ningún trabajo adicional en esta lección, además de leer y validar.

## Objetivos de aprendizaje

Al final de esta lección podrá:

1. Explicar los casos de uso básicos de las integraciones de Compartir audiencias, Analytics para Target (A4T) y Atributos del cliente
1. Validar los aspectos básicos de la implementación del lado del cliente de estas integraciones

## Requisitos previos

Debe completar todas las lecciones anteriores de este tutorial antes de seguir las instrucciones de esta lección.

>[!NOTE] Existen diversos requisitos de permisos de usuario, configuraciones de cuenta y pasos de aprovisionamiento necesarios para utilizar completamente estas integraciones y que están fuera del ámbito de este tutorial. Si todavía no utiliza estas integraciones en la implementación actual de Experience Cloud, debe tener en cuenta lo siguiente:
>
> * Examinar todos los requisitos de las [integraciones de Servicios principales](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)
> * Revise los requisitos completos de la [integración de Analytics para Target](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/before-implement.html)
> * Have an Administrator of your Experience Cloud Organization [request provisioning of these integrations](https://www.adobe.com/go/audiences)


## Audiencias

[Audiencias](https://docs.adobe.com/content/help/en/core-services/interface/audiences/audience-library.htm) forma parte del servicio principal Personas y le permite compartir audiencias entre soluciones. Por ejemplo, puede crear una audiencia en Audience Manager y utilizarla para distribuir contenido personalizado con Target.

Los principales requisitos para implementar A4T (que ya ha hecho) son:

1. Implementación del servicio de identidad de Adobe Experience Platform
1. Implementar Audience Manager
1. Implementar otras soluciones que le gustaría recibir o crear audiencias, como Target y Analytics

### Validar la integración de Audiences

La mejor manera de validar la integración de Audiencias es crear una audiencia, compartirla en otra solución y luego usarla completamente en la otra solución (por ejemplo, confirmar que un visitante que califique para un segmento de AAM puede cumplir los requisitos para una actividad de Target dirigida a ese segmento). Sin embargo, eso no entra dentro del ámbito de este tutorial.

Estos pasos de validación se centrarán en la parte crítica visible en la implementación del cliente: el ID de visitante.

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![El entorno de desarrollo de Launch que se muestra en el depurador](images/switchEnvironments-debuggerOnWeRetail.png)

1. Vaya a la ficha Red del depurador

1. Haga clic en **[!UICONTROL Borrar todas las solicitudes]** sólo para limpiar las cosas

1. Vuelva a cargar la página Luma, asegurándose de que ve las solicitudes de Target y Analytics en el depurador

1. Volver a cargar la página Luma

1. Ahora debería ver cuatro solicitudes en la ficha Red del depurador: dos para Target y dos para Analytics

1. Busque en la fila denominada "ID de visitante de Experience Cloud". Los ID de cada solicitud por cada solución siempre deben ser iguales.

   ![Confirmar los SDID coincidentes](images/integrations-matchingECIDs.png)

1. Los ID son únicos de cada visitante y los puede confirmar solicitando a un compañero que repita estos pasos.

## Analytics for Target (A4T)

The [Analytics for Target (A4T)](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/a4t.html) integration allows you to leverage your Analytics data as the source for reporting metrics in Target.

Los principales requisitos para implementar A4T (que ya ha hecho) son:

1. Implementación del servicio de identidad de Adobe Experience Platform
1. Active la solicitud de carga de página de Target antes de la señalización de vista de página de Analytics

A4T funciona uniendo una solicitud de servidor de Target a Analytics con la señalización de vista de página de Analytics, que llamamos "coincidencia".  La vinculación de visitas requiere que la solicitud de Target que envía la actividad (o incrementa una métrica de objetivo basada en Target) tenga un parámetro que coincida con un parámetro en la señalización de vista de página de Analytics. Este parámetro se denomina identificador de datos suplementario (SDID).

### Validación de la implementación de A4T

La mejor manera de validar la integración de A4T es crear una actividad de Target con A4T y validar los datos de informes. Sin embargo, esto está más allá del ámbito de este tutorial. Este tutorial le mostrará cómo confirmar que los identificadores de datos complementarios coinciden entre las llamadas de la solución.

**Validación de los SDID**

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![El entorno de desarrollo de Launch que se muestra en el depurador](images/switchEnvironments-debuggerOnWeRetail.png)

1. Vaya a la ficha Red del depurador

1. Haga clic en **[!UICONTROL Borrar todas las solicitudes]** sólo para limpiar las cosas

1. Vuelva a cargar la página Luma, asegurándose de que ve las solicitudes de Target y Analytics en el depurador

1. Volver a cargar la página Luma

1. Ahora debería ver cuatro solicitudes en la ficha Red del depurador: dos para Target y dos para Analytics

1. Busque en la fila denominada “ID de datos suplementario”. Los ID de la primera carga de página deben coincidir con Target y Analytics. Los ID de la segunda carga de página también deben coincidir, pero deben diferir de la primera carga de página.

   ![Confirmar los SDID coincidentes](images/integrations-matchingSDIDs.png)

Si realiza solicitudes adicionales de Target en el ámbito de una carga de página (sin incluir aplicaciones de una sola página) que formen parte de actividades de A4T, es bueno darles nombres únicos (no target-global-mbox) para que sigan teniendo los mismos SDID de las solicitudes iniciales de Target y Analytics.

## Atributos del cliente

[Atributos](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) del cliente es una parte del servicio principal Personas que le permite cargar datos de la base de datos de administración de la relación con el cliente (CRM) y aprovecharlos en Adobe Analytics y Adobe Target.

Los requisitos principales para implementar los atributos del cliente (que ya ha hecho) son:

1. Implementación del servicio de identidad de Adobe Experience Platform
1. Set Customer Ids via the Id Service *before* Target and Analytics fire their requests (which you accomplished using the rule ordering feature in Launch)

### Validar la implementación de atributos del cliente

Ya ha validado que los ID de cliente se pasan al servicio de identidad y a Target en lecciones anteriores. También puede validar el ID de cliente en la visita de Analytics.
En este momento, el ID de cliente es uno de los pocos parámetros que no se muestran en Experience Cloud Debugger, por lo que utilizará la consola de JavaScript del explorador para verlo.

1. Abrir el sitio Luma
1. Abra las herramientas para desarrolladores del explorador
1. Vaya a la ficha Red
1. En el campo de filtro, escriba `b/ss` que limitará lo que ve a las solicitudes de Adobe Analytics

   ![Abra las Herramientas de desarrollador y filtre la ficha Red para mostrar solo las solicitudes de Analytics](images/aam-openTheJSConsole.png)

1. Haga clic en el vínculo **[!UICONTROL LOGIN]** en la esquina superior derecha del sitio

   ![Haga clic en Iniciar sesión en la navegación superior](images/idservice-loginNav.png)

1. Escriba `test@adobe.com` como nombre de usuario
1. Escriba `test` como contraseña
1. Haga clic en el botón **[!UICONTROL LOGIN]**

   ![Escriba las credenciales y haga clic en iniciar sesión](images/idservice-login.png)

1. Debería volver a la página principal, que también activará una señalización que puede ver en las herramientas para desarrolladores. Si te llevan a la página de información de la cuenta, haz clic en el logotipo WE.RETAIL para volver a la página principal.
1. Haga clic en la solicitud y seleccione la ficha Encabezados
1. Desplácese hacia abajo hasta que vea varios parámetros anidados
   1. cid: es el delimitador estándar para la porción de ID de cliente de la solicitud
   1. crm_id: es el código de integración personalizado que especificó en la lección de servicio de identidad
   1. id: el valor de ID de cliente que proviene del elemento de datos `Email (Hashed)`
   1. as - El estado de autenticación, con el significado "1" de haber iniciado sesión
   ![Validación de ID de cliente de Analytics](images/integrations-analyticsCustomerIDValidation.png)

[Siguiente "Publicar su propiedad" &gt;](publish.md)