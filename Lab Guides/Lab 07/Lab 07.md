# Laboratorio 7: Creación de un agente autónomo de recuperación de datos financieros con agentes que usan computadoras (CUA)

**Introducción**

Los sistemas legados sin API crean obstáculos importantes para la
automatización. El RPA tradicional a menudo depende de técnicas frágiles
de captura de pantalla (screen-scraping) o soluciones manuales
temporales, lo que ralentiza la toma de decisiones, aumenta los errores
y reduce la productividad. Este laboratorio presenta Microsoft Copilot
Studio y los Computer Using Agents (CUA) como una solución más
inteligente. Al simular la interacción humana con los sistemas internos,
los CUA pueden acceder y procesar datos de forma segura, sin necesidad
de integración mediante API. Aprenderá a crear un agente autónomo que
ofrezca respuestas más rápidas, reduzca la carga de trabajo manual y
permita tomar decisiones informadas en tiempo real.

Objetivo

En este laboratorio, aprenderá a crear un agente autónomo utilizando
Microsoft Copilot Studio. Este agente simulará la interacción humana con
un sistema interno legado para recuperar datos de carteras financieras
sin requerir acceso directo a una API.

## Tarea 1: Crear y configurar un agente autónomo

En esta tarea, creará un nuevo agente autónomo en Microsoft Copilot
Studio, configurará su identidad y establecerá un desencadenador de
correo electrónico utilizando el conector de Microsoft 365 Outlook.

Para automatizar las consultas de carteras, el agente debe ser capaz de
detectar solicitudes de correo electrónico entrantes e iniciar el flujo
de automatización adecuado basado en el filtrado por línea de asunto.

1.  Inicie sesión en Copilot Studio en
    +++https://copilotstudio.microsoft.com+++ utilizando sus
    credenciales de acceso.

2.  Seleccione el entorno Dev One en la parte superior derecha.

![](./media/image1.png)

3.  Seleccione **Create an agent**.

![](./media/image2.png)

4.  Una vez creado el agente, seleccione **Edit** junto a **Details**.

![](./media/image3.png)

5.  Ingrese el Name (nombre) como +++Portfolio Lookup Agent+++ y
    seleccione Save para cambiar el nombre predeterminado del agente.

![](./media/image4.png)

6.  Desplácese hacia abajo hasta la sección **triggers**
    (desencadenadores) y haga clic en **+Add trigger**.

![](./media/image5.png)

7.  Busque y seleccione **When a new email arrives (V3) (Office 365
    Outlook)** y haga clic en **Next**.

![](./media/image6.png)

8.  Cambie el nombre del desencadenador a +++When a portfolio lookup
    email arrives+++, asegúrese de que la conexión esté establecida para
    Copilot Studio y Outlook, y luego haga clic en Next.

![](./media/image7.png)

9.  En el campo **Subject Filter (Optional)**, ingrese +++Portfolio+++
    en la línea de asunto.

![](./media/image8.png)

10. Una vez que se haya creado el desencadenador, puede cerrar
    (**Close**) el cuadro de diálogo **Time to test your trigger**.

![](./media/image9.png)

## Tarea 2: Agregar la herramienta de uso de computadora

En esta tarea, configurará una herramienta de uso de computadora que
inicia sesión en una computadora, navega a través de un sitio web, busca
y recupera datos de una cartera financiera. Luego, utilizará el conector
de Office 365 Outlook para responder con los datos solicitados.

1.  Navegue a **Tools** en el menú de nivel superior.

![](./media/image10.png)

2.  Seleccione **+ Add a tool.**

![](./media/image11.png)

3.  Seleccione **+ New tool**.

![](./media/image12.png)

4.  Seleccione **Computer use (preview)**.

![](./media/image13.png)

5.  Agregue las siguientes instrucciones y luego seleccione **Add and
    configure**.

&nbsp;

1.  Vaya a
    <https://computerusedemos.blob.core.windows.net/web/Portfolio/index.html>.

2.  Ingrese el Portfolio ID en el campo de búsqueda "Enter Portfolio ID"
    y haga clic en el botón "Search".

3.  Recupere los valores de "Client Name", "Portfolio Value" y "Manager"
    exactamente como se muestran.

4.  Devuelva esos tres valores como el resultado final. Si no se
    encuentran datos de la cartera, responda que no se pudo encontrar
    una cartera con el ID especificado.

![](./media/image14.png)

6.  Actualice el **Name** (Nombre) de la herramienta de uso de
    computadora como +++Look up portfolio data+++

7.  Actualice la **Description** (Descripción) como +++Search and
    retrieve financial portfolio data+++

![](./media/image15.png)

8.  En la sección Inputs seleccione **+ Add input**.

![](./media/image16.png)

9.  Ingrese el nombre como +++Portfolio ID+++ y la descripción como
    +++The ID of the portfolio+++ y seleccione **Done**.

![](./media/image17.png)

10. Seleccione **Save**.

![](./media/image18.png)

## Tarea 3: Probar la herramienta de uso de computadora (Computer Use)

1.  En la sección **Instructions**, seleccione el botón **Test** ubicado
    a la derecha.

![](./media/image19.png)

2.  Agregue el valor de ejemplo +++44123BCD+++ y seleccione **Test
    now**.

![](./media/image20.png)

