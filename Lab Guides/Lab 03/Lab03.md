# Lab 03- Using a connection to Azure OpenAI on your data for generative answers

**Lab duration** – 40 minutes

**Objective:**

In this lab, we will learn how to use the Azure Open AI connection in
the copilot to generate answers.

## Exercise 0: Register the required Resource providers

1.  Login to +++<u><https://portal.azure.com/>+++</u>, using the Azure
    account credentials from the Resources tab of the VM.

2.  On **Welcome to Microsoft Azure** dialog box, click on **Maybe
    later** button.

    ![](./media/image1.png
)

3.  Type in +++**Subscriptions**+++ in the search bar and select
    **Subscriptions**.

    ![](./media/image2.png
)

4.  Click on your assigned **subscription**.

    ![](./media/image3.png
)

5.  From the left menu, click on the **Resource Providers** under
    Settings.

    ![](./media/image4.png
)

6.  In the search bar, type +++**Microsoft.Storage**+++, select
    **Microsoft.Storage** from the list below. Click on the three dots
    and select **Register**.

    ![](./media/image5.png
)

    ![](./media/image6.png
)

7.  A notification stating **Successfully registered resource provider**
    is obtained once the registration is successful.

8.  Repeat steps 6 and 7 to register the following Resource providers.

    - **Microsoft.Security**

    - **Microsoft.Search**

    - **Microsoft.CognitiveServices**

    - **Microsoft.Sql**

    - **Microsoft.Web**

    - **Microsoft.ManagedIdentity**

## Exercise 1: Create Azure OpenAI resource

1.  From the Azure portal home page, click on **Azure portal menu**
    represented by three horizontal bars on the left side of the
    Microsoft Azure command bar as shown in the below image.

    ![](./media/image7.png
)

2.  Navigate and click on **+ Create a resource**.

    ![](./media/image8.png
)

3.  On **Create a resource** page, in the **Search services and
    marketplace** search bar, type **Azure OpenAI**, then press the
    **Enter** button.

    ![](./media/image9.png
)

4.  In the Marketplace page, navigate to the Azure OpenAI section, click
    on the Create V chevron button, then click on **Azure OpenAI** as
    shown in the image. (In case, you clicked on the Azure **OpenAI
    section**, then click on the **Create** button on the **Azure OpenAI
    page**).

    ![](./media/image10.png
)

5.  In the **Create Azure OpenAI** window, under the **Basics** tab,
    enter the following details and click on the **Next** button.

    1.  **Subscription**: Select the assigned subscription

    2.  **Resource group**: click on Create new\> enter **AOAI-RGXX**(XX
        can be a unique number)

    3.  **Region**: Select **East US**

    4.  **Name**: Azure-openai-testXX (XX can be a unique number) (here,
        we entered **Azure-open-test29**)

    5.  **Pricing tier**: Select **Standard S0**

    ![](./media/image11.png
)

    ![](./media/image12.png
)

6.  In the **Network** tab, leave all the radio buttons in the default
    state, and click on the **Next** button.

    ![](./media/image13.png
)

7.  In the **Tags** tab, leave all the fields in the default state, and
    click on the **Next** button.

    ![](./media/image14.png
)

8.  In the **Review+submit** tab, once the Validation is Passed, click
    on the **Create** button.

    ![](./media/image15.png
)

9.  Wait for the deployment to complete. The deployment will take around
    10-15 minutes.

    ![](./media/image16.png
)

10. On **Microsoft.CognitiveServicesOpenAI** window, after the
    deployment is completed, click on the **Go to resource** button.

    ![](./media/image17.png
)

## Exercise 2- Create an Azure Storage Account and Azure cognitive Search by using the portal

### **Task 1: Cognitive Services Usages Reader for the Azure OpenAI resource**

