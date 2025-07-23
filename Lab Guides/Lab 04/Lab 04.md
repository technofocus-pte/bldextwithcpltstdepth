# Lab 04 - Integrate an agent with the Dynamics 365 Customer Service app and implement automated case escalation to the live agent

## Objective

This lab details the steps to escalate a conversation to a live agent
from the agents.

>[!Alert] **Important:** This lab can be executed only if the Dynamics
365 trial has been enabled as per **Lab 02 - Configure the Dynamics 365
Customer Service**

## Exercise 1: Configure the Dynamics 365 Customer Service workspace

### Task 1: Configure Omnichannel Power Virtual Agent Extension

1.  Open the link,
    +++https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++ and click on **Get it now** in the Omnichannel Power Virtual Agent Extension page.

    ![](./media/image1.png)

2.  Sign in with the tenant credentials from the **Resources** tab.

    ![](./media/image2.png)

3.  Click on **Get it now**.

    ![](./media/image3.png)

4.  Select the **CustomerService Trial** under **Select an
    environment**, select the check boxes and click on **Install**.

    ![](./media/image4.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

## Task 2: Configure search settings in the Power Platform admin center

1.  Login to +++https://admin.powerplatform.microsoft.com/+++ using
    your tenant details. Select **Manage** from the left pane and then
    select **CustomerService Trial** environment from the list of
    environments.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  Select **Settings** from the top pane.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  Select **Product** -\> **Features**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  Toggle **Dataverse Search** and **Single table search** option
    to **ON** and select **Save**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

## Exercise 2: Create an agent

1.  From the Copilot Studio home page,
    +++https://copilotstudio.microsoft.com+++, select the **CustomerService Trial** Environment from the top right.

    ![](./media/image10.png)

2.  Select **Agents** from the left pane. Click on the **+ New
    Agent** to create a new agent.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  In the Type your message text area, type +++**You are a customer service agent who helps in identifying stores nearby.**+++ And hit **send**.

    ![](./media/image12.png)

4.  The agent might suggest a **name** for the Agent being created.
    Either accept it or suggest a new name.

5.  Type the message +++**Maintain a polite tone**+++ next and
    hit **send**.

    ![](./media/image13.png)

6.  Click on **Create**.

    ![](./media/image14.png)

7.  The created agent opens up with a message, **Your agent is ready**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## Exercise 3: Connect the copilot to Dynamics 365 Customer Service and configure the Escalate topic

### Task 1: Configure the Escalate topic

We are focusing here on showcasing the escalation to live agent concept.
So, we will directly work towards it without creating any other new
topics.

1.  Select the **Topics** tab and then select the **System** tab. Select
    the **Escalate** topic.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  Select the message node of the topic and replace the existing
    content with, +++You will be transferred to a live agent shortly+++

    ![](./media/image17.png)

3.  Click on the + symbol to add a node next to the Message node.

4.  Select **Topic management** -\> **Transfer conversation**.

    ![](./media/image18.png)

5.  Give a message +++The customer wants to talk to a live agent+++ in
    the Transfer conversation node.

    ![ ](./media/image19.png)

6.  **Save** the Topic.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  **Publish** the agent.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### Task 2: Connect the copilot to Dynamics 365 Customer Service

1.  Once published, from the copilot page top right, click
    on **Settings**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  Select **Security**, and **Authentication** under Security.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  Select the **No authentication** option and then click on **Save**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  Select **Save** in the confirmation dialog box.

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  Close the **Settings** pane.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

6.  Click on **Channels** (If the Channels is not visible, click on the
    +1 to view the **Channels** option)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  Select **Dynamics 365 Customer Service** from the Customer
    engagement hub pane.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  On the Dynamics 365 Customer Service page, click on **Connect**.

    ![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  Once you get a **successfully connected** message, click
    on **Close**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## Exercise 4: Create workstream and channel in Dynamics 365 admin center

### Task 1: Manage a user in Omnichannel for Customer Service

1.  Login to +++https://admin.powerplatform.microsoft.com+++ using your admin tenant credentials. Select **Manage** from the left pane. Select **CustomerService Trial** environment **under Environments**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  Click on the **url value** under **Environment URL**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  Select **Customer Service workspace** from the header bar.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  This opens the **Apps** page. Select **Copilot Service admin
    center** from it.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/img2.png)


5.  This opens up the **Dynamics 365 Customer Service admin
    center** page.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/img3.png)


### Task 2: Configure workstream

