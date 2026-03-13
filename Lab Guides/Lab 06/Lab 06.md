# Laboratorio 6: Actualización del agente de contratación a un sistema autónomo

En este laboratorio, profundizará en los disparadores de eventos
(**event triggers**), elevando su sistema de agentes de una
**operación** reactiva a una **autónoma**. Transformará sus agentes para
que dejen de esperar la entrada humana y comiencen a responder
proactivamente a eventos externos, tomando acciones inteligentes sin
supervisión.

Think of it as upgrading from agents that answer questions to agents
that anticipate needs and act independently. Through event triggers and
automated workflows, your **Hiring Agent** will **detect** incoming
resume **emails**, **process** attachments **automatically**, **store**
data in **Dataverse**, and **notify** your **HR recruitment team** via
**Microsoft Teams** - all while you focus on higher-value tasks. Piense
en ello como una actualización: de agentes que responden preguntas a
agentes que anticipan necesidades y actúan de forma independiente. A
través de disparadores de eventos y flujos de trabajo automatizados, su
**Hiring Agent detectará** **correos electrónicos** de currículums
entrantes, **procesará** archivos adjuntos **automáticamente**,
**almacenará** datos en **Dataverse** y **notificará** a su **equipo de
reclutamiento de RR. HH.** a través de Microsoft Teams, todo mientras
usted se enfoca en tareas de mayor valor.

**Objetivos**

En este laboratorio, aprenderá:

1.  Cómo los desencadenadores de eventos habilitan el comportamiento
    autónomo del agente sin interacción del usuario.

2.  Las diferencias entre agentes interactivos y autónomos en Copilot
    Studio.

3.  Cómo crear disparadores de eventos que procesen automáticamente
    archivos adjuntos de correo electrónico y carguen archivos en
    Dataverse.

4.  Cómo construir flujos de agente que publiquen tarjetas adaptativas
    en canales de Teams para notificaciones.

5.  Cómo transferir datos entre disparadores de eventos y flujos de
    agente para una automatización de extremo a extremo.

**¿Qué es un desencadenador de evento (Event trigger)?**

Los **desencadenadores de eventos** permiten que un agente actúe por sí
solo cuando sucede algo en otro sistema, sin necesidad de un mensaje del
usuario. Cuando el evento configurado se activa (como "nuevo elemento de
SharePoint", "nuevo correo electrónico", "tarea de Planner asignada" o
incluso una recurrencia basada en el tiempo), un conector envía una
carga útil de activación (trigger payload) a su agente. El agente sigue
entonces sus instrucciones para decidir qué acciones o temas llamar.

**Agente interactivo vs agente autónomo - comparación-**

Ahora que conoce la diferencia entre desencadenadores de eventos y
desencadenadores de temas, a continuación aprenda la diferencia entre un
agente interactivo y un agente autónomo.

En términos de Copilot Studio, "interactive" corresponde a agentes que
interactúan principalmente mediante **temas** en un chat o canal.
"Autonomous" corresponde a agentes que también aprovechan
**desencadenadores de eventos** para ejecutarse sin intervención del
usuario.

## Ejercicio 1: Automatizar correos electrónicos de solicitud de candidatos

A continuación, agregará un desencadenador de evento al **Hiring Agent**
y creará un flujo de agente en el **agente** secundario **Application
Intake** para gestionar el procesamiento adicional para la autonomía.

**Escenario de caso de uso**

**Como** reclutador de RR. HH.

**Quiero** ser notificado cuando llegue a mi bandeja de entrada un
correo electrónico con un currículum y que se cargue automáticamente en
Dataverse.

**Para poder** informado sobre los currículums enviados por correo
electrónico para solicitudes que se cargan automáticamente en Dataverse.

Logrará esto utilizando dos técnicas:

1.  Un desencadenador de evento cuando llegue el correo electrónico:

    - Verificar que el contentType del archivo sea igual a PDF como tipo
      de formato.

    - Extraer el archivo y cargarlo en Dataverse utilizando acciones a
      través del conector de Dataverse.

    - Luego enviar un prompt al agente para procesamiento adicional
      pasando parámetros de entrada desde las acciones de Dataverse.

2.  Se agregará un flujo de agente al **agente** secundario
    **Application** **Intake**, el cual será invocado por el prompt en
    el desencadenador de evento.

    - Utilice los parámetros de entrada pasados desde el prompt del
      desencadenador de evento en una tarjeta adaptable publicada en un
      canal de Microsoft Teams para notificar al equipo de Reclutamiento
      de RR. HH. La tarjeta adaptable tendrá un enlace a la fila de
      Dataverse que puede visualizarse en el **Hiring Agent**.

### Tarea 1: Automatizar la carga de currículums a Dataverse recibidos por correo electrónico

1.  En el Hiring Agent, desplácese hacia abajo en la **pestaña**
    **Overview** hasta la sección **Triggers** y seleccione **+ Add
    trigger**.

> ![](./media/image1.png)

2.  Se mostrará una lista de desencadenadores. Seleccione **When a new
    email arrives (V3)** y seleccione **Next**.

> ![](./media/image2.png)

3.  Seleccione **Continue** en la siguiente pantalla.

![](./media/image3.png)

4.  Ahora verá el **nombre del desencadenador** y las referencias de
    conexión **Sign** **in** para las aplicaciones listadas. Cambie el
    nombre del desencadenador al siguiente:

