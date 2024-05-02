---
title: Solución de problemas de informes dinámicos
description: Aquí encontrará preguntas comunes relacionadas con la creación de informes dinámicos.
audience: end-user
level: Intermediate
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 1%

---

# Resolución de problemas{#troubleshooting}

En esta sección encontrará preguntas comunes relacionadas con la creación de informes dinámicos.

## Para las aperturas únicas y los clics únicos, el recuento de la fila agregada no coincide con los de las filas individuales {#unique-open-clicks-no-match}

Este es un comportamiento esperado.
Podemos tomar el siguiente ejemplo para explicar este comportamiento.

Se envía un correo electrónico a los perfiles P1 y P2.

P1 abre el correo electrónico dos veces el primer día y, a continuación, tres veces el segundo día.

Por su parte, P2 abre el correo electrónico una vez el primer día y no lo vuelve a abrir en los días siguientes.
Esta es una representación visual de la interacción de los perfiles con el correo electrónico enviado:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Día</strong> <br/> </th> 
   <th align="center"> <strong>Aperturas</strong> <br/> </th> 
   <th align="center"> <strong>Aperturas únicas</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> Día 1<br/> </td> 
   <td align="center"> 2 + 1 = 3<br/> </td> 
   <td align="center"> 1 + 1 = 2<br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> Día 2<br/> </td> 
   <td align="center"> 3 + 0 = 3<br/> </td> 
   <td align="center"> 1 + 0 = 1<br/> </td> 
  </tr>
 </tbody> 
</table>

Para comprender el número total de aperturas únicas, es necesario resumir los recuentos de filas de **[!UICONTROL Aperturas únicas]** que nos da el valor 3. Pero como el correo electrónico estaba dirigido solo a 2 perfiles, la tasa de apertura debería mostrar el 150 %.

Para no obtener un porcentaje superior a 100, la definición de **[!UICONTROL Aperturas únicas]** se mantiene para que sea el número de broadlogs únicos que se abrieron. En este caso, incluso si P1 abrió el correo electrónico el día 1 y el día 2, sus aperturas únicas seguirán siendo 1.

Esto dará como resultado la siguiente tabla:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong></strong> <br/> </th> 
   <th align="center"> <strong>Aperturas</strong> <br/> </th> 
   <th align="center"> <strong>Aperturas únicas</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong> Día </strong><br/> </td> 
   <td align="center"> <strong> 6 </strong><br/> </td> 
   <td align="center"> <strong> 2</strong><br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Día 1<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 2<br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Día 2<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Los recuentos únicos se basan en un boceto basado en HTML, lo que puede causar pequeñas imprecisiones en recuentos grandes.

## Los recuentos abiertos no coinciden con el recuento de la base de datos {#open-counts-no-match-database}

Esto puede deberse al hecho de que la heurística se utiliza en el sistema de informes dinámico para rastrear aperturas incluso cuando no podemos rastrear el **[!UICONTROL Abrir]** acción.

Por ejemplo, si un usuario ha desactivado las imágenes en su cliente y hace clic en un enlace del correo electrónico, la variable **[!UICONTROL Abrir]** puede no ser rastreado por la base de datos, pero la variable **[!UICONTROL Clic]** lo haré.

Por lo tanto, el **[!UICONTROL Abrir]** es posible que los recuentos de registros de seguimiento no tengan el mismo recuento en la base de datos.

Estos sucesos se añaden como **&quot;un clic en el correo electrónico implica que se ha abierto un correo electrónico&quot;**.

>[!NOTE]
>
>Dado que los recuentos únicos se basan en un boceto basado en HTML, pueden producirse incoherencias menores entre los recuentos.

## ¿Cómo se calculan los recuentos de envíos recurrentes/transaccionales? {#counts-recurring-deliveries}

Al trabajar con envíos recurrentes y transaccionales, los recuentos se atribuyen tanto a los envíos principales como a los secundarios.
Podemos tomar el ejemplo de un envío recurrente llamado **R1** configurado para ejecutarse todos los días en el día 1 (RC1), el día 2 (RC2) y el día 3 (RC3).
Supongamos que solo una persona ha abierto todas las entregas secundarias varias veces. En este caso, las entregas secundarias recurrentes individuales mostrarán el **[!UICONTROL Abrir]** cuente como 1 para cada uno.
Sin embargo, como la misma persona hizo clic en todas las entregas, la entrega recurrente principal también tiene **[!UICONTROL Única y abierta]** como 1.

Los informes deben tener el aspecto siguiente:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Envío</strong> <br/> </th> 
   <th align="center"> <strong>Enviado</strong> <br/> </th> 
   <th align="center"> <strong>Entregado</strong> <br/> </th>
   <th align="center"> <strong>Aperturas</strong> <br/> </th> 
   <th align="center"> <strong>Aperturas únicas</strong> <br/> </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>R1</strong><br/> </td> 
   <td align="center"> <strong>100</strong><br/> </td> 
   <td align="center"> <strong>90</strong><br/> </td> 
   <td align="center"> <strong>10</strong><br/> </td> 
   <td align="center"> <strong>3</strong><br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> RC1<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 6<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr>
    <tr> 
   <td align="center"> RC2<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 30<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
    <tr> 
   <td align="center"> RC3<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

