# Laboratorio 3 - Arquitectura de agentes inteligentes con base de conocimiento (grounding) y conectores en vivo

**Introducción**

Los usuarios modernos esperan respuestas inteligentes y contextuales que
vayan más allá de la simple coincidencia de palabras clave. Este
laboratorio le guiará en la creación de un agente inteligente capaz de
razonar a través de múltiples fuentes de conocimiento y realizar
acciones en tiempo real para ofrecer respuestas completas y precisas.

**Objetivo**

En este laboratorio, construirá un asistente inteligente que supera el
esquema básico de preguntas y respuestas para ofrecer interacciones
contextuales y complejas. Al finalizar, usted habrá logrado:

• Crear un agente inteligente mediante la experiencia de creación
conversacional.

• Configurar el tono, comportamiento e instrucciones del agente para
reflejar su marca.

• Agregar sitios web públicos (como Wikipedia) como fuentes de
conocimiento para fundamentar los datos (grounding).

• Desactivar el conocimiento general para reducir alucinaciones y
garantizar la precisión.

## Tarea 1: Crear un nuevo agente y agregar conocimiento

Cree "Nova AI" con instrucciones personalizadas e integración de
Wikipedia utilizando la configuración conversacional de Copilot Studio.

1.  Abra un navegador, dirijase a +++copilotstudio.microsoft.com+++ e
    inicie sesión con sus credenciales.

2.  Seleccione el entorno **Dev One**.

3.  En la página de inicio, seleccione **Create agent**.

![](./media/image1.png)

4.  Una vez que el agente esté creado, seleccione **Edit** junto a
    **Details**.

![](./media/image2.png)

5.  Ingrese los siguientes detalles y seleccione **Save**.

    - Name - +++Researcher agent+++.

    - Description - +++Answers multi-part questions by combining
      historical facts, biographical data, and real-time information
      like weather. Ideal for deep research, exploration, and knowledge
      synthesis+++

> ![](./media/image3.png)

6.  Ingrese el siguiente contenido en el apartado **Instructions** y
    seleccione **Save**.

You should answer complex questions using verified public information
and real-time lookups like weather or conversions. You should give
clear, concise answers and handle multiple questions one at a time. You
must not speculate, share unverified or sensitive information, or
compare products or companies. You should communicate clearly and
professionally, using a friendly tone and light emojis when appropriate.

![](./media/image4.png)

7.  Desplácese hacia abajo y seleccione **+ Add knowledge** para añadir
    una fuente de conocimiento.

![](./media/image5.png)

8.  Seleccione la opción **Public Website** de la lista.

![](./media/image6.png)

9.  Seleccione **Add** en la siguiente pantalla y luego **Add to
    agent**.

![](./media/image7.png)

![](./media/image8.png)

10. A continuación, desactivará el conocimiento general para reducir las
    alucinaciones. Seleccione **Settings** en la parte superior derecha.

![](./media/image9.png)

11. Desactive la opción **Use general knowledge** dentro de la sección
    Knowledge.

![](./media/image10.png)

12. Ingrese el siguiente mensaje en el panel de prueba, haga clic en
    **Send** y observe el resultado:

> Write a draft email to request refund from a toaster that is not
> working properly (bread keeps burning)

![](./media/image11.png)

![](./media/image12.png)

## Tarea 2: Agregar el conector de clima

En esta tarea, agregará un conector de clima para permitir la
recuperación de datos en tiempo real y probar la orquestación
generativa. Asegúrese de que el agente proporcione únicamente respuestas
controladas y basadas en hechos, al tiempo que le permite realizar
acciones en tiempo real, como consultas meteorológicas, para ofrecer
respuestas integrales de varios pasos.

1.  Seleccione la pestaña **Tools** en el menú superior.

![](./media/image13.png)

2.  Escriba +++MSN Weather+++ en el cuadro de búsqueda y seleccione
    **Get current weather**.

![](./media/image14.png)

3.  Seleccione el menú desplegable junto al mensaje **Not connected** y
    seleccione **Create new connection**. Luego, seleccione **Create**
    en la siguiente pantalla.

![](./media/image15.png)

![](./media/image16.png)

4.  Seleccione **Add and configure** para añadir la herramienta al
    agente y configurarla según sea necesario.

![](./media/image17.png)

5.  Una vez agregada, seleccione **Additional details**.

![](./media/image18.png)

6.  En el apartado Credentials to use, seleccione **Maker-provided
    credentials**.

**Nota:** Al utilizar Maker-provided credentials, no se le pedirá al
usuario final del agente que utilice su propio contexto o conexión para
vincularse al servicio. En su lugar, se utilizará el contexto y la
conexión de la persona que configuró el agente. - Utilice la
autenticación del autor únicamente para acciones que no requieran datos
específicos del usuario, ya que el uso de credenciales ajenas puede
exponer el sistema a riesgos de filtración de datos. - Utilice la
autenticación de usuario para escenarios de acceso basado en roles
(RBAC) - Revise siempre las implicaciones de seguridad de sus elecciones
de autenticación

![](./media/image19.png)

7.  En la sección **Inputs**, **Units**, -\> **Fill using** -\>
    seleccione **Custom value**, y elija **Metric**.

![](./media/image20.png)

8.  En la sección **Inputs**, para **Location**, deje la opción **Fill
    using to Dynamically fill with AI**, y seleccione **Customize** para
    configurar la descripción.

![](./media/image21.png)

9.  Establezca la descripción como se indica a continuación y luego
    seleccione **Save**.

