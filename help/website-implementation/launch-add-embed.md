---
title: Implementar el código incrustado de lanzamiento
description: Obtenga información sobre cómo obtener los códigos incrustados de la propiedad Launch e implementarlos en el sitio web. Esta lección forma parte del tutorial Implementación de Experience Cloud en sitios web con Launch.
seo-description: null
seo-title: Implementar el código incrustado de lanzamiento
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 14e46fa7d806f2713a69fe5d3a0a8c326de26d23

---


# Añadir el código de incrustación de Launch

En esta lección, implementará el código incrustado asincrónico del entorno de desarrollo de su propiedad Launch. A lo largo del camino, aprenderá sobre dos conceptos principales de Launch: Entornos y Códigos incrustados.

## Objetivos de aprendizaje

Al final de esta lección podrá:

* Obtenga el código incrustado de la propiedad Launch
* Comprender la diferencia entre los entornos Development, Staging y Production
* Agregar un código incrustado de lanzamiento a un documento HTML
* Explain the optimal location of the Launch embed code in relation to other code in the `<head>` of an html document

## Copiar el código incrustado

The embed code is a `<script>` tag that you put on your webpages to load and execute the logic you build in Launch. Si carga la biblioteca de forma asíncrona, el navegador continúa cargando la página, recupera la biblioteca de Launch y la ejecuta en paralelo. En este caso, solo hay un código incrustado, que usted pone en `<head>`. (When Launch is deployed synchronously, there are two embed codes, one which you put in the `<head>` and another which you put before the `</body>`).

En la propiedad Overview Screen, haga clic en la pestaña `Environments` para ir a la página de entornos. Tenga en cuenta que los entornos de desarrollo, ensayo y producción se han creado previamente para usted.

![Haga clic en Entornos en la barra de navegación superior](images/launch-environments.png)

Los entornos Development, Staging y Production se corresponden con los entornos habituales en el proceso de programación y desarrollo de códigos. El código lo escribe primero un desarrollador en un entorno de desarrollo. Cuando han completado su trabajo, lo envían a un entorno de ensayo (Staging) para que el control de calidad y otros equipos lo revisen. Una vez satisfechos el control de calidad y otros equipos, el código se publica en el entorno de producción, que es el entorno público que experimentan los visitantes cuando acceden al sitio web.

Launch permite entornos de desarrollo adicionales, lo que resulta útil en organizaciones grandes en las que varios desarrolladores trabajan en diferentes proyectos al mismo tiempo.

Estos son los únicos entornos que necesitamos para completar el tutorial. Los entornos le permiten tener diferentes versiones de trabajo de sus bibliotecas de Launch alojadas en diferentes direcciones URL, para que pueda agregar nuevas funciones de forma segura y ponerlas a disposición de los usuarios adecuados (por ejemplo, desarrolladores, ingenieros de control de calidad, público, etc.) en el momento adecuado.

Ahora vamos a copiar el código incrustado:

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal.

1. Tenga en cuenta que Launch pasará de forma predeterminada a los códigos incrustados asincrónicos

1. Haga clic en el icono Copiar ![Copiar icono](images/launch-copyIcon.png) Copiar para copiar el código incrustado en el portapapeles.

1. Click **[!UICONTROL Close]** to close the modal.

   ![Icono de instalación](images/launch-copyInstallCode.png)

## Implement the Embed Code in the `<head>` of the Sample HTML Page

The embed code should be implemented in the `<head>` element of all HTML pages that will share the property. You might have one or several template files which control the `<head>` globally across the site, making it a straightforward process to add Launch.

Si aún no lo ha hecho, descargue [la página](https://www.enablementadobe.com/multi/web/basic-sample.html) HTML de muestra (haga clic con el botón secundario en este vínculo y haga clic en "Guardar vínculo como") y ábralo en un editor de código. [Corchetes](http://brackets.io/) es un editor de código abierto gratuito si lo necesita.

Reemplace el código incrustado existente en la línea 34 o alrededor de ella por el que hay en el portapapeles y guarde la página. Ahora abra la página en un navegador web. If you are loading the page using the `file://` protocol, you will need to add "https:" at the beginning of the embed code URL in your code editor). Las líneas 33-36 de la página de muestra pueden tener un aspecto similar al siguiente:

```html
    <!--Launch Header Embed Code: REPLACE LINE 39 WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="https://assets.adobedtm.com/launch-ENa21cfed3f06f4ddf9690de8077b39e81-development.min.js" async></script>
    <!--/Launch Header Embed Code-->
```

Abra las herramientas de desarrollador del explorador Web y vaya a la ficha Red. At this point you should see a 404 error for the Launch environment URL:
![404 error](images/samplepage-404.png)

