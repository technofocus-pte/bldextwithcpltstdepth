# Laboratorio - Transformando el agente de contratación en una arquitectura multiagente escalable

En el laboratorio anterior, construyó su agente de contratación
principal, lo que le proporcionó una base sólida para gestionar los
flujos de trabajo de reclutamiento. Pero un solo agente tiene sus
límites.

Su misión, si decide aceptarla, es la **Operación Sinfonía**:
transformar su agente individual en un **sistema multiagente**; un
equipo orquestado de agentes especializados que trabajan juntos para
resolver desafíos de contratación complejos. Piense en ello como pasar
de ser un operador solitario a comandar un equipo de fuerzas especiales.

Al igual que una orquesta sinfónica donde cada músico toca su parte en
perfecta armonía, añadirá dos especialistas críticos a su agente de
contratación actual: un Application Intake Agent para procesar
currículums automáticamente y un Interview Prep Agent para crear
materiales de entrevista detallados. Estos agentes trabajarán en
conjunto sin interrupciones bajo la dirección de su orquestador
principal.

Tras crear los multiagentes, transformará sus agentes para que dejen de
esperar la intervención humana y comiencen a responder proactivamente a
eventos externos, tomando acciones inteligentes sin supervisión.

Piense en ello como una actualización: de agentes que responden
preguntas a agentes que anticipan necesidades y actúan de forma
independiente. Mediante disparadores de eventos y flujos de trabajo
automatizados, su Agente de Contratación detectará correos electrónicos
con currículums entrantes, procesará los adjuntos automáticamente,
almacenará los datos en Dataverse y notificará a su equipo de
reclutamiento de RR.HH. a través de Microsoft Teams; todo esto mientras
usted se concentra en tareas de mayor valor.

## Objetivos

En esta misión, aprenderá:

1.  Cuándo usar agentes hijos (**child agents**) frente a **agentes**
    **conectados.**

2.  Cómo diseñar **arquitecturas multiagente** que sean escalables.

3.  Cómo crear **agentes hijos** para tareas específicas.

4.  Cómo establecer **patrones de comunicación** entre agentes.

5.  La construcción del Application Intake Agent y del Interview Prep
    Agent.

6.  Cómo los disparadores de eventos permiten un comportamiento autónomo
    del agente sin interacción del usuario.

7.  Las diferencias entre agentes interactivos y autónomos en Copilot
    Studio.

8.  Cómo crear disparadores de eventos que procesen automáticamente
    archivos adjuntos de correo electrónico y carguen archivos en
    Dataverse.

9.  Cómo construir flujos de agentes que publiquen Adaptive Cards en
    canales de Teams para notificaciones.

10. Cómo pasar datos entre disparadores de eventos y flujos de agentes
    para una automatización de extremo a extremo.

## Agente hijo: Application Intake Agent

Comencemos a construir nuestro sistema de contratación multiagente.
Nuestro primer especialista será el **Application Intake Agent**, un
agente hijo responsable de procesar los currículums entrantes y la
información de los candidatos.

![](./media/image1.png)

**Responsabilidades del Application Intake Agent**

- **Analizar el contenido de currículums** a partir de PDFs
  proporcionados a través del chat interactivo (en una misión futura
  aprenderá a procesarlos de forma autónoma).

- **Extraer datos estructurados** (nombre, habilidades, experiencia,
  educación)

- **Vincular candidatos con roles vacantes** basándose en sus
  cualificaciones y carta de presentación

- **Almacenar la información del candidato** en Dataverse para su
  procesamiento posterior

- **Deduplicar solicitudes** para evitar crear el mismo candidato dos
  veces, comparando con registros existentes mediante la dirección de
  correo electrónico extraída del currículum

**Por qué debería ser un agente hijo (child agent)**

El Application Intake Agent encaja perfectamente como un agente hijo
porque:

- Está diseñado específicamente para el procesamiento de documentos y la
  extracción de datos

- No requiere una publicación por separado, lo que facilita el control
  de versiones

- Forma parte de nuestra solución de contratación global gestionada por
  el mismo equipo

