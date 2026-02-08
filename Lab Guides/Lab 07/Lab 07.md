# Laboratorio 07 – Creación de un asistente de compras personalizado

## Objetivo

El objetivo de este laboratorio es crear un agente de compras
personalizado para Contoso Electronics. Este utilizará tablas de
Dataverse como fuente de información. Sugerirá categorías de productos
al cliente según sus últimas compras y lo asistirá durante toda la
experiencia de compra.

## Ejercicio 1: Crear tablas de Dataverse

En este ejercicio, creará tablas en Dataverse para almacenar los
detalles del **Customer**, **Product** y los detalles del **Order**.

1.  Inicie sesión en +++https://make.powerapps.com+++ utilizando las
    credenciales administrativas del tenant y seleccione Dev One como
    entorno. Haga clic en **Tables** en el panel de navegación de la
    derecha.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  Seleccione el menú desplegable junto a **+ New table** y luego,
    elija la opción **Create new tables** que se encuentra debajo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  Seleccione **Import an Excel file or .csv** para crear una nueva
    tabla.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  En **Import an Excel or .CSV file**, seleccione la opción **Select
    from device**.

![A screenshot of a file AI-generated content may be
incorrect.](./media/image4.png)

5.  En **C:\Labfiles**, seleccione el archivo de Excel –
    **Customers.xlsx**. Haga clic en **Import** para importar los datos
    del rastreador y crear la tabla.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  La tabla se crea con los datos del rastreador.

7.  Aquí, el nombre de la tabla es **Customer Record**. El nombre podría
    ser ligeramente diferente en su caso, ya que se genera
    automáticamente. Anótelo y use el nombre de tabla adecuado durante
    la ejecución del laboratorio.

8.  Haga clic en la tabla y luego seleccione **View data** para ver los
    datos agregados a la tabla.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  Seleccione **Save and exit**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

10. Haga clic en **Save and exit** en el cuadro de diálogo de
    confirmación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. Repita los pasos del 2 al 10 dos veces para crear tablas, una vez
    utilizando el tracker **Product Catalog.xlsx** y la segunda
    utilizando **Orders.xls.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

12. Ahora tendremos 3 tablas,

    - Registro del cliente

    - Registro del producto

    - Pedidos

## Ejercicio 2 – Crear un agente de compras

En este ejercicio, creará un agente de compras que ayudará a los
clientes mientras compran en Contoso Electronics.

### Tarea 1: Cree el agente

El agente debe ser creado en Copilot Studio utilizando Copilot. A través
del chat con Copilot, se le deben proporcionar instrucciones sobre el
diseño y el comportamiento esperado, para que el agente sea generado
automáticamente.

1.  Inicie sesión en Copilot Studio en
    +++https://copilotstudio.microsoft.com/+++ y seleccione el entorno
    **Dev One**.

![](./media/image12.png)

2.  Desde la **Home page**, ingresa el siguiente texto en el área **Describe the agent text area** y selecciona **Send**. Esto crea el agente con la descripción proporcionada. Las instrucciones para el agente se pueden agregar en los siguientes pasos si es necesario.

    +++Create an agent that will assist the customers in shopping with Contoso Electronics. Name it as "Shopping agent".+++
    
![A screenshot of a computer AI-generated content may be
incorrect.](./media/im43.png)

4.  Espera hasta que el agente se aprovisione y luego continúa con el siguiente paso.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/im45.png)

### Tarea 2 – Incorpore conocimiento

La acción de añadir conocimiento al agente lo conecta con los recursos
de información definidos, lo que le permite responder a las consultas de
los usuarios de manera más eficaz. En esta tarea, se agregará la tabla
de Dataverse creada en el ejercicio anterior como fuente de conocimiento
para este agente.

1.  Ingrese +++What is the status of the order o1001?+++ en el panel de
    prueba.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image19.png)

2.  La respuesta será similar a la siguiente ya que el agente no tiene
    ninguna información al respecto.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image20.png)

3.  Ahora, agregaremos la fuente de conocimiento al agente. En la página
    **Home** del agente, haga clic en **Add Knowledge** en la sección
    **Knowledge**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

4.  Seleccione **Dataverse** de la lista de opciones disponibles.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

5.  Busque +++order+++, seleccione la tabla **Order Record** y haga clic
    **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  Seleccione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  Espere unos minutos después de agregar la fuente de conocimiento
    antes de probar el agente nuevamente.

8.  Una vez que el **Order Record** esté **Ready** en la sección
    Knowledge, haga la misma pregunta en el panel de prueba.

Ahora puede ver que el agente recupera la información de la base de
datos y se la proporciona al usuario.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

### Tarea 3: Crear entidades

1.  Seleccione **Settings** en la pantalla de inicio del agente. ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image26.png)

2.  Seleccione **Entities** en el panel izquierdo. Luego, seleccione
    **Add an entity -\> + New entity.**

![](./media/image27.png)

3.  Seleccione **Closed list**.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image28.png)

