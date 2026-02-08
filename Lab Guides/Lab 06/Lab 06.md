
# Laboratorio 06 – Creación de un agente de asistente de conocimiento para RR. HH. en Copilot Studio que aproveche Azure AI Search

## Objetivo

Una gran empresa desea reducir el tiempo que los empleados dedican a
buscar información relacionada con RR. HH. (políticas, prestaciones,
políticas sobre permisos, etc.) dispersa en SharePoint, archivos PDF,
wikis internos y documentos.

Para solucionar este problema, en este laboratorio creará
un **agente** **asistente de conocimiento** en **Copilot Studio** que
utiliza **Azure AI Search** para indexar y buscar semánticamente en los
documentos de RR. HH. de la empresa.

## Ejercicio 1: Crear un recurso de Azure AI Search

1. Abre un navegador e inicia sesión en el portal de Azure en +++https://portal.azure.com/+++
 con tus credenciales.

    -    Username - +++@lab.CloudPortalCredential(User1).Username+++

    -    Password - +++@lab.CloudPortalCredential(User1).Password+++

   Desde la **Home page** del portal de Azure, busca +++Microsoft Foundry+++ y selecciona **Microsoft Foundry** en **Services**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im41.png)

2.  En la **página AI Foundry**, seleccione **AI Search** en el panel
    izquierdo y, a continuación, seleccione **+ Create**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image2.png)

3.  Ingrese los siguientes datos y seleccione **Review + create**.

- Subscription – Seleccione su **suscripción asignada**

- Resource group – Seleccione el **grupo de recursos** asignado
  (**ResourceGroup1**)

- Storage account name – +++**searchleaves**+++

- Location – Seleccione su **región asignada**

![A screenshot of a search service AI-generated content may be
incorrect.](./media/image3.png)

4.  Una vez pasada la validación, seleccione **Create**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image4.png)

5.  La implementación tarda unos minutos. Seleccione **Go to
    resource** una vez creado el servicio de búsqueda.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  En la página **Overview**, copie el valor URL y guárdelo en un bloc
    de notas para utilizarlo en un ejercicio futuro.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  Seleccione **Keys** en **Settings** en el panel izquierdo. Copie
    la **Primary admin key** y guárdela en un bloc de notas para
    utilizarla en los próximos ejercicios.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  Seleccione **Identity **en **Settings **en el panel izquierdo.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image8.png)

9.  Cambie el estado a **On** en **System assigned** y, a continuación,
    haga clic en **Save**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image9.png)

10. Seleccione **Yes** en el cuadro de diálogo de confirmación **Enable
    system assigned managed identity**.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image10.png)

## Ejercicio 2: Crear una cuenta de almacenamiento

1.  Inicie sesión en Azure Portal en +++https://portal.azure.com/+++ e
    inicie sesión con sus credenciales. Seleccione Storage accounts en
    la pantalla de inicio.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  Seleccione **+ Create** para crear una nueva cuenta de
    almacenamiento.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

3.  Ingrese los siguientes datos, acepte los valores predeterminados en
    los demás campos y haga clic en **Review + create**.

- Subscription – Seleccione su **suscripción asignada**

- Resource group – Seleccione su **grupo de recursos asignado**
  (**ResourceGroup1**)

- Region – Seleccione su **región asignada**

- Storage account name – +++**leavepolicystorage**+++

- Primary service – Seleccione **Azure Blob Storage o Azure Data Lake
  Storage Gen 2**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

4.  Una vez pasada la validación, haga clic en **Create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  Una vez que se haya creado el recurso, haga clic en **Go to
    resource**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  Seleccione **Containers** en **Data storage**. Seleccione **+
    Container**, ingrese el nombre como +++**document**+++ y haga clic
    en **Create** para crear el contenedor.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

7.  Seleccione el **documento** de contenedor creado para cargar el
    documento de política de permisos en él.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  Haga clic en **Upload** y luego seleccione **Browse for files**.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image19.png)

9.  Seleccione **LeavePolicy.docx** desde **C:\Labfiles** y luego haga
    clic en **Upload**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

10. Vaya a la cuenta de
    almacenamiento **leavepolicystorage** (seleccione **Storageaccounts** en
    la **página de inicio** del Azure Portal y
    seleccione **leavepolicystorage**) y seleccione **Access Control
    (IAM)** en el panel izquierdo. Seleccione **Add -\> Add role
    assignment**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

11. Busque +++**Storage Blob Data Reader**+++, selecciónelo y haga clic
    en **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

12. Haga clic en **Select members**, busque y seleccione su **user id**,
    seleccione su **user id** que aparece en la lista y, a continuación,
    haga clic en **Select**. Esto añade la función Storage Blob Data
    Reader a su ID de usuario.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

13. Seleccione **Managed identity** y, a continuación, seleccione **+ Select members**. Seleccione **Service search** en **Managed identity** y seleccione el servicio de búsqueda **searchleaves** que
    aparece en la lista.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

14. Haga clic en **Select** para seleccionar el servicio de búsqueda.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

15. De vuelta en la pantalla Add role assignment, haga clic
    en **Review + assign**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

16. Seleccione **Review + assign** de nuevo en la siguiente pantalla.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

17. Continúe con el siguiente paso una vez que haya añadido los roles.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

En este ejercicio, hemos creado una cuenta de almacenamiento y hemos
añadido el documento y los permisos de rol necesarios.

## Ejercicio 3: Crear un servicio de Azure OpenAI e implementar un modelo