- Se centra en un desencadenador específico (recepción de un nuevo
  currículum) y es invocado desde el Hiring Agent (Agente de
  Contratación).

## Agente conectado: Interview Prep Agent

Nuestro segundo especialista será el **Interview Prep Agent**, un agente
conectado que ayuda a crear materiales de entrevista exhaustivos y
evalúa las respuestas de los candidatos.

**Responsabilidades del Interview Prep Agent**

- **Crear paquetes de entrevista** con información de la empresa,
  requisitos del puesto y criterios de evaluación

- **Generar preguntas de entrevista** personalizadas para roles
  específicos y antecedentes de los candidatos

- **Responder preguntas generales** sobre los roles de trabajo y las
  solicitudes para la comunicación con los interesados (stakeholders).

**¿Por qué debería ser un agente conectado (connected agent)?**

El Interview Prep Agent funciona mejor como un agente conectado porque:

- El equipo de adquisición de talento podría querer usarlo de forma
  independiente en múltiples procesos de contratación

- Necesita su propia base de conocimientos sobre mejores prácticas de
  entrevista y criterios de evaluación

- Diferentes gerentes de contratación podrían querer personalizar su
  comportamiento para sus equipos específicos

- Podría reutilizarse para puestos internos, no solo para contrataciones
  externas

## Ejercicio 1: Añadir el Application Intake Agent

Vamos a añadir nuestro primer agente hijo a su Agente de Contratación
(Hiring agent) existente.

### Tarea 1: Configuración de la solución

1.  Dentro de Copilot Studio, seleccione los puntos suspensivos (...)
    debajo de Tools en la navegación de la izquierda.

2.  Seleccione **Solutions**.

> ![](./media/image2.png)

3.  Localice su solución **Operative**, seleccione los puntos
    suspensivos (**...**) junto a ella y elija **Set preferred
    solution**. Seleccione **Apply** en el cuadro de diálogo que
    aparezca. Esto asegurará que todo su trabajo se agregue a esta
    solución.

> ![](./media/image3.png)

4.  Seleccione Apply en el cuadro de diálogo Set your preferred
    solution.

![](./media/image4.png)

### Tarea 2 - Configurar las instrucciones de su Agente de Contratación

1.  **Navegue** a Copilot Studio. Asegúrese de que su entorno esté
    seleccionado en el **Environment Picker** en la parte superior
    derecha.

2.  Abra el **Hiring Agent** (Agente de Contratación).

3.  Seleccione **Edit** en la sección **Instructions** de la pestaña
    **Overview** del agente.

![](./media/image5.png)

4.  Copie y pegue las siguientes instrucciones en el campo de entrada de
    instrucciones.

**You are the central orchestrator for the hiring process. You
coordinate activities, provide summaries, and delegate work to
specialized agents.**

5.  Seleccione **Save**.

> ![](./media/image6.png)

6.  Seleccione el botón **Settings** en la parte superior derecha de la
    pantalla.

> ![](./media/image7.png)

7.  Revise la página, asegúrese de que se apliquen las siguientes
    configuraciones y luego seleccione **Save**.

[TABLE]

> ![](./media/image8.png)
>
> ![](./media/image9.png)
>
> ![](./media/image10.png)
>
> ![](./media/image11.png)

8.  Haga clic en la **X** en la esquina superior derecha para cerrar el
    menú de configuración.

> ![](./media/image12.png)

### Tarea 3: Añadir el agente hijo Application Intake

En esta tarea, añadirá un agente hijo al Agente de Contratación (Hiring
Agent).

1.  **Navegue** a la pestaña **Agents** dentro de su **Hiring Agent**
    (aquí es donde añadirá los agentes especialistas) y seleccione
    **Add**.

![](./media/image13.png)

2.  Seleccione **New child agent**.

![](./media/image14.png)

3.  **Nombre** a su agente +++Application Intake Agent+++

4.  Seleccione **The agent chooses** - Based on description en el menú
    desplegable **When will this be used?**. Estas opciones son
    similares a los desencadenadores que se pueden configurar para los
    temas.