Se espera el error 404 porque aún no ha creado una biblioteca en este entorno de Launch. Lo hará en la siguiente lección. Si ve un mensaje "failed" en lugar de un error 404, probablemente olvidó agregar el protocolo `https://` en el código incrustado. De nuevo, solo debe especificar el protocolo `https://` si está cargando la página de muestra mediante el protocolo `file://`. Realice un cambio y vuelva a cargar la página hasta que aparezca el error 404.

## Iniciar prácticas recomendadas de implementación

Analicemos algunas de las optimizaciones de implementación de Launch que se muestran en la página de muestra:

* **Capa de datos**:

   * We *strongly* recommend creating a digital data layer on your site containing all of the attributes needed to populate variables in Analytics, Target, and other marketing solutions. Esta página de muestra solo contiene una capa de datos muy sencilla, pero una capa de datos real puede contener muchos más detalles sobre la página, el visitante, los detalles del carro de compras, etc. For more info on data layers, please see [Customer Experience Digital Data Layer 1.0](https://www.w3.org/2013/12/ceddl-201312.pdf)

   * Defina la capa de datos antes del código incrustado de Launch para maximizar lo que puede hacer en Target, Atributos del cliente y Analytics.

* **Bibliotecas** auxiliares de JavaScript: Si ya tiene una biblioteca como JQuery implementada en las páginas, cárguela antes `<head>` de iniciar para aprovechar su sintaxis en Launch y Target

* **Tipo de documento** HTML5: Target requiere el tipo de documento HTML5

* **preconnect y dns-prefetch**: Utilice preconnect y dns-prefetch para mejorar el tiempo de carga de la página. Consulte también: [/](https://w3c.github.io/resource-hints/)https://w3c.github.io/resource-hints/

* **ocultación previa de fragmento para implementaciones** asíncronas de Target: Aprenderá más sobre esto en la lección de Target, pero cuando Target se implemente mediante códigos incrustados de Launch asincrónicos, debe codificar un fragmento de ocultación previa en las páginas antes de los códigos incrustados de Launch para administrar el parpadeo del contenido

Este es un resumen de cómo se ven estas prácticas recomendadas en el orden sugerido. Tenga en cuenta que hay algunos marcadores de posición para detalles específicos de la cuenta:

```html
<!doctype html>
<html lang="en">
<head>
    <title>Basic Demo</title>
    <!--Preconnect and DNS-Prefetch to improve page load time. REPLACE "techmarketingdemos" WITH YOUR OWN AAM PARTNER ID, TARGET CLIENT CODE, AND ANALYTICS TRACKING SERVER-->
    <link rel="preconnect" href="//dpm.demdex.net">
    <link rel="preconnect" href="//fast.techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//cm.everesttech.net">
    <link rel="preconnect" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="preconnect" href="//techmarketingdemos.sc.omtrdc.net">
    <link rel="dns-prefetch" href="//dpm.demdex.net">
    <link rel="dns-prefetch" href="//fast.techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//cm.everesttech.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.sc.omtrdc.net">
    <!--/Preconnect and DNS-Prefetch-->
    <!--Data Layer to enable rich data collection and targeting-->
    <script>
    var digitalData = {
        "page": {
            "pageInfo" : {
                "pageName": "Home"
                }
            }
    };
    </script>
    <!--/Data Layer-->
    <!--jQuery or other helper libraries-->
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <!--/jQuery-->
    <!--prehiding snippet for Adobe Target with asynchronous Launch deployment-->
    <script>
        (function(g,b,d,f){(function(a,c,d){if(a){var e=b.createElement("style");e.id=c;e.innerHTML=d;a.appendChild(e)}})(b.getElementsByTagName("head")[0],"at-body-style",d);setTimeout(function(){var a=b.getElementsByTagName("head")[0];if(a){var c=b.getElementById("at-body-style");c&&a.removeChild(c)}},f)})(window,document,"body {opacity: 0 !important}",3E3);
    </script>
    <!--/prehiding snippet for Adobe Target with asynchronous Launch deployment-->
    <!--Launch Header Embed Code: REPLACE LINE 39 WITH THE INSTALL CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
    <!--/Launch Header Embed Code-->
</head>
<body>
    <h1>Launch by Adobe: Basic Demo</h1>
    <p>This is a very simple page to demonstrate basic concepts of Launch by Adobe</p>
</body>
</html>
```

Ahora ya sabe cómo agregar el código incrustado de Launch a su sitio.

[Siguiente "Agregar un elemento de datos, una regla y una biblioteca" &gt;](launch-data-elements-rules.md)