4.  Ingrese los detalles a continuación.

Name - +++Laptop+++

Description - +++Contains products under Laptop category+++

En **List items**, ingrese +++Apple MacBook Air M3+++ y haga clic en
**Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

5.  De manera similar, agregue los siguientes elementos y luego
    seleccione **Save**.

+++Dell XPS 13 Plus+++

+++HP Spectre x360 14+++

+++Lenovo ThinkPad X1 Carbon Gen 12+++

+++Asus ROG Zephyrus G14+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

6.  Ahora, repita los pasos 2 a 5 con los siguientes datos.

Name - +++Desktop+++

Description - +++Contains products under Desktop category+++

En **List items**, ingrese +++Apple iMac+++ y haga clic en **Add**.

7.  Otros elementos que se añadirán a la lista,

+++Microsoft Surface Studio 2+++

+++HP Envy Desktop+++

+++Dell Inspiron Desktop+++

+++Lenovo IdeaCentre AIO 5i+++

8.  Nuevamente, repita los pasos 2 a 5 con los siguientes datos.

Name - +++Tablet+++

Description - +++Contains products under Tablet category+++

En **List items**, ingrese +++Apple iPad Pro+++ y haga clic en **Add**.

9.  Otros elementos que se añadirán a la lista,

+++Samsung Galaxy Tab S9 Ultra+++

+++Microsoft Surface Pro 10+++

+++Lenovo Tab P12 Pro+++

+++Apple iPad Air+++

## Ejercicio 3 – Creación de temas, flujos del agente y diseño del agente

El diseño de temas es una parte muy importante en la creación de un
agente, ya que se ocupa de la lógica detrás de cómo se responden las
preguntas del usuario y cómo será el flujo de los detalles.

### Tarea 1: Editar el tema de inicio de la conversación

El tema "Inicio de conversación" es el primero que se invoca al probar
el agente. Es un tema del sistema disponible de forma predeterminada en
cualquier agente que cree en Copilot Studio. Ahora, editará este tema
para continuar la conversación desde el mensaje de bienvenida del
agente.

1.  En la página **Overview** del agente, seleccione la pestaña
    **Topics** en la barra de menú superior. Seleccione **System** para
    visualizar la lista de temas del sistema. Haga clic en el tema
    Conversation Start de la lista.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  Después del nodo mensaje existente, agregue un **Question node**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  Ingrese el siguiente mensaje,

+++Welcome to Contoso Electronics. Please enter your **Phone number** to
proceed.+++ En el área de mensajes, seleccione **User’s entire
response** dentro de **Identity**. Haga clic en **Var1** en el campo
**Save user response as**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

4.  Cambie el nombre de **Var 1** a +++MobileNumber+++ y seleccione
    **Global** para usarlo en todos los temas. Luego, seleccione
    **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

### Tarea 2: Creación de un tema para gestionar los detalles del cliente

1.  En la página de descripción general del agente, seleccione la
    pestaña Temas en la barra de menú superior. Seleccione el menú
    desplegable junto a **Add a topic -\> From blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  Nombre al agente como +++Customer Details+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  Seleccione **Change trigger** y luego **It’s redirected to** como
    desencadenador.