## ¿Cuál es la significación de los colores en la tabla de mis informes? {#reports-color-signification}

Los colores que se muestran en los informes son aleatorios y no se pueden personalizar. Representan una barra de progreso y se muestran para ayudarle a resaltar mejor el valor máximo alcanzado en los informes.

En el ejemplo siguiente, la celda es del mismo color, ya que su valor es 100%.

![](assets/troubleshooting_1.png)

Si cambia el **[!UICONTROL Formato condicional]** de forma personalizada, cuando el valor alcance el límite superior, la celda se volverá más verde. Mientras que, si alcanza el límite inferior, se pondrá más rojo.

Por ejemplo, aquí se establece la variable **[!UICONTROL Límite superior]** a 500 y **[!UICONTROL Límite inferior]** a 0.

![](assets/troubleshooting_2.png)

## ¿Por qué aparece el valor N/A en mis informes?

![](assets/troubleshooting_3.png)

El valor **N/D** a veces puede aparecer en los informes dinámicos. Esto se puede mostrar por tres motivos:

* La entrega se ha eliminado y se muestra aquí como **N/D** para no causar discrepancias en los resultados.
* Al arrastrar y soltar **[!UICONTROL Entrega transaccional]** dimensión a sus informes, el valor **N/D** podría aparecer como resultado. Esto sucede porque el informe dinámico recupera todos los envíos aunque no sean transaccionales. Esto también puede ocurrir cuando arrastra y suelta el **[!UICONTROL Envío]** dimensión al informe, pero en este caso, la variable **N/D** representará los envíos transaccionales.
* Cuando se utiliza una dimensión con una métrica que no está relacionada con la dimensión. En el ejemplo siguiente, se añade un desglose con la variable **[!UICONTROL URL de seguimiento]** dimensión aunque la variable **[!UICONTROL Clic]** el recuento se establece en 0 en esta entrega.

  ![](assets/troubleshooting_4.png)

## Los informes de las entregas muestran datos incompletos al utilizar la asignación de destino personalizada

Si utiliza asignaciones de Target personalizadas importadas en las entregas y no se muestran datos en los diferentes informes, esto podría significar que no se crearon los enriquecimientos de informes para esas asignaciones de Target.

Para resolver esto:

* Después de importar la asignación de Target desde un XML, también debe importar el enriquecimiento de Creación de informes.

* En lugar de importar la asignación de Target, puede crearla directamente en la interfaz de usuario web de Adobe Campaign, que creará automáticamente el enriquecimiento de creación de informes.

## Discrepancia entre el número de encabezado de columna y la suma de las filas

Se espera una discrepancia entre el número de encabezado de columna y la suma de todas las filas en los siguientes casos:

* **Métricas únicas**: El uso de métricas únicas puede alterar el recuento total mostrado en el encabezado, ya que se basa en los ID de destinatario en lugar de una simple suma de recuentos de filas. Por consiguiente, un solo perfil puede almacenar en déclencheur numerosos eventos en diversas dimensiones, lo que da lugar a varias filas en el conjunto de datos. Sin embargo, en el encabezado, cada perfil se cuenta solo una vez.

  Por ejemplo:

   * Si un perfil A abre un correo electrónico en tres días diferentes, el desglose por día mostrará A en tres filas, pero en el encabezado, A se contará como 1.

   * Si el perfil A hace clic en tres vínculos diferentes en un mensaje de correo electrónico el mismo día, el desglose por URL de seguimiento mostrará A en tres filas, pero en el encabezado, A contará como 1. Lo mismo se aplica a los desgloses por dispositivo y explorador.

* **Abrir métricas**: el recuento de aperturas se determina sumando el total de eventos abiertos reales y eventos de clics únicos (por ID de destinatario), excluyendo los casos en los que no se ha producido un evento de apertura, ya que no se puede hacer clic en un vínculo de correo electrónico sin un evento de apertura.

  Por ejemplo:

   * Cuando el perfil A abre un correo electrónico rastreado (con la URL U1), se registra como un evento abierto con la URL anotada como nula. Al hacer clic en U1 más adelante, se genera un evento de clic. Aunque el clic de A en U1 también se cuenta como un evento abierto, no hay ningún evento abierto específico para U1. Por lo tanto, A solo se cuenta una vez en la cantidad abierta única.

   * Un perfil R abre un correo electrónico el día 1, registra un evento abierto y hace clic en un vínculo. En los dos días siguientes, R vuelve a abrir el correo electrónico y hace clic en el vínculo de nuevo, lo que genera un evento de clic cada día. Mientras que el compromiso de R se rastrea diariamente en el número Abierto, R solo se cuenta una vez en el encabezado de la columna, centrándose en compromisos únicos.

* **Evento anulado**: en los informes, el evento anulado significa intentos de envío que inicialmente se marcaron como correctos, pero que finalmente fallaron después de los reintentos. Se indican mediante un recuento de -1. Para evitar confusiones, estos recuentos negativos se excluyen de los números de métricas de entrega que se muestran. Como resultado, es posible que el total de todas las filas de la métrica de envío no coincidan con el número de encabezado de columna.
