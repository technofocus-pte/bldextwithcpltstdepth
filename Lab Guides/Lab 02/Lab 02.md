# Lab - Create a Knowledge Assistant agent for HR in Copilot Studio that leverages Azure AI Search

## Objective:

A large enterprise wants to reduce the time employees spend searching
for HR-related information (policies, benefits, leave guidelines, etc.)
spread across SharePoint, PDFs, internal wikis, and documents.

To overcome this issue, in this lab, you will build an **Knowledge
assistant** **agent** in **Copilot Studio** that uses **Azure AI
Search**, to index and semantically search across enterprise HR
documents.

## Exercise 1: Create an Azure AI Search resource

1.  Login to Azure portal at +++https://portal.azure.com/+++ with your credentials.
From the Home page of the Azure portal, select **Azure AI Foundry.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  In the **AI Foundry page**, select **AI Search** from the left pane
    and then select **+ Create**.

    ![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image2.png)

3.  Enter the below details and select **Review + create**.

    - Subscription – Select your **assigned subscription**

    - Resource group – Select your **assigned Resource group**
    (**ResourceGroup1**)

    - Storage account name – +++**searchleaves**+++

    - Location – Select your **assigned region**

    ![A screenshot of a search service AI-generated content may be
incorrect.](./media/image3.png)

4.  Once the validation passes, select **Create**.

    ![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image4.png)

5.  The deployment takes a few minutes. Select **Go to resource** once
    the search service is created.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  From the **Overview** page, copy the Url value and save it in a
    notepad to be used in a future exercise.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  Select **Keys** under **Settings** from the left pane. Copy the
    **Primary admin key** and save it in a notepad for using it in the
    upcoming exercises.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  Select **Identity** under **Settings** from the left pane.

    ![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image8.png)

9.  Toggle the Status to **On** under **System assigned** and then click
    on **Save**.

    ![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image9.png)

10. Select **Yes** in the **Enable system assigned managed identity**
    confirmation dialog.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image10.png)

## Exercise 2: Create a Storage account

1.  Login to Azure portal at +++https://portal.azure.com/+++ and login
    with your credentials. Select Storage accounts from the Home screen.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  Select **+ Create** to create a new Storage account.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

3.  Enter the below details, accept the default values in the other
    fields and click on **Review + create**.

    - Subscription – Select your **assigned subscription**

    - Resource group – Select your **assigned Resource group**
    (**ResourceGroup1**)

    - Region – Select your **assigned region**

    - Storage account name – +++**leavepolicystorage**+++

    - Primary service – Select **Azure Blob Storage or Azure Data Lake
    Storage Gen 2**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image13.png)

4.  Once the validation passes, click on **Create**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  Once the resource creation succeeds, click on **Go to resource**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  Select **Containers** under **Data storage**. Select **+
    Container**, enter the name as +++**document**+++ and click on
    **Create** to create the container.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

7.  Select the created container **document** to upload the leave policy
    document into it.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  Click on **Upload** and then select **Browse for files**.

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image19.png)

9.  Select the **LeavePolicy.docx** from **C:\Labfiles** and then click
    on **Upload**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

10. Navigate to the **leavepolicystorage** Storage account (Select
    **Storageaccounts** from the **Home page** of the Azure portal and
    select **leavepolicystorage**) and select **Access Control (IAM)**
    from the left pane. Select **Add -\> Add role assignment**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

11. Search for +++**Storage Blob Data Reader**+++, select it and click
    on **Next**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

12. Click on **+Select members**, search for and select your **user
    id**, select your **user id** that gets listed and then click on
    **Select**. This adds the Storage Blob Data Reader role to your user
    id.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

13. Select **Managed identity** and then select **+ Select members**.
    Select **Search service** under **Managed identity** and select the
    **searchleaves** search service that gets listed.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

14. Click on **Select** to select the search service.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

15. Back in the Add role assignment screen, click on **Review +
    assign**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

16. Select **Review + assign** again in the next screen.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

17. Proceed to the next step once the roles are added.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

In this exercise, we have created a Storage account and added the
document and required Role permissions to it.

## Exercise 3: Create an Azure OpenAI Service and deploy a model 

1.  From the Azure portal Home page, search for select +++Azure
    OpenAI++.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

2.  Select **+ Create**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