The location for the weather query. Valid inputs are City, State,
Country. Always include city and country, and state only for locations
where appropriate (e.g., in the US)

![](./media/image22.png)

![](./media/image23.png)

10. Pruebe su agente mejorado con esta pregunta compleja:

> Who is the current CEO of the company that owns GitHub? Where did they
> earn their MBA? What's the average rent for a one-bedroom apartment
> near that campus? What's the air quality index in that area today?

![](./media/image24.png)

11. Observe cómo la orquestación generativa realiza múltiples búsquedas
    y activa el conector de clima para proporcionar una respuesta
    integral

![](./media/image25.png)

Tarea 3: Ajuste fino de su asistente de IA para conversaciones más
fluidas

Personalice los temas del sistema para mejorar las interacciones y
ofrecer una experiencia de usuario más fluida.

En esta sección, personalizará los temas del sistema integrados para
mejorar las interacciones con el usuario y crear una experiencia sin
interrupciones que vaya más allá de las fuentes de conocimiento.

Personalice el mensaje de bienvenida de su asistente para hacerlo más
atractivo, añada sugerencias de inicio para guiar a los usuarios de
manera efectiva y refine los temas del sistema, como Escalate, para
asegurar que se alineen con las necesidades de su organización.

1.  En el menú superior, seleccione **Topics**.

![](./media/image26.png)

2.  Seleccione el tema **Conversation Start** dentro de la sección
    **System**.

![](./media/image27.png)

3.  En el nodo **Message** del tema, ingrese el mensaje que se indica a
    continuación.

> Hi there! I'm Researcher agent, your intelligent assistant for deep
> research and discovery. I can break down complex questions and combine
> insights from historical facts, biographies, and real-time data like
> the weather. What are you curious about today?
>
> ![](./media/image28.png)

4.  En el mismo nodo, seleccione **+ Add** -\> **Quick reply**.

![](./media/image29.png)

5.  Añada la siguiente pregunta.

+++What caused the fall of the Roman Empire?+++

![](./media/image30.png)

6.  De la misma manera, añada 2 más.

> +++Who is the current CEO of the company that owns GitHub? Where did
> they earn their MBA? What's the average rent for a one-bedroom
> apartment near that campus? What's the air quality index in that area
> today?+++
>
> +++What's the temperature in the city that hosted the last Olympic
> Games?+++

![](./media/image31.png)

7.  Una vez añadidos, seleccione **Save** para guardar el tema.

![](./media/image32.png)

8.  Personalice la experiencia de escalación. Seleccione **Topics** -\>
    **System** -\> **Escalate**.

![](./media/image33.png)

9.  Actualice el texto con el que se indica a continuación, el cual
    ayudará a desbloquear al usuario final de manera más efectiva, y
    seleccione **Save**.

> I'm sorry, but I can't seem to be able to help you. I recommend
> reaching out to our \[Microsoft Copilot Studio community\]
> (https://aka.ms/CopilotStudioCommunity) or submitting a \[support
> request\]
> (<https://learn.microsoft.com/en-us/power-platform/admin/get-help-support>).

![](./media/image34.png)

## Tarea 4: Hacer público su agente y publicarlo en el sitio web de demostración

En esta sección, eliminará la autenticación para que su agente sea
accesible públicamente y, a continuación, lo publicará en el sitio web
de demostración para realizar pruebas y compartirlo. Dado que el agente
de investigación proporciona información general y no maneja datos
privados, desactivará la autenticación para ofrecer una experiencia de
usuario fluida y lo publicará en el sitio web de demostración para
recopilar comentarios antes de implementarlo en su sitio real.

1.  Vaya a **Settings** .

![](./media/image35.png)

2.  Seleccione **Security** -\> **Authentication**. Seleccione **No
    authentication** y luego seleccione **Save**.

![](./media/image36.png)

3.  Seleccione **prompt** en el mensaje de confirmación.

![](./media/image37.png)

4.  Ahora puede cerrar el panel de Settings.

![](./media/image38.png)

5.  Seleccione **Publish** para que sus cambios entren en vigor.

![](./media/image39.png)

6.  Seleccione **Publish** en el cuadro de diálogo de confirmación.

![](./media/image40.png)

7.  Recibirá un mensaje de éxito una vez que la publicación haya
    finalizado.

![](./media/image41.png)

8.  Ahora, seleccione **Channels** en el menú superior.

![](./media/image42.png)

9.  Seleccione **Demo website** de la lista de canales disponibles.

![](./media/image43.png)

10. Ingrese el **Welcome message** como +++Welcome to your demo
    website+++ y seleccione **Save**.

![](./media/image44.png)

11. Haga clic en **Open demo website** para abrir su sitio.

![](./media/image45.png)

12. Ahora puede interactuar con su agente.

![](./media/image46.png)

## Resumen

En este laboratorio, usted ha entregado con éxito un agente inteligente
orientado al público que:

- Responde preguntas de investigación complejas y de múltiples partes.

- Utiliza conocimiento público verificado y conectores en tiempo real.

- Minimiza las alucinaciones mediante fuentes de conocimiento
  controladas.

- Proporciona una experiencia conversacional pulida y fácil de usar.

- Está desplegado y es accesible a través de un sitio web de
  demostración en vivo.

Este laboratorio demuestra cómo diseñar, mejorar y publicar un **agente
inteligente listo para producción** que va más allá de una simple
sección de preguntas y respuestas (Q&A) para ofrecer información
confiable, en tiempo real y consciente del contexto.