5.  Establezca la descripción (**Description**) como - +++Processes
    incoming resumes and stores candidates in the system+++

![](./media/image15.png)

6.  Expanda **Advanced**, y establezca la prioridad (Priority) en 10000.
    Esto asegurará que, más adelante, el Interview Agent se utilice para
    responder preguntas generales antes que este. También se podría
    establecer una condición aquí, como asegurarse de que haya al menos
    un archivo adjunto.

![](./media/image16.png)

7.  Asegúrese de que el interruptor **Web Search** esté configurado
    como **Disabled**. Esto se debe a que solo queremos utilizar la
    información proporcionada por el agente principal. Seleccione
    **Save.**

![](./media/image17.png)

### Tarea 4: Configurar el flujo del agente para la carga de currículums

Los agentes no pueden realizar ninguna acción sin que se les
proporcionen herramientas o temas (topics).

Estamos utilizando **herramientas** de **Agent** **Flow** en lugar de
Topics para el paso de carga de currículums porque este proceso de fondo
(backend) de varios pasos requiere una ejecución determinista e
integración con sistemas externos. Mientras que los Topics son ideales
para guiar el diálogo conversacional, los Agent Flows proporcionan la
automatización estructurada necesaria para manejar de manera confiable
el procesamiento de archivos, la validación de datos y las
actualizaciones de la base de datos (upserts: insertar nuevo o
actualizar existente) sin depender de la interacción del usuario.

1.  Localice la sección **Tools** dentro de la página del Application
    Intake Agent. 

> **Importante:** Esta no es la pestaña Tools del agente principal, sino
> que se encuentra desplazándose hacia abajo, debajo de las
> instrucciones del agente hijo.

2.  Seleccione **+ Add**.

> ![](./media/image18.png)

3.  Seleccione **+ New tool**.

> ![](./media/image19.png)

4.  Seleccione **Agent flow**. Se abrirá el diseñador de Agent Flow;
    aquí es donde agregaremos la lógica para la carga del currículum.  
    ![](./media/image20.png)

5.  Seleccione el nodo **When an agent calls the flow**, y
    seleccione **+ Add an input**

> ![](./media/image21.png)

6.  Agregue **entradas** para cada uno de los parámetros enumerados en
    la tabla siguiente. Seleccione el tipo de entrada (input type)
    adecuado según se muestra en la tabla y asegúrese de agregar tanto
    el nombre como la descripción. Es fundamental incluir la
    descripción, ya que esto ayudará al agente a saber qué información
    debe completar en cada entrada.

[TABLE]

> ![](./media/image22.png)

7.  Seleccione el icono **+** debajo del nodo When an agent calls the
    flow y busque +++Dataverse add+++, después, seleccione la acción
    **Add a new row**  en la sección de **Microsoft Dataverse**.

> ![](./media/image23.png)
>
> ![](./media/image24.png)

**NOTA**

Es posible que se le pida crear una nueva conexión a Dataverse después
de añadir la acción. Introduzca cualquier nombre para la conexión y haga
clic en Add para crear dicha conexión.

8.  Cambie el nombre del nodo a +++**Create Resume** ; para ello,
    seleccione los 3 puntos (...) y seleccione **Rename**.  

> ![](./media/image25.png)

9.  Establezca el nombre de la tabla (**Table name**) como **Resumes**
    (Currículums); después, seleccione **Show all** para ver todos los
    parámetros.

> ![](./media/image26.png)

10. Establezca las siguientes **propiedades**:

[TABLE]

> ![](./media/image27.png)
>
> ![](./media/image28.png)
>
> ![](./media/image29.png)

11. Seleccione el icono **+** debajo del nodo **Create** **Resume**,
    busque +++Dataverse upload+++ y seleccione la acción **Upload a file
    or an image**.

![](./media/image30.png)

12. Cambie el nombre del nodo a +++**Upload Resume File**+++.

> ![](./media/image31.png)

13. Establezca las siguientes **propiedades**:

[TABLE]

> ![](./media/image32.png)