1.  En la página de inicio del Azure Portal, busque y seleccione
    +++Azure OpenAI++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

2.  Seleccione **+ Create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

3.  Ingrese los siguientes datos y seleccione **Next**.

- Subscription – Seleccione su **suscripción asignada**

- Resource group – Seleccione el **grupo de recursos** **asignado**
  (**ResourceGroup1**)

- Region – Seleccione su **región asignada**

- Name – +++**openaiservice52374668**+++

- Pricing tier – Seleccione **Standard**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  Seleccione **Next** en las dos pantallas siguientes y
    seleccione **Create** en la pantalla **Review + submit**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  Haga clic en **Go to resource** una vez creado el servicio.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

6.  Seleccione **Access control (IAM)** en el panel izquierdo,
    seleccione **Add -\> Add role assignment**.

![](./media/image36.png)

7.  Busque +++**Cognitive Services OpenAI User**+++, seleccione el rol y
    haga clic en **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

8.  Seleccione **+ Select members**, busque su **user id**, selecciónelo
    y haga clic en **Select**.

![](./media/image38.png)

9.  De vuelta en la pantalla **Add role assignment**,
    seleccione **Managed identity**. A continuación, seleccione **+
    Select members**. En la pantalla **Select managed identities**,
    seleccione **Search service** en **Managed identity** y seleccione
    el servicio **seachleaves**.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image39.png)

10. Una vez seleccionado, haga clic en **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

11. Seleccione Review + assign en las dos pantallas siguientes.

![](./media/image41.png)

12. Espere a que aparezca un mensaje de **éxito** en las adiciones de
    roles antes de continuar con las siguientes tareas.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

13. En la página **Overview** del recurso Azure OpenAI Service,
    seleccione **Go to Azure AI Foundry portal** para abrir Azure OpenAI
    Service e implementar un modelo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

14. Seleccione **Deployments** en el panel izquierdo.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

15. Seleccione **+ Deploy model** -\> **From base models**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

16. Busque +++**text-embedding**+++,
    seleccione **text-embedding-3-large** y, a continuación,
    seleccione **Confirm**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

17. Seleccione **Deploy** en Deploy text-embedding-3-large.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

18. El modelo se implementa y la pantalla se carga con los detalles de
    la implementación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

## Ejercicio 4: Crear un índice vectorial

1.  Vaya al recurso del servicio de búsqueda con IA **searchleaves**.
    Seleccione **Import y vectorize data**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  Seleccione la opción **Azure Blob Storage**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  Seleccione la opción **RAG** en la pantalla **What scenarios are you
    targeting?**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  Ingrese los siguientes datos, acepte los demás valores por defecto y
    haga clic en **Next**.

- Subscription – Seleccione su **suscripción asignada**

- Storage account- Seleccione **leavepolicystorage**

- Blob-container – Seleccione **document**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  En la pantalla Vectorize your text screen, la suscripción y los
    detalles del recurso Azure OpenAI ya están completados. Ingrese los
    siguientes datos y haga clic en **Next**.

- Model deployment – Seleccione **text-embedding-3-large**

- Authentication type – Seleccione **System assigned identity**

- Seleccione la casilla para aceptar la alerta de costo de Azure OpenAI.

6.  Seleccione Next en la pantalla **Vectorize and enrich your images**,
    ya que aquí no estamos trabajando con imágenes, y
    seleccione **Next** también en la pantalla **Advanced settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

7.  Seleccione **Create** en la pantalla **Review + create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

8.  Haga clic en **Close** en el cuadro de diálogo de éxito.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

## Ejercicio 5: Crear un agente asistente de conocimiento

1.  Inicie sesión en +++https://copilotstudio.microsoft.com+++ con sus
    credenciales de inicio de sesión.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

3.  Seleccione **Agents** para crear un nuevo agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

4.  Ingrese +++You are a Knowledge assistant agent for HR who will
    answer questions related to leaves and leave policies to the
    employees.+++ y seleccione **Send**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/im42.png)

6.  Una vez creado el agente, en el panel Test, ingrese +++How many days
    can I avail Maternity leaves?+++ y haga clic en **Send.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

7.  Proporciona una respuesta generalizada como se muestra en la
    siguiente captura de pantalla.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image64.png)

## Ejercicio 6: Añadir Azure AI Search como fuente de conocimiento

1.  En la página **Overview** del agente, seleccione **Add knowledge**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

2.  Seleccione Azure AI Search en la lista de fuentes de conocimiento
    disponibles.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

3.  Haga clic en el **menú desplegable** junto a **Not connected** en la
    siguiente pantalla y seleccione **Create new connection**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image67.png)

4.  Ingrese los valores de **Endpoint url** y **Admin key** que
    guardamos en un bloc de notas en un ejercicio anterior y luego haga
    clic en **Create** para crear la conexión.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

5.  Una vez establecida la conexión, se muestra el índice disponible y
    ya seleccionado. Haga clic en **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

6.  El servicio de búsqueda con IA se ha añadido como fuente de
    conocimiento al agente y ahora se encuentra en estado **Ready**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

7.  Ahora, probemos el agente con la misma pregunta que probamos antes.

8.  En el panel Test, ingrese +++How many days can I avail Maternity
    leaves?+++ y haga clic en **Send.**

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

9.  Puede ver que la respuesta del agente ahora proviene del documento
    cargado en el servicio AI Search.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image72.png)

## Resumen

En este laboratorio, hemos aprendido a conectar el agente a un servicio
Azure AI Search como fuente de conocimiento y a probar el agente
basándonos en la fuente.
