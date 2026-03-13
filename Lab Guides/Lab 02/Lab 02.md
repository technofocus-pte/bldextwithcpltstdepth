# Laboratorio 2- Construir y mejorar un asistente empresarial basado en plantillas

**Objetivo**

Las **plantillas de agentes** están diseñadas para ayudarle a comenzar
con un **agente personalizado.** Usted es responsable de evaluar todas
las implicaciones legales y de seguridad al usar una plantilla de agente
y personalizarla según sea apropiado para su negocio.

Un **agente creado a partir de la plantilla Safe Travels** es un agente
de empresa a empleado (B2E) diseñado para brindar **asistencia de
viaje** a los colaboradores de una compañía. Este agente ayuda a
garantizar que los empleados estén bien preparados e informados para su
próximo viaje de trabajo. Utiliza procesamiento de lenguaje natural para
ofrecer una interfaz conversacional, lo que facilita e intuitivo el
acceso a la información necesaria. Sin embargo, el sitio web
predeterminado utilizado por el agente actualmente solo cubre destinos
de viaje en EE. UU. Usted puede reemplazar el sitio web predeterminado
con su propia fuente de conocimientos.

En este laboratorio, creará un agente a partir de la **plantilla Safe
Travels** y lo mejorará en el laboratorio 05.

## Ejercicio 0 - Crear un Grupo de Seguridad en Entra ID y configurar los autores de Copilot Studio

Esta es una tarea de prerrequisito para ayudarnos a publicar y trabajar
de manera fluida con los agentes en Copilot Studio a lo largo de este
curso.

1.  Navegue al portal de Azure en +++<https://portal.azure.com/+++> e
    inicie sesión con las credenciales de su tenant que se encuentran en
    la pestaña **Resources**.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  Seleccione **Next** en la ventana "Keep your account secure"
    (Mantenga su cuenta segura) y siga las **instrucciones**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Descargue la aplicación Authenticator en su teléfono si aún no la
    tiene instalada.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  Siga las instrucciones y complete la configuración.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  En la pantalla de bienvenida de Azure, seleccione **Get Started**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  Busque y seleccione +++Microsoft EntraID+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  En el panel izquierdo, seleccione **Manage** -\> **Groups**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  Seleccione **New group** para crear un nuevo grupo de seguridad.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  Ingrese los siguientes detalles:

    - Group type – Seleccione **Security**

    - Group name Enter – +++**copilotagentsecurity**+++

    - Microsoft Entra roles can be assigned to the group –
      Seleccione **Yes** (Si esta opción no está visible, ignore este
      paso)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. Seleccione **No owners selected**, elija el **MOD Administrator** en
    la página **Add owners** y haga clic en **Select**.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. De manera similar, seleccione **No members selected**, y agregue
    al **MOD Administrator** de la lista y haga clic en **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. Seleccione **No roles selected**. Si **no ve** esta **opción**,
    ignore este paso y el siguiente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. Busque y seleccione +++**Global admin**+++ y seleccione **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. Seleccione **Create** una vez que se hayan agregado todos los
    detalles y elija **Yes** en el cuadro de diálogo de confirmación.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. Asegúrese de recibir un mensaje de **éxito**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. Seleccione Contoso|Groups en la parte superior izquierda.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. Seleccione **Properties** bajo la sección **Manage** en el panel
    izquierdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. Cambie a **Yes** en la opción “**can manage access to all Azure
    subscriptions and management groups in this tenant**”  y luego haga
    clic en **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. Ahora, seleccione **Roles and administrators** bajo la
    sección **Manage** en el panel izquierdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. Busque +++privileged role admin+++ y haga clic en el nombre del
    rol **Privileged Role Administrator** (**no seleccione la casilla de
    verificación**, haga clic directamente sobre el nombre).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

21. Seleccione **+ Add assignments**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

22. Seleccione **No members selected**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

23. Seleccione el **ID de** **MOD Admin** y haga clic en **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

24. Seleccione **Assign**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

25. Asegúrese de que la asignación del rol se haya realizado
    correctamente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

26. Desde una nueva pestaña, navegue a
    +++<https://admin.powerplatform.microsoft.com/+++>. Seleccione
    **Manage** en el panel izquierdo y luego seleccione la opción
    **Tenant Settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

27. Seleccione **Copilot Studio Authors** de la lista disponible.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

28. Haga clic en el icono **Edit** para modificar la configuración.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

29. Busque y seleccione el grupo **+++copilotagentsecurity+++** que creó
    anteriormente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

30. Seleccione **Save** para salvar la configuración.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

## Ejercicio 1: Crear el agente "Safe Travels" a partir de una plantilla

En este ejercicio, creará el agente en Copilot Studio utilizando la
plantilla de agente de "Safe Travels".

1.  Desde un navegador, inicie sesión en
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/).
    Se abrirá la página "Start free trial". Seleccione su país y haga
    clic en **Start free trial**.

![](./media/image39.png)

2.  Seleccione el entorno **Dev One**.

> ![](./media/image40.png)
>
> \[!Alerta\] **Importante**: Si Copilot Studio no muestra la opción
> para seleccionar el **Environment** como se ve en la siguiente captura
> de pantalla, siga los pasos que se indican a continuación.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image41.png)
>
> Abra +++<https://admin.powerplatform.microsoft.com/+++>.
> Seleccione **Manage** -\> **Environments -\> Dev One** y seleccione el
> valor de **Environment ID**. ![A screenshot of a computer AI-generated
> content may be incorrect.](./media/image42.png)
>
> Regrese a la pestaña de Copilot Studio y abra
> +++<https://copilotstudio.microsoft.com/environments/>**\<
> EnvironmentID \>**+++ (Reemplazando **\< EnvironmentID \>** con el
> valor obtenido anteriormente)