14. Seleccione el nodo **Respond to the agent node**, y, a continuación,
    seleccione **+ Add an output**. Cree una salida con las propiedades
    definidas en la tabla siguiente.

> ![](./media/image33.png)

[TABLE]

> ![](./media/image34.png)

15. Seleccione **Save draft** en la parte superior derecha.

> ![](./media/image35.png)

16. Seleccione la pestaña **Overview**, seleccione **Edit** en el panel
    de detalles (**Details**). Complete el nombre y la descripción como
    se muestra a continuación y seleccione **Save.**

    1.  **Flow name**:+++Resume Upload+++

    2.  **Description**:+++Uploads a Resume when instructed+++

> ![](./media/image36.png)

17. Seleccione la pestaña **Designer** nuevamente y
    seleccione **Publish**.

> ![](./media/image37.png)

### Tarea 5: Conectar el flujo a su agente

Ahora conectará el flujo publicado a su Application Intake Agent..

1.  Regrese al **Hiring Agent** y seleccione la pestaña **Agents**. Abra
    el **Application Intake Agent**, localice el panel **Tools** y
    seleccione **+Add**.  
    ![](./media/image38.png)

2.  Seleccione el filtro **Flow** y seleccione el flujo **Resume
    Upload**.

> ![](./media/image39.png)

3.  Seleccione **Add and configure**.

> ![](./media/image40.png)

4.  Establezca los siguientes parámetros para la **descripción** y el
    **momento en que debe utilizarse la herramienta**.

[TABLE]

> ![](./media/image41.png)
>
> **Nota:** Esta descripción le indica al agente cuándo debe invocar
> esta herramienta. Observe el uso de "strict rule" (regla estricta) en
> la descripción; esto permite establecer salvaguardas adicionales sobre
> el uso de la herramienta, en este caso, solo si hay archivos adjuntos
> y el contexto de la conversación es la carga de un currículum. Elegir
> cuándo se puede usar esta herramienta también es fundamental. Dado que
> estamos construyendo un sistema multi-agente con un agente hijo,
> queremos asegurarnos de que esta herramienta SOLO sea llamada por el
> agente hijo y no por el principal. Configurar el valor en "only when
> referenced by topics or agents" (solo cuando sea referenciado por
> temas o agentes) garantiza este comportamiento.

5.  Desplácese hacia abajo hasta la sección de entradas inputs y
    seleccione **Add Input** para agregar las siguientes:

[TABLE]

> ![](./media/image42.png)

6.  Ahora debemos configurar las propiedades de las entradas.
    Comenzaremos con la entrada **contentBytes**, que almacenará el
    archivo real del currículum. Seleccione **Custom value** en el menú
    desplegable **Fill using** junto a la entrada **contentBytes**. En
    la propiedad **Value**, seleccione los **tres puntos** (**...**).

> ![](./media/image43.png)

7.  Seleccione la pestaña **Formula**. Pegue la siguiente fórmula, la
    cual extrae el archivo del chat, y haga clic en el botón **Insert**.

+++First(System.Activity.Attachments).Content+++

> ![](./media/image44.png)

8.  Ahora configuraremos la entrada **name**, que almacenará el nombre
    del archivo del currículum. Esto también se definirá de forma fija,
    así que seleccione la opción **Custom value** en la columna **Fill
    using**.

9.  Seleccione los **tres puntos** (**...**) en la columna **Value** y
    pegue la siguiente fórmula, la cual extrae el nombre del archivo del
    chat, y haga clic en el botón **Insert**.

+++First(System.Activity.Attachments).Name+++

> ![](./media/image45.png)

10. Ahora configuraremos la entrada **Message**. Queremos que esta se
    complete dinámicamente con IA, por lo que dejaremos la opción **fill
    using** tal como está. Seleccione el botón **Customize** en la
    columna **Value** para que podamos completar detalles adicionales
    sobre cómo debe llenarse.

![](./media/image46.png)

11. Introduzca lo siguiente en el campo **Description** de la entrada.
    Después, seleccione **Advanced**.

**Extract a cover letter style message from the context. Be sure to
never prompt the user and create at least a minimal cover letter from
the available context. STRICT RULE - the message must be less than 2000
characters.**

