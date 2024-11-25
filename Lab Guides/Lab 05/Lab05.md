# Lab 05 - Integrate an agent with the Dynamics 365 Customer Service app and implement automated case escalation to the live agent

## Exercise 1: Configure the Dynamics 365 Customer Service workspace

### Task 1: Configure Omnichannel Power Virtual Agent Extension

1.  Open the link,
    +++https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++
    and click on Get it now in the Omnichannel Power Virtual Agent
    Extension page.

    ![](./media/image1.png)

    ![](./media/image2.png)

    ![](./media/image3.png)

2.  Select the **CustomerService Trial** under **Select an
    environment**, select the check boxes and click on **Install**.

    ![](./media/image4.png)

3.  In the Dynamics 365 apps page, click on the entries that shows
    **Update available**, **select** the **check box** to agree to the
    terms and click on **Update**.

Make sure to do this for **all** the entries with **Update available**
as the Status.

    ![](./media/image5.png)

    ![](./media/image6.png)

### Task 2: Configure search settings in the Power Platform admin center

1.  Login to +++<https://admin.powerplatform.microsoft.com/>+++ using
    your tenant details. Select **Environments** -\> **CustomerService
    Trial**.

    ![](./media/image7.png)

2.  Select the drop down next to **Resource** (in the top pane) and
    select **Dynamics 365 apps**.

    ![](./media/image8.png)

3.  Make sure that **Omnichannel for Customer Service** is
    **Installed**.

    ![](./media/image9.png)

4.  Navigate back to the **Environments -\> CustomerService** **Trial**
    page in the admin center. Select **Settings** from the top pane.

    ![](./media/image10.png)

5.  Select **Product** -\> **Features**.

    ![](./media/image11.png)

6.  Toggle **Dataverse Search** and **Single table search** option to
    **ON.**

    ![](./media/image12.png)

    Scroll down and click on the **Save** button at the bottom right.

    ![](./media/image13.png)

## Exercise 2: Create an agent

1.  From the Copilot Studio home page,
    +++https://copilotstudio.microsoft.com+++, select the
    **CustomerService Trial** Environment from the top right.

    ![](./media/image14.png)

2.  Select **Agents** from the left pane. Click on the **+ New Agent**
    to create a new agent.

    ![](./media/image15.png)

3.  In the Type your message text area, type **+++You are a customer
    service agent who helps in identifying stores nearby.**+++ And hit
    **send**.

    ![](./media/image16.png)

4.  Type the message +++**Maintain a polite tone**+++ next and hit
    **send.**

    ![](./media/image17.png)

5.  Click on **Create**.

    ![](./media/image18.png)

6.  The created agent opens up with a message, **Your agent is ready**.

    ![](./media/image19.png)

## Exercise 3: Connect the copilot to Dynamics 365 Customer Service and configure the Escalate topic

### Task 1: Configure the Escalate topic

We are focusing here on showcasing the escalation to live agent concept.
So, we will directly work towards it without creating any other new
topics.

1.  Select the **Topics** tab and then select the **System** tab. Select
    the **Escalate** topic.

    ![](./media/image20.png)

2.  Select the message node of the topic and replace the existing
    content with, +++**You will be transferred to a live agent
    shortly**+++

    ![](./media/image21.png)

3.  Click on the + symbol to add a node next to the Message node.

4.  Select **Topic management** -\> **Transfer conversation**.

    ![](./media/image22.png)

5.  Give a message +++The customer wants to talk to a live agent+++ in the
    Transfer conversation node.

    ![ ](./media/image23.png)

6.  **Save** the Topic.

    ![](./media/image24.png)

7.  **Publish** the agent.

    ![](./media/image25.png)

### Task 2: Connect the copilot to Dynamics 365 Customer Service

1.  Once published, from the copilot page top right, click on
    **Settings**.

    ![](./media/image26.png)

2.  Select **Security**, and **Authentication** under Security.

    ![](./media/image27.png)

3.  Select the **No authentication** option and then click on **Save**.

    ![](./media/image28.png)

4.  Select **Save** in the confirmation dialog box.

    ![](./media/image29.png)

5.  Close the **Settings** pane.

6.  Click on **Channels** (If the Channels is not visible, click on the
    +1 to view the **Channels** option)

    ![](./media/image30.png)

7.  Select **Dynamics 365 Customer Service** from the Customer
    engagement hub pane.

    ![](./media/image31.png)

8.  On the Dynamics 365 Customer Service page, click on **Connect**.

    ![](./media/image32.png)

9.  Once you get a **successfully connected** message, click on
    **Close**.

    ![](./media/image33.png)

## Exercise 4: Create workstream and channel in Dynamics 365 admin center

### Task 1: Manage a user in Omnichannel for Customer Service

1.  Login to +++https://admin.powerplatform.microsoft.com+++ using your
    admin tenant credentials and select **Environments** from the left
    tab. The **CustomerService Trial** will be listed here. **Select**
    it.

    ![](./media/image34.png)

2.  Click on the **url value** under **Environment URL**.

    ![](./media/image35.png)

3.  This opens up the **Dynamics 365 Customer Service admin center**
    page.

    ![](./media/image36.png)

4.  In **Dynamics 365 Customer Service admin center**, in the site map,
    select **User management** under **Customer support** group.

5.  On the **User management** page, select **Manage** next
    to **Users**.

    ![](./media/image37.png)

6.  Click the dropdown next to **Enabled Users** and select
    **Omnichannel Users**.

    ![](./media/image38.png)

    >[!Alert] **Important:** If you are not able to see the **Omnichannel Users**