1.  From the admin center page, select **Workstreams** under **Customer
    support** from the left pane and then select the **+ New
    workstream** option.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/img4.png)

2.  Select Inbound

    ![](./media/image37.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

3.  Fill in the below details, scroll down and click on **Create**.

    - Name - +++**New Workstream**+++

    - Owner – **MOD Administrator** (Selected by default)

    - Type – **Messaging**

    - Channel – **Chat**

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image39.png)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  Once the workstream is created, click on **Set up chat** to set up
    the chat channel.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  In the **Live chat setup – Channel details** screen, fill in the
    below details.

    - Name - +++**Chat Channel**+++

    - Language – **English - United States**

    ![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  Scroll down and click **Next**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  Accept the defaults in the next 2 pages until you reach the Chat
    widget screen. In the Live chat setup – Chat widget screen, provide
    the name as +++**Store Locator Assistant**+++, accept the other
    defaults and click on **Next**.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  In the **Live chat setup – Behaviors** screen, accept the defaults
    and click on **Next**.

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  In the **Live chat setup – User features** screen, toggle **File
    attachment** and **Voice and video calls** options to **off** and
    click on **Next**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. Accept the default value in the Notification screen and click
    **Next**.

11. In the **Live chat setup – Review and finish** screen,
    select **Create channel**.

    ![](./media/image47.png)

12. **Copy** the value of the widget that appears in the **Live chat
    setup – Success** screen and **save** it in a notepad to add it to a
    webpage in the upcoming exercises. Then, click on **Done** to
    complete the configuration.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### Task 3: Add the agent to the workstream

1.  Back in the **New Workstream** page, scroll down and click on **+ Add bot** in the **Add an AI agent** section.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image49.png)


2.  From the list of bots on the Add a bot screen, select the **Store
    Locator Assistant** (the name might differ based on the agent that you created earlier) agent and click on **Connect**.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image50.png)


3.  Ensure that the bot is added to the workstream as in the screenshot below.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image51.png)


4.  From the left pane, select **AI Agents**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  Ensure that the **Store locator** agent is connected.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## Exercise 5: Create a webpage and test the escalation to agent

1.  Login to +++https://make.powerpages.microsoft.com/+++ using your
    tenant admin credentials.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  Ensure that you are in **CustomerService Trial** environment.

3.  Click on **Get started**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  Click on Skip in the **Tell us about yourself** page.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  Scroll down in the next page and click on **Start with a
    template** option to start creating the site with a template.

    ![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  Select a template and click on **Choose this template**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  In the Give your site a name textbox, enter the name as +++**Contoso
    Store assistant**+++, accept the other defaults and click
    on **Done**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  Once the site is created, click on **Edit**.

    ![](./media/image60.png)

9.  Click on **Edit site header** in the **Company name** title.

    ![](./media/image61.png)

10. In the **Edit site header** pane, provide the **Site title** as
    +++**Contoso Store assistant**+++ and close the dialog.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. Click on **Edit code** in the top right corner of the page.

    ![](./media/image63.png)

12. Click on **Open Visual Studio Code**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

13. Click **Allow**. **Login** using your tenant credentials if
    required.

    ![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

14. The Home page of the web page opens up in the Visual Studio Code.

    ![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

15. Scroll to the end of the file. Add the **script** copied while
    creating the workstream, after the last line of this file.

    ![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

16. Save the file, close the Visual Studio Code tab and return to the
    Power pages. Click on **Sync**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. Please wait for few minutes before proceeding to the next step.
    
18. Once the Sync is completed, select **Preview** -\> **Desktop.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

19. Your web page opens in a new tab. Find the **Store Locator
    Assistant** embedded to the page at the bottom right of the web
    page. **Click** on it.

    ![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

20. Enter +++Talk to agent+++.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/img5.png)

21. From the Customer Service admin page, click on **Customer Service
    admin center** and select the app **Customer Service
    workspace** from it.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

22. In the Customer Service workspace page, you will get a **chat
    request**. **Accept** it.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

23. Once accepted, the chat screen opens up with the message that we had
    given in the Escalate topic. We can also add any other information
    provided by the user here to the live agent.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

24. Simulate the chat between the live agent and the customer if you
    wish to see how it works and then ends.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image77.png)

## Summary

In this lab, we have learnt to

- Build an agent from the Copilot Studio and configure the Escalate
  topic.

- Publish the agent to Dynamics 365 workspace and integrate it in a web
  page. 