**NOTA**

Completar la descripción de las entradas que se llenan dinámicamente es
un paso crucial para asegurar que el agente sepa cómo completar la
entrada correctamente.

> ![](./media/image47.png)

12. Despliegue la sección **Advanced** para configurar algunas
    propiedades adicionales para esta entrada. En la sección **How many
    reprompts**, seleccione **Don't repeat.**

> ![](./media/image48.png)

**NOTA**

Esta configuración le ayuda a personalizar la experiencia del usuario
para que el agente no haga la misma pregunta varias veces si no puede
identificar los datos que necesita.

13. Desplácese hacia abajo hasta la sección **No valid entity found**.
    Seleccione la opción **Set variable to value** en el menú
    desplegable **Action if no entity found**. Escriba **+++Resume
    upload+++** en el campo de entrada **Default entity value**.

> ![](./media/image49.png)
>
> **NOTA**
>
> Esta configuración nos permite definir un valor de respaldo fijo si el
> agente no puede completar dinámicamente esta entrada de mensaje.

14. Completaremos la entrada **UserEmail** seleccionando la opción
    **Custom value** en la columna **Fill using** y seleccionaremos los
    tres puntos (**...**) en la columna **Value**.

> ![](./media/image50.png)

15. Seleccione la pestaña **System** y busque **User**. Seleccione la
    variable **User.Email** para obtener el correo electrónico de la
    persona que está utilizando el agente.

> ![](./media/image51.png)

16. Seleccione **Save**

> ![](./media/image52.png)

### Tarea 6: Definir instrucciones del agente

En esta tarea, definirá las instrucciones del agente para el agente
Application Intake.

1.  Vuelva al agente **Application Intake** seleccionando la pestaña
    **Agents** y seleccionando **Application Intake Agent**.

> ![](./media/image53.png)

2.  En el campo **Instructions**, pegue la siguiente guía clara para su
    agente secundario.

