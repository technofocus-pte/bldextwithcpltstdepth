# Laboratorio 04 – Integración de un agente con la aplicación Dynamics 365 Customer Service e implementación del escalado automático de casos al agente en vivo

## Objetivo

Este laboratorio detalla los pasos para escalar una conversación a un
agente en vivo desde los agentes.

\[!Alerta\] **Importante:** Este laboratorio sólo puede ejecutarse si se
ha habilitado la prueba de Dynamics 365 según el **Laboratorio 02 -
Configuración de Dynamics 365 Customer Service.**

## Ejercicio 1: Configurar el workspace de Dynamics 365 Customer Service

### Tarea1: Configurar la extensión Omnichannel Power Virtual Agent 

1.  Abra el enlace,
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++> y
    haga clic en **Get it now** en la página Omnichannel Power Virtual
    Agent Extension.

![](./media/image1.png)

2.  Inicie sesión con las credenciales del tenant desde la
    pestaña **Resources**.

![](./media/image2.png)

3.  Haga clic en **Get it now**.

![](./media/image3.png)

4.  Seleccione **CustomerService Trial** en **Select an environment**,
    marque las casillas correspondientes y haga clic en **Install**.

![](./media/image4.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

## Tarea 2: Configurar los ajustes de búsqueda en el centro de administración de Power Platform

1.  Inicie sesión en
    +++<https://admin.powerplatform.microsoft.com/+++> con los datos de
    su tenant. Seleccione **Manage** en el panel izquierdo y, a
    continuación, seleccione **CustomerService Trial** en la lista de
    entornos.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  Seleccione **Settings** en el panel superior.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  Seleccione **Product** -\> **Features**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  Activa **Dataverse Search** a **On** y haz clic en **Save**. Luego, activa la opción **Single table search** a **On** y selecciona **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/im14.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/im15.png)

## Ejercicio 2: Crear un agente

1.  Desde la página de inicio de Copilot Studio,
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/),
    seleccione el entorno **CustomerService Trial** en la parte superior
    derecha.

![](./media/image10.png)

2.  Seleccione **Agents** en el panel izquierdo. Haga clic en **+ New
    Agent** para crear un nuevo agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  En el área de texto Type your message, escriba +++**You are a
    customer service agent who helps in identifying stores nearby.**+++
    y presione **send**.

![](./media/image12.png)

4.  El agente puede sugerir un nombre para el agente que se está
    creando. Aceptarlo o sugerir uno nuevo..

5.  Escriba el mensaje +++**Maintain a polite tone**+++ a continuación y
    presione **send**.

![](./media/image13.png)

6.  Haga clic en **Create**.

![](./media/image14.png)

7.  El agente creado se abre con un mensaje, **Your agent is ready**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## Ejercicio 3: Conectar Copilot a Dynamics 365 Customer Service y configurar el tema Escalate

### Tarea 1: Configurar el tema Escalate

Nos centramos aquí en mostrar el concepto de escalado a agente en vivo.
Por lo tanto, trabajaremos directamente en ello sin crear ningún otro
tema nuevo.

1.  Seleccione la pestaña **Topics** y, a continuación, seleccione la
    pestaña **System**. Seleccione el tema **Escalate**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  Seleccione el nodo de mensaje del tema y sustituya el contenido
    existente con, +++You will be transferred to a live agent shortly+++

![](./media/image17.png)

3.  Haga clic en el símbolo + para añadir un nodo junto al nodo Message.

4.  Seleccione **Topic management** -\> **Transfer conversation**.

![](./media/image18.png)

5.  Escriba el mensaje +++The customer wants to talk to a live agent+++
    en el nodo Transfer conversation.

![ ](./media/image19.png)

6.  **Guarde** el tema hacienda clic en Save.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  **Publique** el agente hacienda clic en Publish.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### Tarea 2: Conectar Copilot a Dynamics 365 Customer Service

1.  Una vez publicado, en la parte superior derecha de la página
    Copilot, haga clic en **Settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  Seleccione **Security**, y **Authentication** en Security.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  Seleccione la opción **No authentication** y luego haga clic
    en **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  Seleccione **Save **en el cuadro de diálogo de confirmación.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  Cierre el panel **Settings**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image26.png)

6.  Haga clic en **Channels** (si los canales no están visibles, haga
    clic en el signo +1 para ver la opción **Channels**)

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  Seleccione **Dynamics 365 Customer Service** en el panel Customer
    engagement hub.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  En la página Dynamics 365 Customer Service, haga clic
    en **Connect**.