3.  Enter the below details and select **Next**.

    - Subscription – Select your **assigned subscription**

    - Resource group – Select your **assigned Resource group**
    (**ResourceGroup1**)

    - Region – Select your **assigned region**

    - Name – +++**openaiservice52374668**+++

    - Pricing tier – Select **Standard**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  Select **Next** in the next 2 screens select **Create** in the
    **Review + submit** screen.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  Click on **Go to resource** once the service is created.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

6.  Select **Access control (IAM)** from the left pane, select **Add -\>
    Add role assignment**.

    ![](./media/image36.png)

7.  Search for +++**Cognitive Services OpenAI User**+++, select the role
    and click on **Next**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

8.  Select **+ Select members**, search for your **user id**, select it
    and click on **Select**.

    ![](./media/image38.png)

9.  Back in the **Add role assignment** screen, select **Managed
    identity**. Then select **+ Select members**. In the **Select
    managed identities** screen, select **Search service** under
    **Managed identity** and select the **seachleaves** service.

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image39.png)

10. Once selected, click on **Select**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

11. Select Review + assign in the next 2 screens.

    ![](./media/image41.png)

12. Wait for a **success** message on the role additions before
    proceeding with the next tasks.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

13. From the **Overview** page of the Azure OpenAI Service resource,
    select **Go to Azure AI Foundry portal** to open the Azure OpenAI
    Service there and deploy a model.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

14. Select **Deployments** from the left pane.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

15. Select **+ Deploy model** -\> **From base models**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

16. Search for +++**text-embedding**+++, select
    **text-embedding-3-large** and then select **Confirm**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

17. Select **Deploy** in the Deploy text-embedding-3-large.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

18. The model gets deployed and the screen is loaded with the deployment
    details.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

## Exercise 4: Create a vector index

1.  Go to the **searchleaves** AI Search service resource. Select
    **Import and vectorize data**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  Select the **Azure Blob Storage** option.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  Select the **RAG** option in the **What scenarios are you
    targeting?** screen.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  Enter the below details, accept the other values as default and
    click **Next**.

    - Subscription – Select your **assigned subscription**

    - Storage account- Select **leavepolicystorage**

    - Blob-container – Select **document**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  In the Vectorize your text screen, the subscription and the Azure
    OpenAI resource details are pre-populated. Enter the below details
    and click **Next**.

    - Model deployment – Select **text-embedding-3-large**

    - Authentication type – Select **System assigned identity**

    - Select the checkbox to acknowledge the cost alert of Azure OpenAI.

6.  Select Next in the **Vectorize and enrich your images** screen since
    we are not dealing with images here and select **Next** in the
    **Advanced settings** screen as well.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

7.  Select **Create** in the **Review + create** screen.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

8.  Click on **Close** in the success dialog box.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

## Exercise 5: Create a knowledge assistant agent

1.  Login to +++https://copilotstudio.microsoft.com+++ using your login
    credentials.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

2.  Select **Create** from the left pane.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

3.  Select **+ New agent** to create a new agent.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

4.  Enter +++You are a Knowledge assistant agent for HR who will answer
    questions related to leaves and leave policies to the employees.+++
    and select **Send**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image60.png)

5.  The copilot suggests a name to the agent. Click on **Create** to
    create the agent.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

6.  Once the agent is created, in the Test pane, enter +++How many days
    can I avail Maternity leaves?+++ and click **Send.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

7.  It gives a generalized reply as in the screenshot below.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image64.png)

## Exercise 6: Add the Azure AI Search as a knowledge source

1.  From the **Overview** page of the agent, select **Add knowledge**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

2.  Select Azure AI Search from the list of knowledge sources available.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

3.  Click on the **drop down** next to **Not connected** in the next
    screen and select **Create new connection**.

    ![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image67.png)

4.  Enter the **Endpoint url** and the **Admin key** values which we
    saved to a notepad in a previous exercise and then click on
    **Create** to create the connection.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

5.  Once the connection is established, the available index is listed
    and already selected. Click on **Add**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

6.  The AI Search service is added as a knowledge source to the agent
    and is in **Ready** state now.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

7.  Now, let us test the agent with the same question we tried before.

8.  In the Test pane, enter +++How many days can I avail Maternity
    leaves?+++ and click **Send.**

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

9.  You can see that the response from the agent now is from the
    document uploaded in the AI Search service.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image72.png)

## Summary:

In this lab, we have learnt to connect the agent to a Azure AI Search
service as a knowledge source and test the agent based on the source.