+++When a new email arrives from an applicant+++

> **NOTA:** Asegúrese de ver una marca de verificación verde junto a
> cada una de las referencias de conexión de las aplicaciones listadas.
> Si no ve una marca de verificación verde, inicie sesión a través del
> menú de puntos suspensivos (...) y seleccione **+ New connection
> reference** para crear una nueva referencia de conexión.
>
> ![](./media/image4.png)

5.  El paso final es establecer las propiedades de entrada del
    desencadenador. Actualice las siguientes propiedades de la siguiente
    manera,

[TABLE]

6.  Seleccione **Create trigger**.

> ![](./media/image5.png)

7.  Una vez creado, aparecerá un mensaje de confirmación indicando que
    el desencadenador se ha agregado al agente. Seleccione **Close** y
    el **desencadenador** aparecerá en la sección Triggers.

> ![](./media/image6.png)

8.  Ahora actualizará el desencadenador de evento para agregar más
    capacidades de automatización. Seleccione el menú de **puntos
    suspensivos (...)** junto al desencadenador y seleccione **Edit in
    Power Automate**.

> ![](./media/image7.png)

9.  El desencadenador se cargará como un flujo en el portal de creación
    de Power Automate. Se abrirá en el diseñador de flujos, donde puede
    agregar lógica y acciones adicionales para mayor automatización. El
    desencadenador aparecerá en la parte superior, seguido de **Sends a
    prompt to the specified copilot for processing** como la última
    acción en el flujo.

> ![](./media/image8.png)

10. De forma predeterminada, el desencadenador **When a new email
    arrives** en Power Automate puede procesar varios correos
    electrónicos juntos si llegan varios al mismo tiempo, ejecutando el
    flujo solo una vez para el lote.

> Para asegurarse de que el flujo se ejecute por separado para cada
> correo electrónico, seleccione el nodo When a new email arrives y
> luego seleccione **Settings**.
>
> Habilite la opción **Split On** en la **configuración** **del
> desencadenador** y
> seleccione **@triggerOutputs()?\['body/value'\]** en el campo de
> **matriz del menú desplegable**.
>
> Con **Split On** activado y el campo de matriz configurado en
> @triggerOutputs()?\['body/value'\], el flujo se ejecutará de forma
> individual para cada mensaje, incluso si llegan varios
> simultáneamente.
>
> ![](./media/image9.png)

11. A continuación, agregue lógica para verificar el tipo de archivo del
    adjunto; solo desea cargar archivos adjuntos .PDF y no imágenes
    (estas pueden provenir de firmas de correo electrónico). Seleccione
    el icono + debajo del desencadenador y seleccione **Control** en la
    sección **Built in tools**.

> ![](./media/image10.png)

12. Seleccione la acción **Condition**.

> ![](./media/image11.png)

13. Ahora configure la condición para verificar si el tipo de archivo
    del adjunto es .PDF. En el campo **Choose a value** a la izquierda,
    seleccione el **icono de rayo**.

> ![](./media/image12.png)

14. En el campo **Search**, escriba **+++content type+++** y seleccione
    el parámetro **Attachments Content-Type** del desencadenador.

> ![](./media/image13.png)

15. Hagamos una pausa aquí por un momento; probablemente habrá notado
    que la acción **For each** apareció automáticamente.

> ![](./media/image14.png)
>
> Esta acción representa el recorrido a través de cada archivo adjunto
> en el correo electrónico, ya que el parámetro **Attachments
> Content-Type** está vinculado a cada archivo adjunto.
>
> Internamente, se trata de una matriz (array) y es por eso que la
> acción **For each** (Para cada uno) se agregó automáticamente al
> seleccionar el parámetro **Attachments Content-Type** en la acción
> **Condition**.

16. A continuación, en el otro campo **Choose a value** a la derecha en
    el bloque de **Condition**, escriba +++application/pdf+++

Esto garantizará que, por cada archivo adjunto, se verifique que el
formato de la extensión del archivo sea .PDF.

> ![](./media/image15.png)

17. Ahora configuraremos la ruta **True** para extraer el archivo del
    correo electrónico y cargarlo en la tabla de **Resume** de
    Dataverse.

> Añada una nueva acción debajo en la ruta **True** y busque html to
> text. Busque y seleccione la acción +++**Html to text**+++ .
>
> **Nota:** La acción **HTML to text** en Power Automate se utiliza para
> convertir contenido con formato HTML en texto sin formato. Esto es
> especialmente útil cuando recibe datos (como correos electrónicos,
> contenido web o respuestas de API) que contienen etiquetas HTML y
> desea extraer solo el texto legible sin ningún formato o código.
>
> ![](./media/image16.png)

18. A continuación, debemos crear una nueva referencia de conexión para
    la acción **Html to text** seleccionando **Create new**.

> ![](./media/image17.png)

19. La acción ya se puede configurar. Vamos a añadir el parámetro
    **Body** del desencadenador. En el campo **Content**, seleccione el
    icono del rayo o el icono **fx** a la derecha.

> ![](./media/image18.png)

20. En la pestaña **Dynamic content**, busque **+++body+++** y
    seleccione el parámetro **Body**, seguido de la selección de
    **Add**.

> ![](./media/image19.png)