> You are tasked with managing incoming Resumes, Candidate information,
> and creating Job Applications.
>
> Only use tools if the step exactly matches the defined process.
> Otherwise, indicate you cannot help.
>
> Process for Resume Upload via Chat
>
> 1. Upload Resume
>
> - Trigger only if /System.Activity.Attachments contains exactly one
> new resume.
>
> - If more than one file, instruct the user to upload one at a time and
> stop.
>
> - Call /Upload Resume once. Never upload more than once for the same
> message.
>
> 2. Post-Upload
>
> - Always output the \[ResumeNumber\] (R#####).
>
> ![](./media/image54.png)

3.  Cuando las instrucciones incluyan una barra diagonal (/), seleccione
    el texto que sigue después de la / y seleccione el nombre resuelto.
    Haga esto para,

    - System.Activity.Attachments (Variable)

    - Upload Resume (Tool)

> Nota: Si hace clic en System.Activity.Attachments en las
> instrucciones, obtendrá el nombre resuelto en la lista. Puede
> seleccionarlo. Después de seleccionarlo, si queda alguna parte del
> texto previamente existente, elimínela.
>
> ![](./media/image55.png)
>
> ![](./media/image56.png)

4.  Las instrucciones ahora deberían verse así.

> ![](./media/image57.png)

5.  Seleccione **Save.**

> ![](./media/image58.png)

### Tarea 7: Probar su agente Application Intake

Ahora verifique que su agente esté funcionando correctamente llamando a
su agente secundario y siguiendo sus instrucciones.

1.  **Active** el panel de prueba seleccionando **Test**.

> ![](./media/image59.png)

2.  Seleccione el icono Attachement, seleccione el curriculum – AVERY
    EXAMPLE pdf y haga clic en **Open**.

> ![](./media/image60.png)

3.  Escriba el mensaje +++Process these resumes+++ y presione
    **enviar**.

> ![](./media/image61.png)

4.  El agente debería mostrar un mensaje similar a **The resume for
    Avery Example has been successfully uploaded. The resume number is
    R1001.**

> ![](./media/image62.png)

5.  En el **mapa de actividad**, debería ver que el **agente Application
    Intake** está gestionando la carga del currículum.

> ![](./media/image63.png)

6.  Si la aplicación no está abierta, navegue a
    +++make.powerapps.com+++. Asegúrese de que el entorno Dev One esté
    seleccionado en el selector Environment en la esquina superior
    derecha. Seleccione **Apps** → Hiring Hub → menú de puntos
    suspensivos (...) → **Play**  
    ![](./media/image64.png)

**NOTA:** Si el botón Play aparece en gris, significa que no ha
publicado su solución. Seleccione **Solutions** → **Publish all
customizations**.

7.  En la aplicación Power Apps – Hiring Hub, navegue a **Resumes** y
    verifique que el archivo del currículum esté cargado y que la carta
    de presentación esté configurada correctamente.

> ![](./media/image65.png)

## Ejercicio 2: Agregar el agente conectado Interview Prep

Ahora cree su agente conectado para la preparación de entrevistas y
agréguelo a su Hiring Agent existente.

### Tarea 1: Crear el agente conectado Interview Agent

1.  Desde Copilot Studio, seleccione la pestaña **Agents** en la
    navegación izquierda y seleccione el **menú desplegable** junto a
    **+ Create blank agent**, y seleccione **Advanced create**.

> ![](./media/image66.png)

2.  Seleccione la **Solution** **(solución)** como **Operative** y
    seleccione **Confirm and create**.

> ![](./media/image67.png)

3.  Seleccione **Edit** en la sección Details.

> ![](./media/image68.png)

4.  Proporcione los siguientes detalles y seleccione **Save**.

    - **Name**: +++Interview Agent+++

    - **Description**: +++Assists with the interview process.+++

> ![](./media/image69.png)

5.  Seleccione **Edit** en la sección **Instructions**, ingrese la
    siguiente instrucción y seleccione **Save**.

> You are the Interview Agent. You help interviewers and hiring managers
> prepare for interviews. You never contact candidates.
>
> Use Knowledge to help with interview preparation.
>
> The only valid identifiers are:
>
> - ResumeNumber (ppa_resumenumber)→ format R#####
>
> - CandidateNumber (ppa_candidatenumber)→ format C#####
>
> - ApplicationNumber (ppa_applicationnumber)→ format A#####
>
> - JobRoleNumber (ppa_jobrolenumber)→ format J#####
>
> Examples you handle
>
> - Give me a summary of ...
>
> - Help me prepare to interview candidates for the Power Platform
> Developer role
>
> - Create interview assistance for the candidates for Power Platform
> Developer
>
> - Give targeted questions for Candidate Alex Johnson focusing on the
> criteria for the Job Application
>
> How to work:
>
> You are expected to ask clarification questions if required
> information for queries is not provided
>
> - If asked for interview help without providing a job role, ask for it
>
> - If asking for interview questions, ask for the candidate and job
> role if not provided.
>
> General behavior
>
> - Do not invent or guess facts
>
> - Be concise, professional, and evidence-based
>
> - Map strengths and risks to the highest-weight criteria
>
> - If data is missing (e.g., no resume), state what is missing and ask
> for clarification
>
> - Never address or message a candidate
>
> ![](./media/image70.png)

6.  Asegúrese de que **Web Search** este **Disabled.**

> ![](./media/image71.png)

### Tarea 2: Configurar el acceso a datos y publicar

En esta tarea, configurará el acceso a los datos y luego publicará el
agente.

1.  En la sección **Knowledge**, seleccione **+ Add knowledge.**

> ![](./media/image72.png)

2.  Seleccione **Dataverse**  
    ![](./media/image73.png)

3.  En el **cuadro de búsqueda**, escriba +++ppa\_+++. Este es el
    prefijo de las tablas que importó previamente en el laboratorio
    anterior.

4.  **Seleccione** las 5 tablas (Candidate, Evaluation Criteria, Job
    Application, Job Role, Resume). Seleccione **Add to agent**.

> ![](./media/image74.png)

5.  Seleccione el botón **Settings** en la esquina superior derecha.

> ![](./media/image75.png)

6.  Asegúrese de que las siguientes configuraciones estén establecidas:

    - **Let other agents connect to and use this one:** On

    - **Use general knowledge**: Off

    - **File uploads**: Off

    - **Content moderation level:** Medium

> ![](./media/image76.png)
>
> ![](./media/image77.png)
>
> ![](./media/image78.png)

7.  Seleccione **Save** y seleccione la **X** en la esquina superior
    derecha para cerrar el menú de configuración.

> ![](./media/image79.png)

8.  Seleccione **Publish**.

> ![](./media/image80.png)

9.  Seleccione **Publish** en el cuadro de diálogo de confirmación y
    espere a que se complete la publicación.

![](./media/image81.png)

### Tarea 3: Conectar el agente Interview Prep a su Hiring Agent

En esta tarea, conectará el agente Interview Prep a su Hiring Agent para
lograr una orquestación multiagente.

1.  Navegue de regreso a su **Hiring Agent**. Seleccione la pestaña
    **Agents** y seleccione **+ Add an agent.**

> ![](./media/image82.png)

2.  Seleccione el **Interview Agent**.

> ![](./media/image83.png)
>
> **NOTA**
>
> Si el Interview Agent aparece en gris y no se puede seleccionar,
> significa que no se publicó. Regrese al Interview Agent y publíquelo
> primero.

3.  Establezca la **Description** como,

> Assists with the interview process and provides information about
> Resumes, Candidates, Job Roles, and Evaluation Criteria.
>
> Observe que la opción Pass conversation history to this agent está
> seleccionada. Esto permite que el agente principal proporcione el
> contexto completo al agente conectado.
>
> Seleccione **Add and configure.**

![](./media/image84.png)

4.  Asegúrese de ver tanto el **Application Intake Agent** como el
    **Interview** **Agent**. Observe cómo uno es un agente secundario y
    el otro es un agente conectado.

> ![](./media/image85.png)
>
> ![](./media/image86.png)

### Tarea 4: Probar la colaboración multiagente

1.  **Active** el panel de prueba seleccionando **Test**.

2.  **Cargue** uno de los currículums de prueba e ingrese la siguiente
    descripción que indica al agente principal lo que puede delegar al
    agente conectado:

> Upload this resume, then show me open job roles, each with a
> description of the evaluation criteria, then use this to match the
> resume to at least one suitable job role even if not a perfect match.
>
> ![](./media/image87.png)

3.  Observe cómo el Hiring Agent delegó la carga al agente secundario y
    luego solicitó al Interview Agent que proporcionara un resumen y una
    coincidencia de puesto utilizando su conocimiento.

> ![](./media/image88.png)

4.  Experimente con diferentes formas de hacer preguntas sobre Resumes,
    Job Roles y Evaluation Criteria. **Ejemplos:**

> +++Give me a summary of active resumes+++
>
> +++Summarize resume R1006+++
>
> +++Which active resumes are suitable for the Power Platform Developer
> role?+++

## Resumen

Ha transformado con éxito su Hiring Agent único en uno sofisticado con
orquestación multiagente y capacidades especializadas.

Esto es lo que logró en este laboratorio.

**Dominio de la arquitectura multiagente**  
Ahora comprende cuándo utilizar agentes secundarios frente a agentes
conectados y cómo diseñar sistemas que escalen.

**Application Intake agent secundario**  
Ha agregado un agente secundario especializado a su Hiring Agent que
procesa currículums, extrae datos de candidatos y almacena la
información en Dataverse.

**Interview Prep agent conectado**  
Ha creado un agente conectado reutilizable para la preparación de
entrevistas y lo ha conectado correctamente a su Hiring Agent.

**Comunicación entre agentes**  
Ha visto cómo su agente principal puede coordinarse con agentes
especializados, compartir contexto y orquestar flujos de trabajo
complejos.

**Base para la autonomía**  
Su sistema de contratación mejorado ahora está listo para las funciones
avanzadas que agregaremos en las próximas misiones: desencadenadores
autónomos, moderación de contenido y razonamiento profundo.