3.  Seleccione **Skip** en la pantalla de bienvenida.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

4.  Seleccione **Agents** en el panel izquierdo y luego elija la
    plantilla **Safe Travels** bajo la sección **Start with an agent
    template**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

5.  La plantilla Safe Travels crea un nuevo agente diseñado para brindar
    asistencia de viaje a los empleados de una empresa. 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

6.  Explore la página de configuración. En la sección **Knowledge**,
    podrá observar que el sitio web **US Travel Website** ya ha sido
    agregado como fuente de conocimiento. Es posible editarlo si es
    necesario; en este caso, utilizaremos el mismo sitio web.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

7.  Seleccione **Create** para generar el agente "Safe Travels". No
    realizaremos cambios en este punto y utilizaremos la plantilla tal
    como está. En cualquier momento, el agente puede ser actualizado
    según los requisitos del usuario.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

8.  El **agente** se **crea** y se abre automáticamente, mostrando la
    página de **Overview**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

9.  En el panel de prueba, escriba +++How to apply for passport?+++ y
    presione **Send**.

El panel de prueba se abre de forma predeterminada. Si no es así, haga
clic en el icono Test en la parte superior derecha.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

10. Podrá observar que el agente proporciona información sobre cómo
    solicitar el pasaporte basándose en su fuente de conocimiento.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image50.png)

## Ejercicio 2: Publicar el agente en Teams y Microsoft 365 Copilot

In this exercise, you will **publish** the agent created in Copilot
Studio to the **Microsoft Teams** and **Microsoft 365 Copilot** channel.
En este ejercicio, **publicará** el agente creado en Copilot Studio en
los canales de **Microsoft Teams** y **Microsoft 365 Copilot**.

1.  Abra **MS Teams** +++<https://teams.microsoft.com/v2/+++> desde un
    navegador e **inicie sesión** utilizando las credenciales de su
    tenant desde la pestaña **Resources**.

2.  De regreso en Copilot Studio, seleccione **Publish** en la parte
    superior derecha de la página del agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

3.  Marque la casilla **Force newest version** y luego seleccione
    **Publish** en el cuadro de diálogo de confirmación.

![](./media/image52.png)

![](./media/image53.png)

4.  Seleccione **Channels** en la barra de navegación superior.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

5.  Seleccione **Teams and Microsoft 365 Copilot** de la lista de
    canales disponibles.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

6.  Seleccione **Add channel**.

![](./media/image56.png)

7.  Haga clic en la opción **See agent in Teams** para añadir el agente
    a Teams.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

8.  Esto abrirá el agente en Microsoft Teams. Seleccione **Cancel** en
    la ventana emergente **This site is trying to open Microsoft
    Teams** y luego elija la opción **Use the Web App instead**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  Seleccione **Add** para añadir el agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

10. Una vez agregado, verá una opción para abrir el agente. Seleccione
    **Open**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image61.png)

11. Pruebe el agente desde Teams.

![](./media/image62.png)

12. De regreso en Copilot Studio, cierre la ventana del canal de Teams
    and Microsoft 365 Copilot.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

## Ejercicio 3: Probar el agente "Safe Travels" existente

En este ejercicio, probaremos el agente "**Safe Travels**" para observar
cómo responde cuando se le pregunta sobre la aprobación de viajes.

1.  De regreso en Copilot Studio -\> agente Safe Travels, seleccione el
    icono **Test** para probar el agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

2.  Escriba +++Need travel approval+++ en la ventana de prueba (test
    window) y presione **Enter**.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image65.png)

3.  Podrá observar que el agente responde con un conjunto de
    instrucciones generales que deben seguirse para obtener la
    aprobación del viaje.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image66.png)

## Ejercicio 4: Mejorar el agente con activos de conocimiento específicos de la empresa

En este ejercicio, agregaremos un activo de conocimiento - **Travel
Policy** específica de Contoso.

1.  Desde la página de Overview del agente, desplácese hacia abajo y
    seleccione **+ Add knowledge.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

2.  Haga clic en la opción **select to browse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

3.  Desde la carpeta **C:\Labfiles\Lab Files**, seleccione **Travel
    Policy.docx** y haga clic en **Open**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

4.  Haga clic en **Add to agent** para añadir el archivo.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image70.png)

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image71.png)

5.  Asegúrese de que el archivo se haya agregado correctamente. Espere
    hasta que el estado cambie de **In progress** to **Ready**. Puede
    continuar con el siguiente paso si el cambio al estado "Ready"
    demora más de unos minutos.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image73.png)

6.  Ahora, pruebe el agente con la misma pregunta para observar que este
    responde con las políticas específicas de la empresa, provenientes
    del activo de conocimiento que acaba de agregar.

## Resumen

En este laboratorio, ha creado un agente de **asistencia de viajes de
negocio a empleado (B2E)** utilizando la **plantilla de agente "Safe
Travels"** en Microsoft Copilot Studio. Exploró cómo las plantillas de
agentes proporcionan un punto de partida rápido al preconfigurar
capacidades conversacionales y fuentes de conocimiento, permitiendo al
mismo tiempo personalizaciones futuras para cumplir con los requisitos
organizacionales y legales. Utilizando el **sitio web de viajes de EE.
UU.** integrado como **fuente de conocimiento**, probó la capacidad del
agente para responder preguntas de los empleados relacionadas con viajes
mediante interacciones en lenguaje natural. Finalmente, publicó el
agente en **Microsoft Teams y Microsoft 365 Copilot**, validó su
disponibilidad en Teams y confirmó que los empleados pueden acceder e
interactuar con el agente "Safe Travels" directamente dentro de sus
herramientas de colaboración cotidianas.

 