21. Hemos terminado de configurar esta acción, así que salgamos de ella
    seleccionando los dos paréntesis angulares (**«**) que apuntan hacia
    la izquierda para contraer el panel.

> ![](./media/image20.png)

22. Añadiremos una nueva acción seleccionando el icono **+** debajo de
    la acción **Html to text**, lo cual cargará el panel para añadir
    acciones. Busque **Dataverse add**. Seleccione la acción **Add a new
    row**.

> ![](./media/image21.png)

23. Rename the action by pasting +++Add a new Resume row+++ as the name
    in the upper left-hand corner of the properties panel,

Para el parámetro **Table name**, busque **res** y seleccione la tabla
**Resumes**.

> ![](./media/image22.png)

24. Seleccione a continuación el campo **Resume Title** y seleccione el
    icono **fx** a la derecha.

> ![](./media/image23.png)

25. En la **pestaña** **Function**, introduzca la siguiente expresión
    que utiliza la función item().

+++item()?\['name'\]+++

> Seleccione **Add** para agregar la expresión al parámetro **Resume
> Title**.
>
> ![](./media/image24.png)

**Note on item() function:**

- Cuando utiliza una acción **Apply to each**, Power Automate recorre
  cada elemento de una colección (matriz).

- Se utiliza con mayor frecuencia dentro de acciones como **Apply to
  each** (o **For each**), **Select** o **Filter array**.

26. Aún necesitamos configurar varios parámetros más; seleccione **Show
    all**.

> ![](./media/image25.png)

27. En el campo **Cover Letter**, seleccione el icono **fx icon** a la
    derecha.

> En la **pestaña** **Function** tab, introduzca la siguiente
> expression:
>
> +++if(greater(length(body('Html_to_text')), 2000),
> substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))+++
>
> Esta expresión verifica si el texto de la acción **Html to text**
> tiene más de 2000 caracteres; de ser así, devuelve solo los primeros
> 2000 caracteres; de lo contrario, devuelve el texto completo.
>
> ![](./media/image26.png)

28. La expresión se agregará ahora al campo **Cover Letter**.

> ![](./media/image27.png)

29. Para el campo **Source Email Address**, seleccione el icono del rayo
    y elija el parámetro **From** del desencadenador, ya que este
    contiene el valor de la dirección de correo electrónico.

> ![](./media/image28.png)

30. Para el campo **Upload Date**, eleccione el icono **fx** a la
    derecha. En la pestaña **Function**, introduzca **+++utcNow()+++** y
    seleccione **Add**.

**Nota:** **¿Qué es la función utcNow()?**

- La función **utcnow()** en Power Automate devuelve la fecha y hora
  actuales en Tiempo Universal Coordinado (UTC) en un formato ISO 8601,
  como: 2025-09-23T04:32:14Z

> ![](./media/image29.png)

31. Hemos completado la configuración de la acción **Add a new Resume
    row**, por lo que saldremos del panel contrayéndolo.

> ![](./media/image30.png)

32. Añadiremos una nueva acción seleccionando el icono **+** debajo de
    la acción **Add a new Resume row**, lo cual cargará el panel para
    añadir acciones. Busque **+++Dataverse Upload+++**. Seleccione la
    acción **Upload a file or an image**.

> ![](./media/image31.png)

33. Cambie el nombre de la acción pegando +++Upload Resume File+++ como
    nombre.

> ![](./media/image32.png)

34. Seleccione a continuación el campo **Content name** (Nombre del
    contenido) (elimine el mensaje **Untitled** si ya está disponible) y
    seleccione el icono **fx** a la derecha.

> En la pestaña **Function**, introduzca la siguiente expresión que
> utiliza la función **item()**. Esto obtiene la propiedad de nombre del
> elemento actual (el archivo adjunto).
>
> +++item()?\['name'\]+++
>
> ![](./media/image33.png)

35. Para el parámetro **Table name**, busque +++resumes+++ y seleccione
    la tabla **Resumes**.

> ![](./media/image34.png)

36. Seleccione a continuación el campo **Row ID** y elija el **icono del
    rayo a la derecha**.

> Busque **+++ID+++** y seleccione el parámetro **Resume** de la acción
> de Dataverse **Add a new row**, ya que este contiene el valor del ID
> de la fila en la cual se cargará el archivo PDF.
>
> ![](./media/image35.png)

37. Seleccione el campo **Column name** y seleccione la opción **Resume
    PDF**.

> ![](./media/image36.png)

38. Seleccione el campo **Content** y elija el icono **fx** a la
    derecha.

> En la **pestaña** **Function**, introduzca la siguiente expresión que
> utiliza la función item(). Esto obtiene la propiedad contentBytes del
> elemento actual (el archivo adjunto). contentBytes se refiere a los
> datos binarios sin procesar de un archivo o adjunto, codificados como
> una cadena Base64.
>
> +++item()?\['contentBytes'\]+++
>
> ![](./media/image37.png)

39. Hemos completado la configuración de esta acción, así que salgamos
    de ella seleccionando los dos paréntesis angulares (**«**) que
    apuntan hacia la izquierda para contraer el panel.

> ![](./media/image38.png)

40. A continuación, seleccione la acción **Sends a prompt to the
    specified copilot for processing**, luego arrástrela y suéltela
    debajo de la acción **Upload Resume File** en la
    ruta **True** (Verdadero) de la condición.

> ![](./media/image39.png)