1.  From the home page of Azure portal(+++https://portal.azure.com+++),
    type in +++**Subscriptions**+++ in the search bar and select
    **Subscriptions**.

    ![](./media/image2.png
)

2.  Click on your assigned **subscription**.

    ![](./media/image3.png
)

3.  From the left menu, click on the **Access control(IAM).**

    ![](./media/image18.png")

4.  On the Access control(IAM) page, Click +**Add** and select **Add
    role assignments.**

    ![](./media/image19.png")

5.  Type the **Cognitive Services Usages Reader** in the search box and
    select it. Click **Next**

    ![](./media/image20.png)

6.  In the **Add role assignment** tab, select Assign access to User
    group or service principal. Under Members, click **+Select members**

    ![](./media/image21.png)

7.  On the Select members tab , search your Azure OpenAI subscription
    and click **Select.**

    ![](./media/image22.png)

8.  In the **Add role assignment** page, Click **Review + Assign**, you
    will get a notification once the role assignment is complete.

    ![](./media/image23.png
)

    ![](./media/image24.png
)

9.  You will see a notification – added as Cognitive Services Usage
    Reader for Azure Pass-Sponsorship.

    ![](./media/image25.png
)

10. In Azure subscription page from the left menu, click on the **Access
    control(IAM).**

    ![](./media/image18.png")


11. On the Access control(IAM) page, Click +**Add** and select **Add
    role assignments.**

    ![](./media/image19.png")

12. Type the [**Cognitive Services
    Contributor**](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/role-based-access-control#cognitive-services-contributor)
    in the search box and select it. Click **Next**.

    ![](./media/image26.png />

13. In the **Add role assignment** tab, select Assign access to User
    group or service principal. Under Members, click **+Select members**

    ![](./media/image27.png />

14. On the Select members tab , search your Azure OpenAI subscription
    and click **Select.**

    ![](./media/image22.png
)

15. In the **Add role assignment** page, Click **Review + Assign**, you
    will get a notification once the role assignment is complete.

    ![](./media/image28.png />

    ![](./media/image29.png />

16. You will see a notification – added as Cognitive Services Usage
    Reader for Azure Pass-Sponsorship.

    ![](./media/image30.png")

17. Click on **Home**, search for +++**Azure OpenAI**+++ in the search
    bar and select **Azure OpenAI.**

    ![](./media/image31.png
)

18. Click on your **Azure OpenAI** service.

    ![](./media/image32.png
)

19. From the left menu, click on the **Access control(IAM).**

    ![](./media/image33.png
)

21. Type the [**Cognitive Services
    Contributor**](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/role-based-access-control#cognitive-services-contributor)
    in the search box and select it. Click **Next**.

    ![](./media/image35.png
)

22. In the **Add role assignment** tab, select Assign access to User
    group or service principal. Under Members, click **+Select members**

    ![](./media/image27.png
)

23. On the Select members tab , search your Azure OpenAI subscription
    and click **Select.**

    ![](./media/image22.png
)

24. In the **Add role assignment** page, Click **Review + Assign**, you
    will get a notification once the role assignment is complete.

    ![](./media/image28.png
)

    ![](./media/image29.png
)

25. You will see a notification – added as Cognitive Services Usage
    Reader for Azure Pass-Sponsorship.

    ![](./media/image36.png
)

### **Task 2: Create an Azure Storage Account by using the portal**

1.  Sign in to the +++**<https://portal.azure.com/>+++**

2.  Click on the **Portal Menu**, then select **+ Create a resource**

    ![](./media/image37.png)

3.  In the **Create a resource** window search box, type +++**Storage
    account**+++ and then click on the **storage account**.

    ![](./media/image38.png)

4.  In the **Marketplace** page, click on the **Storage account**
    section.

    ![](./media/image39.png
)

5.  In the **Storage account** window, click on the **Create** button.

    ![](./media/image40.png
)

6.  On **Create a storage account** window, under the **Basics** tab,
    enter the below details to create a storage account and then click
    on **Review + create**

- 

    | **Subscription** | Select your Azure OpenAI subscription |
    |----|----|
    | **Resource group** | Select AOAI-RGXX |
    | **Storage account name** | **azureopenaistorageXX**(XX can be a unique number) (here, we entered **azureopenaistorage39**) |
    | **Region** | **East US** |
    | **Performance** | **Standard: **Recommended for most scenarios (general-purpose v2 account) |
    | **Redundancy** | **Locally-redundant storage (LRS)** |

    ![](./media/image41.png")

7.  On the **Review** tab, click on the **Create** button.

    ![](./media/image42.png")

8.  This new Azure Storage account is now set up to host data for an
    Azure Data Lake. Click on the **Go to resource** button.

    ![](./media/image43.png)

9.  After the account has been deployed, you will find options related
    to Azure Data Lake in the Overview page. In the left-side navigation
    pane, navigate to **Data storage** section, then click on
    **Containers**.

    ![](./media/image44.png")

10. On **azureopenaistorageXX \| Containers** page, click on
    **+Container.**

    ![](./media/image45.png />

11. On the New container pane that appear on the right side, enter the
    container **Name** as +++ **source**+++ and click on **Create**
    button.

    ![](./media/image46.png />

12. On **azureopenaistorageXX \| Containers** page, select **source**
    container.

    ![](./media/image47.png />

13. On **source** container page, click on **Upload** button.

    ![](./media/image48.png />

14. In the **Upload blob** pane, click on **Browse for file**, navigate
    to **C:\Labfiles** location and select **TF-AzureOpenAI.pdf**, then
    click on the **Open** button.

    ![](./media/image49.png)

    ![](./media/image50.png)

15. In **Upload blob** pane, click on the **Upload** button.

    ![](./media/image51.png)

16. You will see a notification – **Successfully uploaded blob** when
    the uploaded is succeeded.

    ![](./media/image52.png")

    ![](./media/image53.png />

### **Task 3: Create an Azure Cognitive Search service in the portal**

1.  From the **azureopenaistorageXX \| Containers** page, click on
    **Home** to go back to Azure portal home page.

    ![](./media/image54.png)

2.  In Azure portal home page, click on **+ Create Resource**.

    ![](./media/image55.png")

3.  In the **Create a resource** page search bar, type **Azure AI
    Search** and click on the appeared **azure ai search**.

    ![](./media/image56.png)

4.  Click on **azure ai search** section.

    ![](./media/image57.png")

5.  In the **Azure AI Search** page, click on the **Create** button.

    ![](./media/image58.png)

6.  On the **Create a search service** page, provide the following
    information and click on **Review+create** button.

    | **Field**          | **Description**                                |
    |--------------------|------------------------------------------------|
    | **Subscription**   | Select your Azure OpenAI subscription          |
    | **Resource group** | Select your Resource group                     |
    | **Region**         | EastUS                                         |
    | **Name**           | **mysearchserviceXX** (XXcan be unique number) |
    | **Pricing Tier**   | Click on change Price Tire\>select **Basic**   |

    ![](./media/image59.png")

    ![](./media/image60.png />

    ![](./media/image61.png")

7.  Once the Validation is passed, click on the **Create** button.

    ![](./media/image62.png")

    ![](./media/image63.png)

8.  After the deployment is completed, click on the **Go to resource**
    button.

    ![](./media/image64.png")

9.  In the **mysearchserviceXX** Overview page. In the left-side
    navigation pane, under **Settings** section, select **Semantic
    ranker**.

    ![](./media/image65.png />

10. On the **Semantic ranker** tab**,** select **Free** tile and click
    on the **Select plan.**

    ![](./media/image66.png")

11. You will see a notification -**Successfully updated semantic ranker
    to free plan**

    ![](./media/image67.png />

## Exercise-3: Add your data using Azure OpenAI Studio

### **Task 1: Deploy gpt-3-turbo and embedded models in Azure AI Studio**

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL:
    +++https://oai.azure.com/+++ then
    press the **Enter** button. Login using your **Azure** credentials.

    ![](./media/image68.png
)

> **Note**: If you are directed to the **Azure OpenAI Studio** home
> page, then skip steps from \#2 to \#4, else continue.

2.  In the **Microsoft Azure** window, enter your **Sign-in**
    credentials, and click on the **Next** button.

    ![](./media/image69.png
)

3.  Then, enter the password and click on the **Sign in** button**.**

    ![](./media/image70.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

    ![](./media/image71.png)

5.  On the **Welcome to Azure OpenAI Studio** dialog box, under the
    **Subscription** field, enter the subscription assigned to you, and
    in the **Resource** field, select the existing AOAI Resource name,
    and then click on the **Use resource** button.

    ![](./media/image72.png
)

6.  Within few minutes **Azure OpenAI Studio** page will appear.

    ![](./media/image73.png
)

7.  On the **Azure OpenAI Studio** homepage, click on **Create new
    deployment** button.

    ![](./media/image74.png
)

8.  In the **Deployments** page, click on +**Create new deployment**.

    ![](./media/image75.png
)

9.  Enter the below details and click on the **Create** button. 

    -	Model – Select **gpt-35-turbo**
    
    -	Deployment type – **Standard**
    
    -	Deployment name - +++**gpt-35-turbo**+++

    ![](./media/image76.png) 

You will see a notification – **Successfully Created deployment** when the deployment is succeeded. (You can also view the notification by clicking on the bell icon beside **Azure AI \| Azure AI Studio)**.

    ![](./media/image77.png
)

## Exercise 4: Create a Copilot app with custom data

### **Task 1: Create a chatbot with custom data**

1.  Select **Chat** to open the Chat playground.

    ![](./media/image78.png
)

2.  In **Chat playground pane** , under the Assistant setup select **Add
    your data** and then select the **+Add data source** .

    ![](./media/image79.png)

3.  In the **Add data** page, under **Select or add data source** enter
    the following details and select **Next.**

    | **Select data source** | **Select Azure Blob Storage(preview)** |
    |----|----|
    | **Subscription** | Select your Azure OpenAI subscription |
    | **Select Azure Blob storage resource** | Select **azureopenaistorageXX** |
    | **Select storage container** | Select **source** |
    | **Select Azure AI Search resource** | Select **mysearchserviceXX** |
    | **Enter the index name** | **copilot-index** |
    | **Indexer schedule** | Once |

    ![](./media/image80.png")

***Note**: In case, you encounter an error – **Can‘t manage CORS on this
resource. Please select another storage resource**, then syn your VM
time, as mentioned in Lab \#1, Task \#1.*

4.  In the **Add data** page, on the **Data management** tab select
    **Keyword** under **Search type,** select the chunk size as
    **1024(default).**Then, click on **Next.**

    ![](./media/image81.png />

5.  In **Review and Finish** pane, review the details that you’ve
    entered, and click on **Save and close** button**.**

    ![](./media/image82.png")

6.  The data will be added in your Chat Playground. This will take
    approximately 4-5 minutes.

    ![](./media/image83.png
)

    ![](./media/image84.png")

7.  In Azure AI Studio **Chat playground**, click on the V chevron
    button beside **Deploy to**, then navigate and click on **A new
    copilot in Copilot Studio(preview)**

***Note:** In case, you did not see **Deploy to** button on your VM,
then use Ctrl+- or Ctrl+minus keyboard shortcut to zoom out and decrease
the font size.*

    ![](./media/image85.png")

8.  **Deploy to a copilot in Copilot Studio(preview)** dialog box
    appears, then click on the **Continue in Copilot Studio** button.

    ![](./media/image86.png />

9.  you are prompted to **Choose your country/region**, then click on
    the dropdown and select your region, then click on **Start free
    trail** button.

    ![](./media/image87.png />

    ![](./media/image88.png")

10. In the **Create a copilot pane,** enter **Copilot name** as
    **TF-Copilot** and click on **Create** button.

    ![](./media/image89.png")

11. Wait for the deployment to complete. The deployment will take around
    **15-16** minutes.

    ![](./media/image90.png
)

12. In the **New features in Copilot Studio** dialog box, click on the
    **Skip** button.

    ![](./media/image91.png />

    ![](./media/image92.png")

13. In the Copilot Studio, select **Topics** under the **Overview .**

    ![](./media/image93.png />

15. Select **Edit** under the **Data sources.**

    ![](./media/image95.png")

16. In the **Create generative answers properties** pane, under Azure
    OpenAI Services on your data select **Connection properties** .

    ![](./media/image96.png")

17. Under the **Data sources**, in the **Connect data** field enter
    +++**content+++** and click on the **plus(+)** symbol.

    ![](./media/image97.png)

18. In your **Copilot Studio \| TF-Copilot** window, navigate to the
    **Test copilot** pane enter the following text and click on the
    **Submit icon** as shown in the below image.

**TextCopy**

**<span class="mark">How do I get access to Azure OpenAI?</span>**

    ![](./media/image98.png />

19. Similarly, paste the following text in the text box and click on the
    **Send** icon.


    +++**What is the expiry date of GPT-35-Turbo version 0301 and GPT-4 version 0314?**+++

    ![](./media/image99.png")

    ![](./media/image100.png")

### **Task 2: Delete the deployed models**

1.  In Azure OpenAI Studio, on the left pane, under the **Management**
    section, click on **Deployments**.

    ![](./media/image101.png
)

2.  Select **gpt-35-turbo0301** deployment name and click on **Delete
    deployment**.

    ![](./media/image102.png")

3.  In the **Confirm delete** dialog box, click on the **Delete**
    button. You will see the notification – **Successfully Deleted
    deployment** (In case, you did not see the notification, then click
    on the bell icon beside **Azure AI \| Azure AI Studio**).

    ![](./media/image103.png
)

    ![](./media/image104.png")

4.  In Azure OpenAI Studio, on the left pane, under the **Management**
    section, click on **Deployments**.

    ![](./media/image101.png")

5.  Select **text-embedding-ada-002** deployment name and click on
    **Delete deployment**.

    ![](./media/image105.png")

6.  In the **Confirm delete** dialog box, click on the **Delete**
    button. You will see the notification – **Successfully Deleted
    deployment** (In case, you did not see the notification, then click
    on the bell icon beside **Cognitive Services \| Azure OpenAI
    Studio**).

    ![](./media/image106.png")

### **Task 3: Delete the Azure storage account, Azure cognitive search and Azure Web app**

1.  To delete the storage account, navigate to Azure portal home page,
    type **Resource groups** in the Azure portal search bar, navigate
    and click on **Resource groups** under **Services**.

    ![](./media/image107.png />

2.  Click on the assigned resource group.

    ![](./media/image108.png")

3.  Carefully select storage account, Azure Cognitive Search, Azure web
    app, CosmosDB that you’ve created.

**Note**: Don’t select Azure OpenAI service.

    ![](./media/image109.png")

4.  In the Resource group page, navigate to
    <span class="mark">the</span> command bar and click on **Delete**.

    **Important Note**: Don’t click on **Delete resource group**. If you
    don’t see the **Delete** option in the command bar, then click on the
    horizontal ellipsis.

    ![](./media/image110.png)

5.  In the **Delete Resources** pane that appears on the right side,
    enter the **delete** and click on **Delete** button.

    ![](./media/image111.png")

6.  On **Delete confirmation** dialog box, click on D**elete** button.

    ![](./media/image112.png")

7.  Click on the bell icon, you’ll see the notification – **Executed
    delete command on 4 selected items.**

    ![](./media/image113.png")

> **Summary**
>
> You've created a storage account, container, and Azure cognitive
> service in Azure portal, then you've deployed gpt-3-turbo model in
> Azure AI Studio. You’ve added data in Chat Playground and tested the
> Assistant setup by sending queries in a chat session. Then, you've
> launched a new app and started conversation with the chatbot. You've
> deleted the gpt-3-turbo model, Azure storage account, cognitive search
> service, and the new web app to effectively and efficiently manage the
> Azure OpenAI resources.