3.  Observe cómo la herramienta de uso de computadora (Computer use)
    inicia sesión en el equipo y realiza las acciones solicitadas:

    - El panel izquierdo muestra sus instrucciones y un registro paso a
      paso del razonamiento y las acciones de la herramienta.

    - El panel derecho muestra una vista previa de las acciones en la
      máquina que configuró para el uso de computadora.

![](./media/image21.png)

> ![](./media/image22.png)

![](./media/image23.png)

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

4.  Seleccione **Finish testing**.

![](./media/image27.png)

## Tarea 4: Configuración de las capacidades de respuesta por correo electrónico

En esta tarea, configurará la capacidad de envío de correos
electrónicos.

1.  Regrese a la pestaña **Tools** y seleccione **+ Add a tool**.

![](./media/image28.png)

2.  Busque +++**Send an email (V2) (Office 365 Outlook)**+++ y
    selecciónelo.

![](./media/image29.png)

3.  Seleccione **Add and configure**.

![](./media/image30.png)

4.  Actualice su **Name** a +++Reply to email+++ y su **Description** a
    +++Use this operation to reply to the email received+++, y luego
    seleccione **Additional details**.

![](./media/image31.png)

5.  En **Additional details**, establezca **Credentials to use** como
    **Maker-provided credentials.**

![](./media/image32.png)

6.  En la sección **Inputs**, haga clic en **customize** junto a la
    entrada **To** y establezca su **Description** como+++Use the "from"
    email of the triggering received email+++.

![](./media/image33.png)

![](./media/image34.png)

7.  **Personalice** la entrada **Subject** y establezca su
    **Description** como +++Write the email subject+++.

![](./media/image35.png)

8.  Personalice la entrada **Body** y establezca su **Description**
    como+++Write the email body using HTML and highlight the requested
    data+++.

![](./media/image36.png)

9.  Haga clic en **Save** para finalizar la configuración de la
    herramienta.

![](./media/image37.png)

10. Navegue a la pestaña **Overview** y luego seleccione **Edit** en la
    sección **Instructions**.

![](./media/image38.png)

11. Pegue la siguiente instrucción.

When a financial portfolio related request is received, identify the
Portfolio ID and search for the requested data using \< Look up
portfolio data \>. Once you have gathered the financial portfolio
information, use the \< Reply to email \> tool to reply to the original
email you received. Do not respond with data beyond what was requested.

![](./media/image39.png)

12. Seleccione \< Look up portfolio data \>, ingrese un / y seleccione
    la herramienta Look up portfolio data.

![](./media/image40.png)

![](./media/image41.png)

13. Del mismo modo, reemplace \< Reply to email \> con la herramienta,
    **Reply to email**.

14. Una vez realizadas las sustituciones, como se muestra en la captura
    de pantalla de abajo, seleccione **Save**.

![](./media/image42.png)

15. Seleccione **Settings** en la parte superior derecha.

![](./media/image43.png)

16. **Desactive la opción** **Use general knowledge** en la sección
    **Knowledge** y seleccione **Save**.

![](./media/image44.png)

17. Cierre el panel de **Settings**.

![](./media/image45.png)

## Tarea 5: Probar el agente completo

En esta tarea, probará el funcionamiento integral del agente que ha
creado.

1.  Envíe un correo electrónico de prueba desde una dirección de su
    preferencia a la cuenta de correo electrónico de su usuario de
    capacitación con:

Asunto: +++Portfolio data request+++

Cuerpo:

Hi!

I hope you're doing well!

I'm looking for the portfolio manager and value of portfolio \#44123BCD.
Much appreciated.

Thanks!

![](./media/image46.png)

2.  Asegúrese de recibir el correo electrónico en la bandeja de entrada
    de su usuario de capacitación.

3.  En la pestaña **Overview**, vaya a la sección **Triggers**
    (Desencadenadores) y seleccione **Test trigger**.

![](./media/image47.png)

4.  Seleccione la **instancia del desencadenador** y luego **Start
    testing.**

![](./media/image48.png)

5.  Se lleva a cabo la ejecución y podrá ver las actualizaciones y el
    flujo en el panel Test.

![](./media/image49.png)

![](./media/image50.png)

6.  Una vez completada la ejecución, revise su correo electrónico para
    ver la respuesta del agente.

![](./media/image51.png)

## Resumen

En este laboratorio, usted construyó un agente autónomo de recuperación
de datos financieros utilizando Microsoft Copilot Studio y agentes que
usan computadoras (CUA). Configuró un agente basado en eventos que
responde automáticamente a solicitudes por correo electrónico, simula la
interacción humana con un sistema legado para recuperar datos de
carteras y devuelve resultados precisos sin depender de APIs.

Usted aprendió a:

- Diseñar un agente autónomo que opera sin interacción directa del
  usuario

- Utilizar desencadenadores (triggers) basados en el correo electrónico
  para iniciar flujos de trabajo automatizados.

- Configurar Agentes que Usan Computadoras para navegar de forma segura
  y extraer datos de aplicaciones web legadas

- Integrar herramientas de acción para devolver resultados a través de
  correo electrónico.

- Reducir la dependencia de patrones de RPA frágiles mediante el uso de
  interacción con computadoras impulsada por IA

Este laboratorio demuestra cómo los agentes autónomos con CUA pueden
modernizar el acceso a sistemas legados, optimizar los flujos de trabajo
operativos y permitir una toma de decisiones más rápida y confiable en
entornos donde no hay APIs disponibles.