![Screens screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

4.  Haga clic en **Save** para guardar el tema.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

### Tarea 3: Creación de un flujo de agente para obtener los detalles del cliente

En esta tarea se creará un flujo del agente que recibirá como entrada el
número de teléfono proporcionado por el cliente. El flujo estará
diseñado para verificar la existencia del usuario, recuperar su
información y devolver los detalles correspondientes al agente.

1.  Debajo del nodo desencadenador, agregue un nodo seleccionando **Add
    a tool** -\> **New Agent flow**.

![](./media/image39.png)

2.  Se abrirá el diseñador de flujo del agente. Seleccione **Save
    draft** para guardar el flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  Seleccione **Overview** en el menú superior, haga clic en **Edit** e
    ingrese el nombre del flujo "+++ GetCustomer+++". A continuación,
    seleccione **Save**. ![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image41.png)

4.  Vuelva a la pestaña **Designer** para diseñar el flujo. Seleccione
    el nodo **When an agent calls the flow** y haga clic en **+ Add an
    input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  Seleccione **Text**.

![](./media/image43.png)

6.  Ingrese la entrada como +++Phone number+++ y luego contraiga la
    pestaña **Parameters**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  Haga clic en **Add an action** entre los dos nodos del flujo. Busque
    +++List rows+++ y seleccione la acción **List rows** en **Microsoft
    Dataverse**.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

8.  Ingrese el nombre de la conexión como +++**Dataverse**+++ y haga
    clic en **Sign in**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  **Sign in** mediante el uso de las credenciales administrativas del
    tenant; si se le solicita, conceder acceso seleccionando **Allow
    access**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. Acceda a PowerApps en +++https://make.powerapps.com/+++ y abra la
    tabla **Customer Record.** Haga clic en el menú desplegable junto al
    campo **Mobile number** y seleccione **Edit column**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. Desplácese hacia la parte inferior y, dentro de la sección
    **Advanced** **options**, identifique el campo **Logical name**.
    Anote su valor para referencia posterior.

**Importante:** En Dataverse, todos los campos poseen un nombre lógico.
En la configuración del flujo del agente, debe utilizarse exclusivamente
el nombre lógico de cada campo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. En este caso, para el número de teléfono, es **cr6dd_mobilecontact**
    . Anótelo.

13. Regrese a la pestaña de flujo de Copilot Studio – Agente. Abra el
    flujo Getcustomer y seleccione la acción **List rows**.

14. En Filter rows, ingrese **\<Logical name of Mobile number\> eq '
    '**. Reemplace **\<Logical name\>** con el valor obtenido en el paso
    anterior. Mantenga el cursor entre comillas y agregue la variable
    dinámica **'Phone number'**.

En este caso será **cr6dd_mobilecontact eq 'Phone number'**

![](./media/image50.png)

![](./media/image51.png)

15. Debajo del nodo List rows, agregue un nodo **Condition**.

![](./media/image52.png)

16. Ingrese **/** y seleccione **Insert expression**.

![](./media/image53.png)

17. Ingrese +++length(outputs('List_rows')?\['body'\]?\['value'\])+++ en
    la función y seleccione **Add**. Esto permitirá verificar si las
    filas de la lista retornan algún valor.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

18. Haga clic en **Add an action** debajo de la rama **True** de la
    condición agregada y añada un nuevo nodo de tipo **Condition node.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

19. Ingrese +++not(empty(first(outputs('List_rows')?\['body/value'\])?\[
    cr6dd_lastpurchasedproduct '\]))+++ en el área de función de la
    condición.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

> **Importante** : Asegúrese de reemplazar
> **cr6dd_lastpurchasedproduct** con el **logical name** del campo
> **Recent Products Purchased** de la tabla **Customer Record**.
>
> ![](./media/image58.png)

20. Establezca la condición como **is equal to true.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

21. Agregue una nueva acción debajo de la ruta **True** de
    **Condition1** y seleccione el nodo **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

22. Haga clic en **Respond to the agent node** y cámbiele el nombre a
    +++If the customer has made a previous purchase+++. Seleccione **+
    Add an output**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

23. Seleccione **Text**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

24. Ingrese +++Customer ID+++ como nombre y haga clic en **Insert
    expression**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

25. Ingrese+++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
    +++ El **cr6dd_customeridentifier** es el nombre lógico del ID de
    cliente de la tabla registro de clientes. **Reemplácelo** con su
    valor.

26. Seleccione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

27. De igual forma, agregue las siguientes variables y expresiones de
    salida a cada una. Para cada variable, asegúrese de reemplazar el
    nombre lógico por el suyo.

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_lastpurchasedproduct'\]+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

28. El nodo **Respond to the agent** del agente contendrá tres variables
    de salida, como se muestra en la captura de pantalla a continuación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

29. Agregue un nodo "Responder al agente" en la ruta **False** del nodo
    **Condition1**. Renómbrelo como +++If the customer has not made a
    previous purchase+++. Haga clic en **+ Add an output**.

![](./media/image68.png)

30. Ingrese las siguientes variables de salida, reemplazando los nombres
    lógicos de ejemplo por los nombres lógicos correspondientes a cada
    columna.

- +++Customer ID+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
  +++

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ - +++’1’+++

31. La **respuesta al** nodo del agente bajo la ruta **False** se verá
    como la que se muestra en la siguiente captura de pantalla.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

32. Ahora, agregue una **respuesta al** nodo del agente bajo la ruta
    **False** del nodo condición, cámbiele el nombre a +++If the
    customer does not exist+++ y agréguele salidas como se muestra a
    continuación.

- +++Customer ID+++ - +++’1’+++

- +++Customer Name+++ - +++’1’+++

- +++Product Category+++ - +++’1’+++

![](./media/image70.png)

33. El flujo **GetCustomer** se verá como el que se muestra en la
    captura de pantalla a continuación.

![](./media/image71.png)

34. En el nodo **Respond to the agent,** situado al final del flujo,
    haga clic derecho y seleccione **Delete** para proceder con su
    eliminación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

35. Seleccione **Save Draft** para guardar el laboratorio. Una vez
    guardado, haga clic en **Publish** para publicar el flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

### Tarea 4: Diseño de un flujo del agente para la incorporación de clientes

En esta tarea, creará un flujo de agente para agregar un nuevo cliente a
Dataverse cuando el cliente sea un cliente nuevo.

1.  Desde la pestaña **Agent flows**, seleccione **+ New agent flow.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  Seleccione el nodo **Add a trigger** y reemplácelo al nodo **When an
    agent calls the flow**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

3.  Seleccione **+ Add an input** y agregue una entrada de **Text**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

4.  Ingrese +++Name+++ como nombre de entrada.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

5.  De manera similar, agregue los siguientes valores de entrada.

+++Phone Number+++

+++Email ID+++

+++Address+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image79.png)

6.  Agregue una acción debajo del nodo y seleccione **Add a new row**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

7.  Seleccione el nombre de la tabla como **Customer Record** y luego
    seleccione **Show all** en parámetros avanzados.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

8.  Haga clic en el campo **Address,** seleccione **Dynamic value** y
    haga clic en el valor dinámico **Address**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image83.png)

9.  De manera similar, agregue los valores dinámicos para:

- Customer Name – Name

- Email ID – Email ID

- Mobile Number – Phone Number

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

10. Abra la expresión de inserción para **Customer ID**, ingrese
    +++guid()+++ y seleccione **Add**. Esto permite agregar un valor
    único como ID del cliente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

11. Agregue una nueva acción y seleccione **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

12. Agregue un valor de salida llamado +++Customer ID+++ e inserte una
    expresión e ingrese
    +++string(outputs('Add_a_new_row')?\['body/cr6dd_customeridentifier'\])+++
    como valor.

Reemplace **cr6dd_customeridentifier** con su nombre lógico para la
columna **Customer ID**.

Seleccione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

13. Seleccione **Save draft** para guardar el flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

14. Una vez guardado el flujo, seleccione **Publish** para publicar el
    flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

15. Seleccione la pestaña **Overview**. **Haga cli en Edit.** Ingrese el
    nombre del flujo como +++Add Customer+++ y seleccione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

### Tarea 5: Agregar el flujo y diseñar el tema Customer Details

En esta tarea, diseñará el tema **Customer Details** donde obtendrá el
número de teléfono del cliente, verificará si el detalle ya está
presente en Dataverse y lo agregará si aún no está presente.

1.  Regrese al tema **Customer Details**.

2.  Agregue un nodo debajo del nodo desencadenador, seleccione **Add a
    tool -\> GetCustomer**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

3.  En las entradas, seleccione la variable **MobileNumber**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

4.  Seleccione las variables **output** y marque el ID del cliente y la
    categoría del producto como **Global** como en la captura de
    pantalla a continuación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

5.  Debajo del nodo **Action,** agregue un nodo de **condition**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

6.  Seleccione **CustomerID** en **Select a variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

7.  Seleccione la condición como **is not equal to** e ingrese +++
    '1'+++ en el campo **Value**. Esto verifica si el detalle del
    cliente ya existe en la base de datos.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

8.  Debajo del nodo de condición, agregue un nodo **Set a variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

9.  Haga clic en **Select a variable** y seleccione **Create a new
    variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

10. Nombre la variable +++IsNewCustomer+++ y márquela como **Global**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

11. Establezca el valor como +++‘No’+++. Esto significa que el cliente
    es un cliente antiguo cuyos datos ya están presentes en Dataverse.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

12. Agregará un nuevo nodo junto al nodo variable y dará un mensaje de
    bienvenida al cliente.

13. Seleccione Add a node y luego el nodo **Send a message**. En el área
    de mensajes, escriba +++Welcome+++ y haga clic en el icono {x} para
    seleccionar la variable. Seleccione la variable **Customer Name**.

![](./media/image101.png)

Ahora, hemos invocado el flujo de agente **GetCustomer**, verificamos si
el registro del cliente ya existe y, si es así, agregamos un mensaje de
bienvenida al cliente.

Ahora, diseñaremos la parte del tema si el registro del cliente aún no
existe.

13. En el nodo **All other** agregue un nodo **set a variable** y
    establezca el valor para la variable **isNewCustomer** como
    +++’Yes’+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

14. Junto al nodo variable, agregue un nodo **Message** e ingrese +++We
    do not have your details in our system. Please fill in your details
    below to help us serve you better.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

15. Junto al nodo **Message**, agregue un nodo **Ask with adaptive
    card**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

16. Haga clic en los 3 puntos en la parte superior derecha de la
    pantalla y seleccione **Properties**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

17. Seleccione **Edit adaptive card**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

18. Ingrese el **JSON** **a continuación** en el área **Card payload
    editor**. Haga clic en **Save**.

> {
>
> "type": "AdaptiveCard",
>
> "body": \[
>
> {
>
> "type": "TextBlock",
>
> "size": "Medium",
>
> "weight": "Bolder",
>
> "text": "Please enter your details"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Name",
>
> "label": "Name"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Mobile Number",
>
> "label": "Mobile Number"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Email ID",
>
> "label": "Email ID"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Address",
>
> "label": "Address"
>
> }
>
> \],
>
> "actions": \[
>
> {
>
> "type": "Action.Submit",
>
> "title": "Submit"
>
> }
>
> \],
>
> "version": "1.5",
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json"
>
> }
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image107.png)

19. Seleccione **Close** para cerrar el editor.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

20. Expanda la sección **Outputs** del nodo de tarjeta adaptable creada,
    seleccione el valor correspondiente a número de teléfono móvil y
    asígnelo a la variable **Global.MobileNumber** para almacenar el
    número ingresado por el usuario.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

21. Deje los demás valores con los estados predeterminados.

22. La tarjeta adaptable está lista con el formulario para obtener los
    datos del cliente.

23. Junto al nodo Tarjeta adaptable, invoque el flujo **Add Customer.**

![](./media/image110.png)

24. Haga clic en **los tres puntos** del campo **Enter or select a
    value** y seleccione la variable **CustomerName.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

25. De manera similar, agregue las variables de entrada para los demás
    campos que se pasarán al flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

26. Seleccione **Global.CustomerID** como la variable de salida en la
    que se guardará la salida del flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

27. Después del nodo de acción, agregue un **nodo de mensaje** e ingrese
    el valor: +++Thank You! Customer detail has been added to the
    database. Please select a product type to shop.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

28. Haga clic en **Save,** para guardar el tema.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

29. Abra el tema de Conversation Start y desde allí invoque el tema de
    Customer Details.

30. Añada un nodo después del nodo "Question" en el tema. Seleccione
    **Topic management -\> Go to another topic**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

31. Seleccione el tema **Customer Details**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

32. Seleccione **Save** para guardar el tema.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### Tarea 6: Crear un flujo de agente para obtener los detalles del producto

En esta tarea, creará un flujo de agente que obtendrá los detalles del
producto de Dataverse en función del producto seleccionado.

1.  Seleccione la pestaña **Flows** de Copilot Studio y seleccione **+
    New agent flow**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  Seleccione el nodo de activación y elija la opción **When an agent
    calls the flow action**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  Agregue una entrada de texto y asígnele el nombre +++Product Name+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

4.  Seleccione **Save draft** para guardar el flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

5.  Seleccione la pestaña **Overview** y haga clic en **Edit**. Ingrese
    el nombre +++GetProductDetails+++ y seleccione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

6.  Regrese a la pestaña **Designer** y seleccione **Add an action**
    **acción** debajo del nodo **When an agent calls the flow**. Busque
    +++list rows+++ y seleccione la acción **List rows** en **Microsoft
    Dataverse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

7.  Ingrese los siguientes valores

- **Table name –** Seleccione **Product Record**

- Filter rows – +++cr6dd_producttitle eq '**\<Product Name\>**'+++
  Reemplace \<Product Name\> con el valor dinámico ProductName.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image125.png)

8.  Agregue un nodo **Respond to the agent** en el nodo **List rows**.
    Seleccione **+ Add an output** y agregue una variable de salida de
    texto. Ingrese los siguientes valores y haga clic en "Add" en la
    **insert expression.**

    - Ingrese un nombre – Ingrese +++Product Name+++

    - Expresión -
      +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_producttitle'\]+++
      (Reemplace **cr6dd_producttitle** con el nombre lógico de la
      columna Product Name en su tabla.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image126.png)

9.  De manera similar, agregue otro nodo de salida con los siguientes
    detalles

- Ingrese un nombre – Ingrese +++Price+++

- Expresión -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_productprice'\]+++
  Reemplace **cr6dd_productprice** con el nombre lógico de la columna
  **Price** en su tabla.

> El nodo ahora debería verse así.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image127.png)

10. Seleccione **Save draft** para guardar el tema y luego **Publish**
    para publicar el flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

### Tarea 7 – Crear un tema para obtener la categoría de producto del cliente

1.  Desde la pestaña Topics de Copilot Studio, seleccione **+ Add a
    topic -\> From blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

2.  Cambie el nombre del tema a +++Place Order+++. Cambie el
    desencadenador del nodo de activación a **It’s redirected to**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

3.  Haga clic en **Save,** para guardar el tema.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image131.png)

4.  Desde la pestaña Topics de Copilot Studio, seleccione **+ Add a
    topic -\> From blank**.

![](./media/image129.png)

5.  Cambie el nombre del tema a +++Get Product Categories+++. Seleccione
    la opción **Change trigger** en el nodo **Trigger** y seleccione la
    opción **It’s redirect to**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

6.  Debajo del nodo **Trigger**, agregue un nodo **Condition**.

Seleccione la variable global **IsNewCustomer** y agregue la condición,
**IsNewCustomer** **is equal to** +++**'Yes'**+++.

Seleccione **+ New condition.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

7.  Seleccione **Or**.

En la condición Or, seleccione la variable global **ProductCategory** y
agregue la condición, **is equal to** +++'1'+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

![](./media/image136.png)

8.  En el nodo condición, agregue un nodo de pregunta e ingrese
    +++Select a category+++ y seleccione **+ New option**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

9.  Ingrese a la opción +++Laptop+++ y seleccione nuevamente la opción
    **+ New option**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

10. De forma similar, agregue otras dos opciones +++**Desktop**+++ y
    +++**Tablet**+++. Seleccione la variable en **Save user response
    as**, y nómbrela como +++**ProdCatchoice**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

11. Debajo del nodo de pregunta, agregue un nodo **Set a variable
    value** para convertir la opción recibida del nodo de pregunta en
    una cadena.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

12. Seleccione la variable global **ProductCategory** en la sección Set
    variable. En el campo **To value**, haga clic en los tres puntos y
    seleccione la pestaña **Formula**. Ingrese la expresión
    +++Text(Topic.ProdCatchoice)+++ y seleccione **Insert**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

13. Debajo del nodo Set variable value, agregue un nuevo nodo, **Topic
    management** -\> **Go to another topic** -\> **Place Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

14. Ahora, una ruta está completamente finalizada. Obtendrá la categoría
    del usuario e invocará el tema Place Order.

15. Regrese al inicio de este tema. En cualquier otra situación, agregue
    un nodo de **Question**. Agregue el mensaje +++Based on your recent
    purchase we suggest you products in \<Product Category\> category.
    Would you like to continue?+++

En el mensaje reemplace **\<Product Category\>** con la variable
**Global.ProductCategory.**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image143.png)

16. Agregue dos opciones, +++Yes+++ y +++No+++. Haga clic en la variable
    bajo Save user response as y cámbiele el nombre a
    +++Userschoiceofcategory+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

17. Debajo del nodo **question**, agregue un nodo **condition**.

Establezca la primera condición como **Userschoiceofcategory is equal to
Yes**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

36. Debajo de este nodo, agregue un **Topic management node** e invoque
    el tema **Place Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

18. En el nodo de condición, seleccione los tres puntos en la esquina
    superior derecha del nodo y elija **Insert new condition**.

![](./media/image147.png)

19. Agregue una condición, **Userschoiceofcategory is equal to No**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

20. En el nodo condición, agregue un nodo de pregunta e ingrese
    +++Select a category+++ y seleccione **+ New option**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

21. Ingrese a la opción +++Laptop+++ y seleccione nuevamente la opción +
    New option.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

22. Del mismo modo, agregue otras dos opciones +++**Desktop**+++ y
    +++**Tablet**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

23. Debajo del nodo de pregunta, agregue un nodo **Set a variable
    value** para convertir la opción recibida del nodo de pregunta en
    una cadena.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

24. Seleccione la variable global **ProductCategory** en la sección Set
    variable. En el campo **To value**, haga clic en los 3 puntos y
    seleccione la pestaña **Formula**. Ingrese la expresión
    +++Text(Topic.Var1)+++ y seleccione **Insert**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

25. Debajo del nodo Set variable value, agregue un nuevo nodo, **Topic
    management** -\> **Go to another topic** -\> **Place Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

26. Seleccione **Save** para guardar el tema.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image151.png)

27. Abra el tema **Customer Details** y muévase al último nodo.

28. **Add a new node** para invocar el tema **Get Product Categories**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image152.png)

29. Seleccione **Save** para guardar el tema.

![](./media/image153.png)

### Tarea 8: Crear flujo de agente para realizar el pedido

En esta tarea, creará un flujo de agente para realizar el pedido en
función del producto elegido por el cliente.

1.  Desde la pestaña **Agent flows**, seleccione **+ New agent flow.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image154.png)

2.  Haga clic en **Add a trigger node** y seleccione al nodo **When an
    agent calls the flow**.

![](./media/image155.png)

3.  Agregue 2 variables de **Texto** +++Product Name+++ y +++Customer
    ID+++ como **Input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image156.png)

4.  Haga clic en **Save Draft** para guardar el flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image157.png)

5.  Seleccione **Overview** en el menú superior, haga clic en **Edit** e
    ingrese el nombre del flujo +++PlaceOrder+++. A continuación,
    seleccione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image158.png)

6.  Regrese a la pestaña **Designer**. Seleccione Add a new action y, en
    Dataverse **Add a new row**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image159.png)

7.  Seleccione el nombre de la tabla como **Order Record** y luego haga
    clic en **Show all** en **Advanced parameters.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image160.png)

8.  Ingrese los siguientes valores.

Customer Identifier - **Customer ID** (valor dinámico)

Order identifier – Ingrese guid() en la expresión Insert

Order Status - +++**Order Placed**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image161.png)

9.  Agregue un nodo, **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image162.png)

10. Agregue una variable de texto de salida y nómbrela +++Order ID+++.

Ingrese su valor como +++
string(outputs('Add_a_new_row')?\['body/cr6dd_orderidentifier'\])+++
(Reemplace **cr6dd_orderidentifier** con el valor del nombre lógico de
la columna Order ID de la tabla Order Record.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image163.png)

11. Haga clic en **Save draft** para guardar el flujo y luego haga clic
    en **Publish** para publicar el flujo.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image164.png)

### Tarea 9 – Diseñar el tema Place Order 

En esta tarea, diseñará el tema para realizar el pedido y actualizar la
tabla Dataverse.

1.  Abra el tema **Place Order** desde la pestaña **Topic** del agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image165.png)

2.  Agregue un nodo de mensaje con +++Options based on the category will
    be listed below.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image166.png)

3.  Agregue un nodo de condición. Ingrese la condición como
    ProductCategory(Global variable) igual a +++Laptop+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image167.png)

4.  Debajo del nodo, agregue un nodo de pregunta e ingrese el mensaje
    +++Select a Laptop product+++. Seleccione **Laptop** en
    **Identity**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image168.png)

5.  Haga clic en **Select** **options for user** y seleccione las 5
    opciones disponibles.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image169.png)

6.  Ingrese el nombre de la variable como +++ProdNameLapChoice+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image170.png)

7.  Ahora, siga el mismo procedimiento y agregue nodos de condición para
    ProductCategory is equal to +++Desktop+++ y +++Tablet+++.

8.  Guarde los valores en nombres de variables.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image171.png)

9.  Seleccione un nodo **Set variable value** debajo del nodo de
    pregunta **Select a Laptop product**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image172.png)

10. Cambie el nombre de la variable creada a +++ProdNameSelected+++ y
    configúrela como **Global**.![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image173.png)

11. Establezca el valor en el campo fórmula como
    +++Text(Topic.ProdNameLapChoice)+++ (Reemplace el nombre de la
    variable, si ha utilizado uno diferente).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image174.png)

12. De forma similar, agregue un nodo **Set variable value** en las
    ramas **Desktop** y **Tablet.** Seleccione **Set variable**
    **value** como **ProdNameSelected** e inserte la expresión en el
    campo **To value** utilizando el nombre de la variable
    correspondiente al que se haya usado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image175.png)

13. Agregue un nodo de acción debajo de todos estos nodos en común e
    invoque el flujo GetProductDetails.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image176.png)

14. Seleccione la variable de entrada **ProdNameSelected** que se pasará
    al flujo. Deje los demás valores predeterminados.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image177.png)

15. Agregue un nodo de mensaje debajo del nodo de acción e ingrese el
    siguiente mensaje. Reemplace \<ProductName\> y \<Price\> con los
    nombres de las variables correspondientes

Detalles del producto

- Product Name - \<ProductName\>

- Price - \<Price\>

​

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image178.png)

16. Debajo del nodo de mensaje, agregue **Question node** con el
    mensaje, +++Would you like to place order for this item?+++. Añada
    las opciones **Yes** y **No** y nombre la variable +++PlaceOrder+++.

![](./media/image179.png)

17. En el nodo Pregunta, agregue un nodo de condición. En una de las
    ramas, configure la condición **PlaceOrder is equal to yes**; todas
    las demás condiciones se asignarán a la segunda rama.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image180.png)

18. Invoque el flujo **PlaceOrder** como el siguiente paso.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image181.png)

19. Seleccione **ProductName** y **CustomerID** como entrada para el
    flujo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image182.png)

20. Ahora, agregue un nodo de mensaje debajo de este con el siguiente
    mensaje: +++Your order is placed. This is your Order ID for
    reference - \<OrderID\>+++ (Reemplace **\<OrderID\>** con la
    **variable OrderID**, que es la **variable de salida** del flujo).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image183.png)

21. Con esto, la rama **PlaceOrder is equal to Yes** está **completa**.
    Ahora, navegue a la rama **all other conditions.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image184.png)

22. Debajo de esa rama, agregue un nodo de pregunta con el mensaje:
    +++Do you want to go to the main menu?+++ con las opciones **Yes** y
    **No**. Asigne un nombre a la variable como +++**GoToMainMenu**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image185.png)

23. Debajo de este nodo, agregue un nodo de condición y, en una rama,
    agregue una condición con **GoToMainMenu is equal to Yes**. La otra
    rama de esta condición será **All other conditions**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image186.png)

24\. Debajo de este nodo de condición, agregue un nodo de pregunta con
el mensaje: +++**Select Product Category**+++ y añada 3 opciones:
+++**Laptop**+++, +++**Desktop**+++ y +++**Tablet**+++.  
Tome nota del nombre de la variable en la que se guarda el resultado, ya
que se convertirá a texto en el siguiente paso.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image187.png)

25. Agregue un nodo **Set variable value**, seleccione la variable
    **ProductCategory** en el campo set variable e ingrese el valor
    +++**Text(Topic.Var1**)+++ en la pestaña **Formula**.  
    Reemplace **Var1** con el nombre de su variable si es diferente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image188.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image189.png)

26. En el nodo Set variable, agregue un nodo **Go to step**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image190.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image191.png)

27. Después de agregar el nodo, será necesario seleccionar el **paso**
    al que **debe dirigirse el control** en este punto. **Desplácese
    hacia arriba** y seleccione el **nodo de mensaje ubicado al inicio
    de este tema**, ya que ahora se ha obtenido la variable
    **ProductCategory** del cliente y es necesario continuar la
    ejecución desde el principio.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image192.png)

28. Añada un nodo de mensaje común al final con el siguiente mensaje
    +++Thank you for shopping with us! Please visit again!+++ Luego,
    seleccione **Save** para guardar el tema.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image193.png)

## Ejercicio 4 – Agregar un desencadenador

En este ejercicio, agregará un desencadenador que se activará cuando se
agregue una nueva fila a la tabla de pedidos o se modifique una fila
existente, y enviará un correo electrónico al cliente automáticamente.
Esto define la capacidad autónoma del agente en este escenario.

1.  Seleccione la pestaña **Overview** del agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image194.png)

2.  Desplácese hacia abajo en la página y seleccione **Add trigger.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image195.png)

3.  Seleccione la opción **When a row is added, modified or deleted** y
    luego seleccione **Next**.

![](./media/image196.png)

4.  Una vez que **Microsoft Copilot Studio** y **Dataverse** estén
    conectados, haga clic en **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image196.png)

5.  Seleccione las siguientes opciones, deje el resto en estado
    predeterminado y seleccione **Create trigger**.

- Change Type – Added or Modified or Deleted

- Table name – Order Record

- Scope - Organization

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image197.png)

6.  Esto podría tardar unos minutos. Una vez hecho esto, seleccione
    **Close** en el cuadro de diálogo **Add trigger.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image198.png)

7.  Desde la sección **Trigger** en la página **Overview** del agente,
    haga clic en los **3 puntos** junto al desencadenador agregado y
    seleccione **Edit in Power Automate**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image199.png)

8.  Seleccione el primer nodo en el flujo y agregue los nombres de las
    columnas, +++cr6dd_orderidentifier, cr6dd_customeridentifier+++ en
    **Select columns**. (**Reemplácelos** con **los nombres lógicos** de
    las columnas **Order ID** y **Customer ID** de la **tabla Order
    Record**).

![](./media/image200.png)

9.  Agregue un nuevo nodo y seleccione la acción **List rows** en él.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image201.png)

10. En la acción **List rows**, seleccione **Table name** como
    **Customer Record**.

En **Filter rows**, ingrese +++**cr6dd_customeridentifier eq ''**+++,
reemplazando el nombre de la columna con **Customer ID’s logical name**.
Mantenga el **cursor dentro de las comillas simples.**

![A screenshot of a list AI-generated content may be
incorrect.](./media/image202.png)

11. Seleccione Insert expression, ingrese
    +++String(triggerOutputs()?\['body/cr6dd_customeridentifier'\])+++,
    reemplazando **cr6dd_customeridentifier** con el nombre lógico de su
    CustomerID y seleccione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image203.png)

12. Junto a las **List rows**, agregue una acción **Send an email
    (V2).**

![A screenshot of a mail box AI-generated content may be
incorrect.](./media/image204.png)

13. Haga clic en **Sign in** e inicie sesión con sus credenciales.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image205.png)

14. En el campo **To**, inserte la expresión e ingrese
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_emailaddress'\]+++,
    ++, reemplazando **cr6dd_emailaddress** con el nombre lógico de su
    campo de identificación de correo electrónico de la tabla registro
    de cliente y luego seleccione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image206.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image207.png)

15. Ingrese los detalles a continuación,

Subject - +++Order Placement+++

Body –

Hi,

This is to update you that your order has been placed. Thank you for
shopping with us.

Thank You.

16. Guarde el flujo y luego publíquelo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image208.png)

17. De regreso a la página del agente de Copilot Studio, seleccione
    **Publish** para publicar el agente.

![](./media/image209.png)

18. Seleccione **Publish** en el cuadro de diálogo de confirmación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image210.png)

19. ewqewqew

## Ejercicio 5 – Probar el agente

En este ejercicio, probará cómo funciona el agente.

1.  Desde la página del agente, seleccione **Test** para abrir el panel
    prueba.

2.  Ingrese +++3148987666+++. Este es el número de teléfono de un
    cliente existente.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image211.png)

3.  Seleccione **Yes** de las opciones dadas.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image212.png)

4.  Seleccione un **producto** de las opciones dadas.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image213.png)

5.  Seleccione **Yes** de las opciones dadas.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image214.png)

6.  Se realiza el pedido y se proporciona el ID de referencia al
    cliente.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image215.png)

7\. También puede hacer otras preguntas, como el seguimiento de la
entrega del pedido con la identificación que recibió. Aunque no hemos
configurado temas para eso, le daremos una respuesta basada en la fuente
de información.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image216.png)

Pruebe los demás escenarios seleccionando diferentes opciones. Añada un
nuevo cliente y compruebe que ha recibido un correo en su dirección de
correo electrónico, que se añade a la tabla de registro de clientes.

## Resumen:

En este laboratorio se abordó el diseño de un agente de compras
autónomo. Los temas tratados incluyeron los siguientes:

- Variables

- Entidades

- Temas

- Flujos de agentes

- Desencadenadores

- Fuentes de conocimiento
