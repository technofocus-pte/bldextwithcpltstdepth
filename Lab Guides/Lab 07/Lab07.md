# **Lab 07_ Sending messages from a Copilot(classic) to a Teams channel**

**Lab duration** – 30 minutes

**Objective:**

In this lab, we will send message from a Copilot to a Teams channel by
invoking a flow.

## **Exercise 1: Add channel and Team in Microsoft Teams**

1.  Open **Microsoft Teams** from the VM and login using your tenant
    credentials if you have closed it already. Select **Teams** option.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  From the Teams, select **More options** and select **+ -\>**
    **Create team**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Name the team as +++**HR Team**+++, channel as +++**HR Experts**+++
    and select **Create**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Select **Skip** on ‘Add members to HR Team’ window.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  Select **Skip** on ‘Add members to the HR Experts channel’ window.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

## **Exercise 2: Enhance topic to handle complex queries by escalating to HR experts**

1.  From the Teams app, select the Copilot Studio app(Power Virtual
    Agents), select **Copilots** tab and open the **HR Support
    Copilot**.

> ![](./media/image6.png)
>
> **Note:** If Copilot Studio shortcut is not found, search for
> **Copilot Studio/Power Virtual Agents under Apps** and select
> **Open**)
>
> ![](./media/image7.png)

2.  Select **Topics** from left pane and return to the topic you created
    earlier(**Employee time off**) and go to the authoring canvas.

> ![A screenshot of a chat Description automatically
> generated](./media/image8.png)

3.  In the **Ask a question node**, add an option named **Extended
    leave**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  Under the Condition node of Extended leave, add a question node
    asking for a description for the issue and add the text +++**How
    would you describe the issue?***+++*

> ![](./media/image10.png)

5.  Select **User’s entire response** under Identity and save the
    description in a variable named +++**Description**+++.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image11.png)

6.  Select **Save**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  Add a node under the question and select **Call an action**. Select
    **Create a flow** which launches the Power Automate within the
    Copilot Studio in Teams.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

8.  Choose the **Power Virtual Agents Flow** Template option.

![](./media/image14.png)

![A screenshot of a computer Description automatically
generated](./media/image15.png)

9.  Add a **Text** input field by clicking on **+ Add an input** in the
    first step. Replace the Input by **Description**.

![A computer screen shot of a computer error Description automatically
generated](./media/image16.png)

10. Insert a **new step** and select **Add an action**.

![](./media/image17.png)

11. Select **Microsoft Teams** under **Choose an operation**.

![](./media/image18.png)

12. Select **Post message in a chat or channel**.

![](./media/image19.png)

13. Provide the below details:

- Post as – **User**

- Post in – **Channel**

- Team – **HR Team**

- Channel – **HR Experts**

- Message **– Description** from **Dynamic Content**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

14. Rename the flow as +++**Send a message to HR team**+++ and click on
    **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

15. Click on **Close** to close the Power Automate and return to the
    Authoring canvas.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

16. From the Authoring canvas, add a node – **call an action** -\>
    **Send a message to HR team**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

17. Add in the input as **Description**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

18. Add in a message node with the message, +++**We notified the expert.
    They’ll reach out shortly**+++.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

19. End the conversation \> End the survey.

![A screenshot of a chat Description automatically
generated](./media/image26.png)

20. Click on **Save** to save the topic.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

21. A success message of **Topic saved** is obtained.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

## **Exercise 3: Test your chatbot**

1.  Select Test your chatbot from the left pane.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

2.  Send a message +++**I need help with time off**+++ and select
    Extended leave to answer the chatbot.

![A screenshot of a chat Description automatically
generated](./media/image30.png)

3.  Describe a reason for your leave extension. Here, we have given it
    as +++**I need extended leave of one month for travelling**+++.

![A screenshot of a chat Description automatically
generated](./media/image31.png)

4.  The bot replies with “We notified an expert…..” message.

![A screenshot of a chatbot Description automatically
generated](./media/image32.png)

> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)

## **Exercise 4: Check the message in Teams.**

1.  Click on Teams from the left menu of the MS Teams app.

![](./media/image34.png)

2.  Select the **HR Experts** channel under the **HR Team** team. Notice
    that the message from the user to the bot has been sent here.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

## **Exercise 5: Publish your copilot – Teams**

1.  Go back to Microsoft Copilot Studio app. Select the chatbot **HR
    Support Copilot**.

2.  Select Publish from the left pane.

![A screenshot of a chat Description automatically
generated](./media/image36.png)

3.  Click on **Publish**.

![](./media/image37.png)

4.  Select Publish in the **Publish latest content?**

![A close-up of a computer screen Description automatically
generated](./media/image38.png)

5.  Success message is obtained as in the screenshot below. Click on the
    **Availability options**.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  The **Add to Contoso** option adds the bot to the specific team.

7.  **Show to my team mates and shared users** makes the bot to appear
    under the Built by colleagues section.

8.  **Show to everyone in the org** submits the request to the admin to
    get the bot listed under the **Built by org** section.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

**Summary:**

In this lab, we have learnt to post a message to the Teams channel from
the bot.