![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  Una vez que reciba el mensaje **successfully connected**, haga clic
    en **Close**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## Ejercicio 4: Crear flujo de trabajo y canal en el centro de administración de Dynamics 365 

### Tarea 1: Gestionar un usuario en Omnichannel para Customer Service 

1.  Inicie sesión en
    +++[https://admin.powerplatform.microsoft.com+++](https://admin.powerplatform.microsoft.com+++/) con
    sus credenciales de administrador de tenants. Seleccione **Manage**
    en el panel izquierdo. Seleccione el entorno **CustomerService
    Trial** en **Environments**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  Haga clic en el **valor de la URL** debajo de **Environment URL**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  Seleccione **Customer Service workspace** en la barra de encabezado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  Se abrirá la página **Apps**. Seleccione **Customer Service admin
    center**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  Esto abre la página **Dynamics 365 Customer Service admin center**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

### Tarea 2: Configurar flujo de trabajo

1.  En la página del centro de administración,
    seleccione **Workstreams** en **Customer support** en el panel
    izquierdo y, a continuación, seleccione la opción **+ New
    workstream**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

2.  Seleccione Inbound

![](./media/image37.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

3.  Complete los siguientes datos, desplácese hacia abajo y haga clic en
    **Create**.

    - Name - +++**New Workstream**+++

    - Owner – **MOD Administrator** (Seleccionado por defecto)

    - Type – **Messaging**

    - Channel – **Chat**

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image39.png)

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  Una vez creado el flujo de trabajo, haga clic en **Set up
    chat **para configurar el canal de chat.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  En la pantalla **Live chat setup – Channel details**, complete los
    siguientes datos.

    - Name - +++**Chat Channel**+++

    - Language – **English - United States**

![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  Desplácese hacia abajo y haga clic en **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  Acepte los valores predeterminados en las dos páginas siguientes
    hasta llegar a la pantalla del widget de chat. En la pantalla Live
    chat setup – Chat widget, ingrese el nombre +++**Store Locator
    Assistant**+++, acepte los demás valores predeterminados y haga clic
    en **Next**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  En la pantalla **Live chat setup – Behaviors**, acepte los valores
    predeterminados y haga clic en **Next**.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  En la pantalla **Live chat setup – User features**, desactive las
    opciones **File attachment** y **Voice and video calls** y haga clic
    en **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. Acepte el valor predeterminado en la pantalla Notification y haga
    clic en **Next**.

11. En la pantalla **Live chat setup – Review and finish**,
    seleccione **Create channel**.

![](./media/image47.png)

12. **Copie** el valor del widget que aparece en la pantalla **Live chat
    setup – Success** y **guárdelo** en un bloc de notas para añadirlo a
    una página web en los próximos ejercicios. A continuación, haga clic
    en **Done** para completar la configuración.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### Tarea 3: Agregue el agente al flujo de trabajo

1.  De vuelta en la página **New Workstream**, desplácese hacia abajo y
    haga clic en **+ Add bot** en la sección Bot.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  En la lista de copilotos de la pantalla Add bot, seleccione el
    agente **Store Locator Assistant** y haga clic en **Connect**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  Asegúrese de que el bot se ha añadido al flujo de trabajo tal y como
    se muestra en la siguiente captura de pantalla.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  En el panel izquierdo, seleccione **AI Agents**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  Asegúrese de que el agente **Store locator** está conectado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## Ejercicio 5: Crear una página web y probar el escalado al agente

1.  Inicie sesión en +++<https://make.powerpages.microsoft.com/+++> con
    sus credenciales de administrador de tenants.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  Asegúrese de que se encuentra en el entorno **CustomerService
    Trial**.

3.  Haga clic en **Get started**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  Haga clic en Skip en la página **Tell us about yourself**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  Desplácese hacia abajo en la página siguiente y haga clic en la
    opción **Start with a template **para empezar a crear el sitio con
    una plantilla.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  Seleccione una plantilla y haga clic en **Choose this template**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  En el cuadro de texto Give your site a name textbox, ingrese el
    nombre como +++**Contoso Store assistant**+++, acepte los demás
    valores predeterminados y haga clic en **Done**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  Una vez creado el sitio, haga clic en **Edit**.

> ![](./media/image60.png)

9.  Haga clic en **Edit site header** en el título **Company name**.

![](./media/image61.png)

10. En el panel **Edit site header**, ingrese el **Site title** como
    +++**Contoso Store assistant**+++ y cierre el cuadro de diálogo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. Haga clic en **Edit code** en la esquina superior derecha de la
    página.

![](./media/image63.png)

12. Haga clic en **Open Visual Studio Code**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

13. Haga clic en **Allow**. **Inicie sesión **con sus credenciales de
    tenant si es necesario.

![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

14. Se abre la página de inicio de la página web en Visual Studio Code.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

15. Desplácese hasta el final del archivo. Añada el **script** copiado
    al crear el flujo de trabajo, después de la última línea de este
    archivo.

![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

16. Guarde el archivo, cierre la pestaña Visual Studio Code y vuelva a
    Power Pages. Haga clic en **Sync**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. Una vez completada la sincronización,
    seleccione **Preview** -\> **Desktop.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

18. Su página web se abrirá en una nueva pestaña. Busque **Store Locator
    Assistant** integrado en la página, en la parte inferior
    derecha. **Haga clic** en él.

![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

19. Ingrese +++Talk to agent+++.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

20. Desde la página de administración de Customer Service, haga clic
    en **Customer Service admin center** y seleccione la
    aplicación **Customer Service workspace**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

21. En la página del workspace de Customer Service, recibirá
    una **solicitud de chat**. **Acéptela**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

22. Una vez aceptada, se abre la pantalla de chat con el mensaje que
    habíamos indicado en el tema Escalate. Aquí también podemos añadir
    cualquier otra información proporcionada por el usuario al agente en
    vivo.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

23. Simule el chat entre el agente en vivo y el cliente si desea ver
    cómo funciona y cómo termina.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image77.png)

## Resumen

En este laboratorio, hemos aprendido a

- Crear un agente desde Copilot Studio y configurar el tema Escalate.

- Publicar el agente en el workspace de Dynamics 365 e integrarlo en una
  página web. 