option, it is due to some back-end changes that is happening recently.
If you are not able to complete this step, then you will not be able to
complete the Exercises 7 and 8. Please omit them.

7.  On the **Omnichannel Users** page, select a user **MOD
    Administrator** in the list.

    ![](./media/image39.png)

8.  On the **MOD Administrator** page, select the **Omnichannel** tab.

    ![](./media/image40.png)

9.  Specify the following in the user page.

    | Setting   |   Value |
    |:---------|:---------|
    |   Capacity |  100|
    |   Default Presence | available    |
    ![](./media/image41.png)

10. Select **Save and close**.

    ![](./media/image42.png)

### Task 2: Configure workstream 

1.  From the admin center page, select **Workstreams** under **Customer
    support** from the left pane and then select the **+ New
    workstream** option.

    ![](./media/image43.png)

2.  Fill in the below details, scroll down and click on **Create**.

    - Name - +++**New Workstream**+++

    - Owner – **MOD Administrator** (Selected by default)

    - Type – **Messaging**

    - Channel – **Chat**

    ![](./media/image44.png)

    ![](./media/image45.png)

3.  Once the workstream is created, click on **Set up chat** to set up
    the chat channel.

    ![](./media/image46.png)

4.  In the **Live chat setup – Channel details** screen, fill in the
    below details and click on **Next**.

    - Name - +++**Chat Channel**+++

    - Language – **United States**

    ![](./media/image47.png)

5.  In the Live chat setup – Chat widget screen, provide the name as
    +++**Store Locator Assistant**+++, accept the other defaults and
    click on **Next**.

    ![](./media/image48.png)

6.  In the **Live chat setup – Behaviors** screen, accept the defaults
    and click on **Next**.

    ![](./media/image49.png)

7.  In the **Live chat setup – User features** screen, toggle **File
    attachment** and **Voice and video calls** options to **off** and
    click on **Next**.

    ![](./media/image50.png)

8.  In the **Live chat setup – Review and finish** screen, select
    **Create channel**.

    ![](./media/image51.png)

9.  **Copy** the widget that appears in the **Live chat setup –
    Success** screen and **save** it in a notepad to add it to a webpage
    in the upcoming exercises. Then, click on **Done** to complete the
    configuration.

    ![](./media/image52.png)

### Task 3: Add the copilot to the workstream

1.  Back in the **New Workstream** page, scroll down and click on **+
    Add bot** in the Bot section.

    ![](./media/image53.png)

2.  From the list of copilots on the Add bot screen, select the **Store
    Locator Assistant** copilot and click on **Connect**.

    ![](./media/image54.png)

3.  Ensure that the bot is added to the workstream as in the screenshot
    below.

    ![](./media/image55.png)

4.  From the left pane, select **Bots**.

    ![](./media/image56.png)

5.  Ensure that the Real Estate Booking Service copilot is connected.

    ![](./media/image57.png)

## Exercise 5: Create a webpage and test the escalation to agent

1.  Login to +++https://make.powerpages.microsoft.com/+++ using your
    tenant admin credentials.

    ![](./media/image58.png)

2.  Ensure that you are in **CustomerService Trial** environment.

3.  Click on **Get started**.

    ![](./media/image59.png)

4.  Click on Skip in the **Tell us about yourself** page.

    ![](./media/image60.png)

5.  Scroll down in the next page and click on **Start with a template**
    option to start creating the site with a template.

    ![](./media/image61.png)

6.  Select a template and click on **Choose this template**.

    ![](./media/image62.png)

7.  In the Give your site a name textbox, enter the name as +++**Contoso
    Store assistant**+++, accept the other defaults and click on
    **Done**.

    ![](./media/image63.png)

8.  Once the site is created, click on **Edit site header** in the
    **Company name** title.

    ![](./media/image64.png)

9.  In the **Edit site header** pane, provide the **Site title** as
    +++**Contoso Store assistant**+++.

    ![](./media/image65.png)

10. Click on Edit code in the top right corner of the page.

    ![](./media/image66.png)

11. Click on **Open Visual Studio Code**.

    ![](./media/image67.png)

12. Click **Allow**.

    ![](./media/image68.png)

13. The Home page of the web page opens up in the Visual Studio Code.

    ![](./media/image69.png)

14. Scroll to the end of the file. Add the **script** copied while
    creating the workstream, after the last line of this file.

    ![](./media/image70.png)

15. Save the file, close the Visual Studio Code tab and return to the
    Power pages. Click on **Sync**.

    ![](./media/image71.png)

16. Once the Sync is completed, select **Preview** -\> **Desktop.**

    ![](./media/image72.png)

17. Your web page opens in a new tab. Find the **Store Locator
    Assistant** embedded to the page at the bottom right of the web
    page. **Click** on it.

    ![](./media/image73.png)

18. Enter +++Talk to agent+++.

    ![](./media/image74.png)

19. From the Customer Service admin page, click on **Customer Service
    admin center** and select the app **Customer Service workspace**
    from it.

    ![](./media/image75.png)

    ![](./media/image76.png)

20. In the Customer Service workspace page, you will get a **chat
    request**. **Accept** it.

    ![](./media/image77.png)

21. Once accepted, the chat screen opens up with the message that we had
    given in the Escalate topic. We can also add any other information
    provided by the user here to the live agent.

    ![](./media/image78.png)

22. Simulate the chat between the live agent and the customer if you
    wish to see how it works and then ends.

    ![](./media/image79.png)

    ![](./media/image80.png)

**Summary**

In this lab, we have learnt to

- Build an agent from the Copilot Studio and configure the Escalate
  topic.

- Publish the agent to Dynamics 365 workspace and integrate it in a web
  page.

- Configure and test the escalation to a live agent.