41. Seleccione la acción **Sends a prompt to the specified copilot for
    processing** para configurarla.

![](./media/image40.png)

42. En el campo **Body/message**, seleccione todo el contenido del campo
    y bórrelo/elimínelo.

> ![](./media/image41.png)

43. Copie y pegue el siguiente texto en el campo **Body/message**,
    resalte el texto **RESUME ID PLACEHOLDER** y seleccione el icono del
    rayo.

> Send \[ResumeId (text)\] = "RESUME ID PLACEHOLDER" and \[ResumeTitle
> (text_1)\] = "RESUME TITLE PLACEHOLDER" and \[ResumeNumber (text_2)\]=
> "RESUME NUMBER PLACEHOLDER" to the Tool "Notify Teams Applicant
> channel" in the child agent "Application Intake Agent"
>
> ![](./media/image42.png)

44. Busque **+++resume+++** y seleccione el parámetro **Resume** de la
    acción de *Dataverse* **Add a new row**, ya que este contiene el
    valor del ID de la fila del currículum que se ha creado.

> ![](./media/image43.png)

45. Resalte el texto RESUME TITLE PLACEHOLDER. Seleccione el **icono del
    rayo** a la derecha.

> Busque +++title+++ y seleccione el parámetro **Resume Title** de la
> acción de Dataverse **Add a new row,** ya que este contiene el valor
> del título del currículum de la fila creada.
>
> ![](./media/image44.png)

46. Resalte el texto RESUME TITLE PLACEHOLDER. Seleccione el **icono del
    rayo** a la derecha.

> Busque +++resume number+++ y seleccione el parámetro **Resume Number**
> de la acción de Dataverse **Add a new row**, ya que este contiene el
> valor del número de currículum de la fila creada.
>
> ![](./media/image45.png)

47. Hemos completado la configuración de esta acción y de nuestro flujo
    de agente. Ahora, guardemos nuestro flujo de desencadenador de
    eventos seleccionando **Save**.

> ![](./media/image46.png)

48. Ahora necesitamos editar los detalles del flujo del agente;
    seleccione **Back** una vez guardado.

> ![](./media/image47.png)

49. Seleccione **Edit** en la sección **Details** y actualice
    el **Plan** a la opción **Copilot Studio**. Seleccione **Save**.

> ![](./media/image48.png)

50. Aparecerá una ventana modal para pedirle que confirme el cambio al
    plan de Copilot Studio. Seleccione **Confirm**.

> ![](./media/image49.png)

51. El plan se ha actualizado ahora a **Copilot Studio**. Seleccione
    **Edit**, ya que necesitamos publicar el flujo de desencadenador de
    eventos para nuestro agente.

> ![](./media/image50.png)

52. Seleccione **Publish**.

> ![](./media/image51.png)
>
> El flujo de desencadenador de eventos ya está publicado.

![](./media/image52.png)

Procedamos a crear un nuevo flujo de agente que será invocado por el
agente secundario (child) **Intake Application Agent**.

### Tarea 2 - Notificar a un canal de Teams mediante una tarjeta adaptativa

Ahora vamos a crear un nuevo flujo de agente para el agente secundario
**Intake Application Agent** que utilice los valores pasados por el
desencadenador de eventos para publicar una tarjeta adaptativa en un
canal de Teams. Esta tarjeta adaptativa alertará al equipo de
contratación de RR. HH. sobre el PDF que se cargó automáticamente para
que puedan revisarlo.

#### Tarea 2.1: Crear un canal en Teams

En esta tarea, creará un equipo y un canal en MS Teams que se utilizarán
más adelante en este laboratorio.

1.  Inicie sesión en +++https://teams.microsoft.com+++

2.  Seleccione **New items drop down** y seleccione **New team**.

![](./media/image53.png)

3.  Proporcione los siguientes detalles y seleccione Create.

    - Team name - +++HR Team+++

    - First channel name - +++Applicants +++

> ![](./media/image54.png)

4.  Seleccione Skip en la siguiente pantalla.

![](./media/image55.png)

5.  Ya ha creado el nuevo equipo (Team) y el canal (Channel).

![](./media/image56.png)

#### Tarea 2.2: Crear el flujo del agente

1.  De vuelta en Copilot Studio, dentro del **Hiring** **Agent**,
    seleccione la pestaña **Agents** y seleccione el **Application
    Intake Agent**

![](./media/image57.png)

2.  Desplácese hacia abajo hasta **Tools** y seleccione **+ Add.**

> ![](./media/image58.png)

3.  Aparecerá la ventana modal **Add tool**. Seleccione **+ New tool**.

> ![](./media/image59.png)

4.  Seleccione **Agent flow**.

> ![](./media/image60.png)

5.  A continuación, se cargará el diseñador de flujos del agente. En el
    desencadenador **When an agent calls the flow**, seleccione **+ Add
    an input**.

> ![](./media/image61.png)

6.  Seleccione **Text** como tipo de entrada de usuario.

> ![](./media/image62.png)

7.  En el campo de texto de entrada, escriba +++ResumeId+++ como nombre
    del parámetro de entrada.

> ![](./media/image63.png)

8.  Repita los mismos pasos para los siguientes parámetros.

Text - +++ResumeTitle+++

Text - +++ResumeNumber+++

![](./media/image64.png)

![](./media/image65.png)

9.  Ahora, va a agregar una tarjeta adaptativa en el flujo del agente.
    Vamos a añadir otra acción a nuestro flujo que publicará una tarjeta
    adaptativa en un canal de Teams.

Seleccione el **icono +** debajo del desencadenador.

> ![](./media/image66.png)

10. Busque **+++Microsoft Teams post+++** y seleccione la acción **Post
    card in a chat or channel**.

> ![](./media/image67.png)

11. Es necesario crear una referencia de conexión a **Microsoft Teams**
    con su cuenta de usuario iniciada. Seleccione **Sign in**.

> ![](./media/image68.png)

12. Seleccione su cuenta de usuario y luego seleccione **Allow access**.

> ![](./media/image69.png)

13. Configure de acuerdo con los siguientes parámetros de entrada:

[TABLE]

> ![](./media/image70.png)

14. A continuación, configuraremos el campo **Adaptive Card**.
    Seleccione el campo **Adaptive Card**.

> ![](./media/image71.png)

15. Copie el siguiente código y péguelo en el campo Adaptive Card.

> {
>
> "type": "AdaptiveCard",
>
> "speak": "New Resume Uploaded",
>
> "body": \[
>
> {
>
> "inlines": \[
>
> {
>
> "type": "TextRun",
>
> "size": "Small",
>
> "text": "Resume table updated",
>
> "selectAction": {
>
> "url": "https://adaptivecards.io",
>
> "type": "Action.OpenUrl"
>
> }
>
> }
>
> \],
>
> "type": "RichTextBlock"
>
> },
>
> {
>
> "columns": \[
>
> {
>
> "width": "auto",
>
> "items": \[
>
> {
>
> "type": "Icon",
>
> "name": "DocumentArrowUp",
>
> "color": "Accent"
>
> }
>
> \],
>
> "type": "Column"
>
> },
>
> {
>
> "width": "stretch",
>
> "items": \[
>
> {
>
> "size": "Large",
>
> "text": "New Resume Uploaded",
>
> "weight": "Bolder",
>
> "wrap": true,
>
> "type": "TextBlock"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center",
>
> "spacing": "Small",
>
> "type": "Column"
>
> }
>
> \],
>
> "spacing": "Small",
>
> "type": "ColumnSet"
>
> },
>
> {
>
> "type": "Table",
>
> "targetWidth": "AtLeast:Narrow",
>
> "columns": \[
>
> {
>
> "width": 1
>
> },
>
> {
>
> "width": 2
>
> }
>
> \],
>
> "rows": \[
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Resume Number",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "RESUME NUMBER PLACEHOLDER",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Name",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "RESUME NAME PLACEHOLDER",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Status",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Waiting for Review",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Due Date",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "May 21, 2023",
>
> "wrap": true
>
> }
>
> \]
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Priority",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "ColumnSet",
>
> "columns": \[
>
> {
>
> "type": "Column",
>
> "width": "auto",
>
> "items": \[
>
> {
>
> "type": "Icon",
>
> "name": "Flag",
>
> "color": "Attention",
>
> "size": "xSmall",
>
> "horizontalAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "Column",
>
> "width": "stretch",
>
> "items": \[
>
> {
>
> "color": "Attention",
>
> "text": "Important",
>
> "wrap": true,
>
> "spacing": "Small",
>
> "type": "TextBlock"
>
> }
>
> \],
>
> "spacing": "Small"
>
> }
>
> \],
>
> "spacing": "Small"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> }
>
> \],
>
> "firstRowAsHeaders": false,
>
> "showGridLines": false
>
> },
>
> {
>
> "actions": \[
>
> {
>
> "title": "View Resume",
>
> "type": "Action.OpenUrl",
>
> "url": "https://adaptivecards.io/"
>
> }
>
> \],
>
> "type": "ActionSet",
>
> "targetWidth": "AtLeast:Narrow",
>
> "spacing": "ExtraLarge"
>
> }
>
> \],
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
>
> "version": "1.5"
>
> }

![](./media/image72.png)

16. Ahora reemplazaremos los valores existentes en el JSON por valores
    reales o contenido dinámico.

> En primer lugar, actualicemos la dirección URL de la propiedad **url**
> dentro de la propiedad **selectAction** (o del bloque de acciones).
> Esta URL se sustituirá por la de la vista de sistema **Resumes**
> (Currículums) en la aplicación basada en modelos **Hiring Hub**. Esto
> permitirá que el reclutador seleccione la acción y sea dirigido a
> dicha vista en la aplicación. Resalte el valor de la URL actual y
> elimínelo.
>
> Resalte el valor de la **URL actual** y elimínelo.

![](./media/image73.png)

17. En la aplicación basada en modelo **Hiring Hub**, navegue a la vista
    del sistema **Resumes** utilizando el menú del lado izquierdo y
    copie la URL. Luego, **regrese** al **flujo del agente** y **pegue**
    **la** **URL** **copiada** en la propiedad url dentro de la
    propiedad selectAction.

> ![](./media/image74.png)

18. Debería ver lo siguiente, donde lo resaltado en amarillo corresponde
    a los detalles de su entorno de la aplicación basada en modelos
    **Hiring Hub**.

[TABLE]

> ![](./media/image75.png)

19. A continuación, agregaremos valores de contenido dinámico para
    varias propiedades. Comencemos con el texto que mostrará la
    referencia del Resume Number (Número de currículum) de la fila que
    fue creada de forma autónoma por el desencadenador de eventos.

Seleccione el icono del **panel** para cargar el panel de acciones.

![](./media/image76.png)

20. Desplácese hacia abajo hasta la línea donde vea la propiedad text
    para RESUME NUMBER PLACEHOLDER. Resalte el valor del marcador de
    posición y elimínelo.

![Delete placeholder](./media/image77.png)

21. Haga clic entre las comillas dobles y seleccione el **icono del
    rayo** que aparece a la derecha.

![](./media/image78.png)

22. En la pestaña **Dynamic Content**, seleccione el parámetro
    **ResumeId**.

> ![](./media/image79.png)

23. El parámetro **ResumeNumber** se agregará ahora como contenido
    dinámico a la propiedad de texto.

> ![](./media/image80.png)

24. Repetiremos los mismos pasos para el marcador de posición RESUME
    NAME PLACEHOLDER. Desplácese hacia abajo hasta la línea donde vea la
    propiedad text para RESUME NAME PLACEHOLDER. Resalte el valor del
    marcador de posición y elimínelo. Haga clic entre las comillas
    dobles y seleccione el **icono del rayo** (contenido dinámico) de la
    derecha.

> ![](./media/image81.png)

25. En la pestaña **Dynamic Content**, seleccione el parámetro
    **ResumeTitle**.

> ![](./media/image82.png)

26. El parámetro **ResumeTitle** se agregará ahora como contenido
    dinámico a la propiedad de texto.

> ![](./media/image83.png)

27. Repetiremos los mismos pasos para el valor **Due Date** que
    representa cuándo debe revisar el currículum un reclutador.
    Desplácese hacia abajo hasta la línea donde vea la propiedad text
    con el valor May 21, 2023.

![Select Allow access](./media/image84.png)

28. Elimine este valor de marcador de posición de fecha, haga clic entre
    las comillas dobles y seleccione el **icono fx** de la derecha.

> ![](./media/image85.png)

29. En la pestaña **Function**, introduzca la siguiente expresión y
    seleccione **Add**.

> +++addDays(utcNow(), 3, 'MMM dd, yyyy')+++

Esta expresión utiliza dos funciones.

[TABLE]

Para el valor utcNow, estamos dando formato a la fecha para que muestre
el mes y el día, seguidos del año.

> ![](./media/image86.png)

30. La expresión se agregará ahora a la propiedad text.

![](./media/image87.png)

31. Por último, actualizaremos la dirección URL de la propiedad **url**
    dentro de la matriz de acciones (**actions**) en la parte inferior
    del JSON. Esta URL provisional se sustituirá por la URL de la fila
    específica del **Resume** (Currículum) en la aplicación basada en
    modelos **Hiring Hub**. Esto permitirá que el reclutador seleccione
    la acción **Action.OpenURL** de la tarjeta adaptativa y sea dirigido
    directamente al registro del currículum en la aplicación.

> ![](./media/image88.png)

32. En la aplicación basada en modelos **Hiring Hub**, abra una fila en
    la vista de sistema **Resumes** (Currículums) utilizando el menú del
    lado izquierdo. La fila del currículum se cargará como un formulario
    en la aplicación.

Copie la URL de la fila del currículum.

![](./media/image89.png)

> ![](./media/image90.png)

33. Luego, regrese al flujo del agente, resalte el valor de la URL
    provisional actual y **elimínelo**.

> ![](./media/image91.png)

34. Luego, **pegue** la **URL copiada** en la propiedad **url** (dentro
    de la sección de acciones).

> ![](./media/image92.png)

35. Debería ver lo siguiente. Elimine el valor del ID (GUID) al final de
    la dirección. Lo reemplazaremos con contenido dinámico: el parámetro
    **ResumeId**.

![](./media/image93.png)

36. Seleccione el **icono del rayo** (contenido dinámico) de la
    derechat.

En la pestaña **Dynamic Content** (Contenido dinámico), seleccione el
parámetro **ResumeId**.

> ![](./media/image94.png)

37. El **ResumeId** se agregará como contenido dinámico. Lo resaltado en
    amarillo a continuación representa los detalles de su entorno de la
    aplicación basada en modelos **Hiring Hub**.

[TABLE]

> ![](./media/image95.png)

38. Hemos completado la configuración de la acción **Post card in a chat
    or channel** (Publicar tarjeta en un chat o canal) 👏🏻 Salga del
    panel de configuración de la acción seleccionando el icono x.

> ![](./media/image96.png)

39. Finalmente, configuraremos la última acción, **Respond to the
    agent** (Responder al agente), enviando un texto de vuelta al agente
    para finalizar el procesamiento.

En la acción **Respond to the agent**, seleccione **+Add an output**.

> ![](./media/image97.png)

40. Seleccione **Text** (Texto) como tipo de salida.

> ![](./media/image98.png)

41. Introduzca los siguientes detalles

    - Name - +++EndConversation+++

    - Value - +++ Finished+++

> ![](./media/image99.png)

42. Ya hemos completado la configuración del flujo del agente.
    Seleccione **Save draft** (Guardar borrador) para guardar el flujo
    del agente. Aparecerá un mensaje de confirmación una vez guardado.

> ![](./media/image100.png)

43. Antes de publicar el flujo del agente, debemos actualizar sus
    detalles. Seleccione la pestaña **Overview** (Información general) y
    seleccione **Edit** (Editar).

> ![](./media/image101.png)

44. Ingrese el nombre como +++Notify Teams Applicant channel+++
    (Notificar al canal de aplicantes en Teams) y seleccione el icono de
    actualización (Refresh) debajo de la descripción para actualizarla
    mediante IA.

![](./media/image102.png)

45. Una vez que se haya completado la descripción, seleccione **Save**
    para guardar los detalles actualizados del flujo del agente.

> ![](./media/image103.png)

46. Regrese a la pestaña **Designer** y seleccione **Publish** para
    publicar el flujo del agente.

> ![](./media/image104.png)

47. Aparecerá un mensaje de confirmación una vez que se haya publicado.

> ![](./media/image105.png)

48. El flujo del agente ahora debe agregarse como una herramienta en el
    **Application Intake Agent**. Regrese al **Hiring Agent**,
    seleccione la pestaña **Agents** y, a continuación, seleccione el
    **Application Intake Agent**.

![](./media/image106.png)

49. En la sección **Details** del agente, actualizaremos el campo
    **Description**. Copie lo siguiente y péguelo al final del texto de
    la descripción:

+++and also notifies the Teams Applicant channel+++

Seleccione **Save**.

> ![](./media/image107.png)

50. A continuación, agregaremos el flujo del agente como una
    herramienta. Desplácese hacia abajo hasta la sección **tools** y
    seleccione**+ Add**.

> ![](./media/image108.png)

51. Seleccione la pestaña **Flow** y elija el flujo del agente creado
    anteriormente, **Notify Teams Applicant Channel**.

> ![](./media/image109.png)

52. A continuación, seleccione **Add and configure**.

> ![](./media/image110.png)

53. En la sección **Inputs**, son visibles las tres entradas que
    configuramos anteriormente en el flujo del agente. Por defecto, la
    configuración **Fill using** está establecida en **Dynamically fill
    with AI**. Mantendremos esta configuración tal cual, ya que la
    instrucción del desencadenador del evento contendrá los valores de
    los parámetros que la IA extraerá.

> ![](./media/image111.png)

54. Ahora que se ha agregado la herramienta al **Application Intake
    Agent**, es necesario actualizar las instrucciones del agente.
    Seleccione la **flecha hacia atrás**.

![](./media/image112.png)

55. Seleccione el **Application Intake Agent** en la pestaña **Agents**
    del **Hiring Agent**.

![](./media/image113.png)

56. En el campo **Instructions**, introduzca una nueva línea después de
    **2.Post-Upload instructions**. Copie y pegue las siguientes
    instrucciones.

> Process for Resume Upload via Email
>
> 1. When you receive a message, \*\*Send \[ResumeId (text)\] =
> "1680265f-5793-f011-b41b-7c1e525be9f7" and \[ResumeTitle (text_1)\] =
> "TAYLOR TESTPERSON (FICTITIOUS).pdf" and \[ResumeNumber (text_2)\]=
> "R01026" to the Tool "Notify Teams Applicant channel"\*\* in the child
> agent "Application Intake Agent", call \[AGENT FLOW PLACEHOLDER\]
>
> ![](./media/image114.png)

57. Resalte el texto \[AGENT FLOW PLACEHOLDER\].

> ![](./media/image115.png)

58. Escriba el carácter de barra diagonal, **/**, y seleccione la
    herramienta **Notify Teams Applicant Channel**.

> ![](./media/image116.png)

59. El flujo del agente ahora será invocado por el **Application Intake
    Agent** siguiendo las instrucciones, después de que la última acción
    (**Sends a prompt to the specified copilot for processing**) en el
    desencadenador del evento envíe la instrucción que contiene los
    valores de los parámetros de vuelta al agente.

Seleccione **Save** para guardar las instrucciones actualizadas para el
**Application Intake Agent**.

> ![](./media/image117.png)

60. Las instrucciones se actualizarán una vez que se haya guardado el
    agente.

> ![](./media/image118.png)

61. Ahora necesitamos publicar el **Hiring Agent**. Seleccione
    **Publish** en la parte superior derecha y, en el cuadro de diálogo
    **Publish this agent** que aparece, seleccione de nuevo **Publish**.

> ![](./media/image119.png)
>
> ![](./media/image120.png)

62. Una vez publicado, aparecerá un mensaje de confirmación indicando
    que el agente ha sido publicado.

> ![](./media/image121.png)

¡Ahora podemos probar el agente!

## Ejercicio 3: Probar el desencadenador de evento

En este ejercicio, probará el desencadenador de evento (event trigger)
creado en este laboratorio.

1.  Para ejecutar el desencadenador de evento, se debe enviar un correo
    electrónico con un archivo PDF de un currículum. En Outlook, redacte
    un nuevo mensaje de correo electrónico.

[TABLE]

> Dear Hiring Manager,
>
> I am writing to express my interest in the Senior Power Platform
> Engineer position at your organization. With over nine years of
> experience delivering secure and scalable solutions on Microsoft cloud
> platforms, I am confident in my ability to contribute effectively to
> your team.
>
> In my most recent role as Lead Power Platform Engineer, I developed an
> automated resume-intake pipeline, reducing manual triage and improving
> searchability. I have delivered HR case management applications,
> introduced solution-aware flows, and implemented PR checks to enhance
> deployment lead times. My expertise includes Power Apps, Power
> Automate, Power Pages, Dataverse, and a range of Microsoft 365
> services, as well as integration with Graph/REST APIs and Azure
> Functions.
>
> Previously, I developed Teams approvals with adaptive cards, cutting
> approval times to the same day, and created robust error-handling
> frameworks. My background also includes migrating legacy workflows to
> Power Automate and building self-service portals adopted by hundreds
> of employees.
>
> I hold a B.Sc. in Computer Science and am certified as a Power
> Platform Developer (PL-400) and Solution Architect (PL-600). I am also
> passionate about mentoring and have volunteered with local maker
> groups.
>
> Please find my CV attached for your consideration. I would welcome the
> opportunity to discuss how my skills and experience align with your
> needs.
>
> Thank you for your time and consideration.
>
> Kind regards,
>
> Taylor Testperson

2.  **Envíe** el correo electrónico una vez redactado desde su buzón de
    correo.

> ![](./media/image122.png)

3.  En +++<https://make.powerautomate.com/>+++, dentro del flujo del
    desencadenador de evento (event trigger), seleccione el icono
    Refresh (Actualizar) para ver la ejecución del flujo que resultó
    exitosa tras el envío del correo. Podrá ver que el flujo se ha
    ejecutado correctamente.

> ![](./media/image123.png)

4.  De vuelta en **Copilot Studio**, dentro del **Hiring Agent**,
    seleccione la pestaña **Activity**. Se cargará la pestaña de
    actividad, la cual mostrará todas las actividades del agente. Habrá
    una actividad con el nombre **Automated** que tiene un estado de
    **Complete**. Esta actividad representa el desencadenador del evento
    y el flujo del agente que fue invocado.

> ![](./media/image124.png)

5.  Seleccione la actividad y elija el **event trigger** (desencadenador
    de evento) en el mapa de actividad. En el panel del lado derecho,
    observe cómo los parámetros de entrada en la instrucción (prompt)
    contienen los valores de **Resume Id**, **Resume Title** y **Resume
    Number** de la fila de Dataverse que se creó. Esto proviene de los
    valores de contenido dinámico configurados anteriormente en la
    automatización de carga de currículos a Dataverse recibidos por
    correo electrónico.

> ![](./media/image125.png)

6.  Regrese a la aplicación basada en modelos Hiring Hub y, en la
    **vista del sistema Resumes**, seleccione **Refresh** para
    actualizar la vista. La fila recién creada para el currículum
    enviado por correo electrónico aparecerá ahora en la lista, ya que
    fue creada a través del desencadenador de evento.

> ![](./media/image126.png)

7.  Regrese a **Copilot Studio** y seleccione el flujo del agente
    **Notify Teams Applicant Channel** dentro del **Application Intake
    Agent** en el mapa de actividad. En el panel del lado derecho,
    observe cómo las entradas tienen valores de la fila de Dataverse.
    Esto proviene de la instrucción (prompt) enviada por la última
    acción (**Sends a prompt to the specified copilot for processing**)
    en el desencadenador del evento, la cual contiene los valores de los
    parámetros de la fila de Dataverse recién creada. Así es como
    podemos pasar valores de parámetros desde los desencadenadores de
    eventos a los flujos del agente..

> ![](./media/image127.png)

8.  Finalmente, echemos un vistazo a la tarjeta adaptativa publicada en
    el canal de **Microsoft Teams**. En el canal, veremos la tarjeta
    adaptativa que muestra la información sobre la fila de **Resume**
    recién creada en Dataverse. Pase el cursor sobre el hipervínculo al
    principio de la tarjeta adaptativa y observe que la URL es la URL de
    la vista del sistema de currículums que configuramos anteriormente
    en el JSON de la tarjeta adaptativa.

> ![](./media/image128.png)

9.  Seleccione el hipervínculo y será dirigido a la vista del sistema
    Resumes en la aplicación basada en modelos **Hiring Hub** en su
    navegador.

> ![](./media/image129.png)

10. Regrese a la tarjeta adaptativa publicada en el canal de Microsoft
    Teams. Esta vez, pase el cursor sobre **View Resume** (Ver
    currículum), que es la acción Action.OpenURL de la tarjeta
    adaptativa. Observe que la URL es la fila de curriculums (Resumes
    row) específica que configuramos anteriormente en el cuerpo
    (payload) JSON de la tarjeta.

> ![](./media/image130.png)

11. Seleccione la acción y será dirigido al formulario de la fila de
    Resumes en la aplicación basada en modelos Hiring Hub en su
    navegador.

> ![](./media/image131.png)

## Resumen

En este laboratorio,

1.  Ha creado un desencadenador de evento (event trigger) que transfiere
    los valores de los parámetros de Dataverse a un flujo del agente.

2.  Ha creado un flujo del agente: este consume los valores de los
    parámetros de Dataverse para publicar una tarjeta adaptativa en un
    canal de Microsoft Teams y así alertar al equipo de selección de RR.
    HH.

3.  Ha actualizado las instrucciones del agente secundario: para invocar
    el flujo una vez que el desencadenador del evento se haya
    completado.

4.  Esto permite que el **Hiring Agent** trabaje de forma autónoma cada
    vez que se reciban currículos como archivos adjuntos por correo
    electrónico y notifique al equipo de selección de RR. HH. para su
    revisión manual.
