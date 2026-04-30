# Lab 6 - Upgrading the hiring agent into an autonomous system

In this lab, you will dive deeper into **event triggers** - elevating
your agent system from reactive to **autonomous operation**. You'll
transform your agents from waiting for human input to proactively
responding to external events and taking intelligent action without
supervision.

Think of it as upgrading from agents that answer questions to agents
that anticipate needs and act independently. Through event triggers and
automated workflows, your **Hiring Agent** will **detect** incoming
resume **emails**, **process** attachments **automatically**, **store**
data in **Dataverse**, and **notify** your **HR recruitment team** via
**Microsoft Teams** - all while you focus on higher-value tasks.

**Objectives**

In this lab, you'll learn:

-    How event triggers enable autonomous agent behavior without user
    interaction

-    The differences between interactive and autonomous agents in Copilot
    Studio

-    How to create event triggers that automatically process email
    attachments and upload files to Dataverse

-    How to build agent flows that post adaptive cards to Teams channels
    for notifications

-    How to pass data between event triggers and agent flows for
    end-to-end automation

**What is an Event trigger?**

**Event triggers** let an agent *act* on *its* own when something
happens in another system - no user message required. When the
configured event fires - such as “new SharePoint item,” “new email,”
“Planner task assigned,” or even a time‑based recurrence, a connector
sends a trigger payload to your agent. The agent then follows your
instructions to decide which actions or topics to call.

**Interactive agent vs Autonomous agent - comparison**

Now that you know the difference between event triggers and topics
triggers, let's next learn about the difference between an interactive
agent vs an autonomous agent.

In Copilot Studio terms, "interactive" maps to agents that primarily
engage via **topics** in a chat or channel. "Autonomous" maps to agents
that also leverage **event triggers** to run without user input.

## Exercise 1: Automating candidate application emails

We're next going to add an event trigger to the **Hiring Agent** and
build an agent flow in the child **Application Intake Agent** to handle
further processing for autonomy.

**Use case scenario**

**As an** HR Recruiter

**I want to** be notified when an email with a resume arrives in my
Inbox and is automatically uploaded to Dataverse

**So that I can** stay notified of resumes sent by email for
applications automatically uploaded to Dataverse

We'll be achieving this using two techniques

1.  An event trigger for when the email arrives,

    - Check the contentType of the file equals PDF as the format type.

    - Extract the file and upload to Dataverse using actions through the
      Dataverse connector.

    - Then send a prompt to the agent for further processing by passing
      input parameters from the Dataverse actions.

2.  An agent flow will be added to the child **Application Intake
    Agent** which is invoked by the prompt in the event trigger.

    - Use the input parameters passed from the prompt of the event
      trigger in an adaptive card posted to a channel in Microsoft Teams
      to notify the HR Recruitment team. The adaptive card will have a
      link to the Dataverse row which can be viewed in the **Hiring
      Agent**.

### Task 1: Automate uploading resumes to Dataverse received by email

1.  In the Hiring Agent, scroll down in the **Overview tab** to
    the **Triggers** section and select **+ Add trigger**.

    ![](./media/image1.png)

3.  A list of triggers will appear. Select **When a new email arrives
    (V3)** and select **Next**.

    ![](./media/image2.png)

3.  Select **Continue** in the next screen.

    ![](./media/image3.png)

4.  We'll now see the **Trigger name** and the **Sign in** connection
    references for the apps listed. Rename the trigger name to the
    following:

    +++When a new email arrives from an applicant+++

    **NOTE:** Make sure you see a green check by each of the connection references for the apps listed. If you don't see a green check, sign in through the ellipsis (...) and select **+ New connection reference** to create a new connection reference.

    ![](./media/image4.png)

5.  The final step is to set the input properties of the trigger. Update
    the following properties to the following,

    | **Property**   | **How to Set**   |  **Details**  |
    |:--------|:----|:-------|
    |  **Include Attachments (Optional)**  |  Dropdown  | Yes   |
    |  **Subject Filter (Optional)**  | Type/Enter with keyboard   | +++Application+++   |
    |  Only with Attachments (Optional)  |  Dropdown  | Yes   |

6.  Select **Create trigger**.

    ![](./media/image5.png)

7.  Once created, a confirmation message will appear that the trigger
    has been added to the agent. Select **Close** and the trigger will
    be listed in the **Triggers** section.

    ![](./media/image6.png)

9.  We're now going to update the event trigger to add some more
    automation capabilities. Select the **ellipsis (...)** by the
    trigger and select **Edit in Power Automate**.

    ![](./media/image7.png)

9.  The trigger will then load as a flow in the Power Automate maker
    portal. It will open to the flow designer where we can add further
    logic and actions for more automation. The trigger will appear at
    the top, followed by **Sends a prompt to the specified copilot for
    processing** as the last action in the flow.

    ![](./media/image8.png)

    >[!Note] **Note:** If the **New designer** is not selected by default on the top right, please ensure to toggle it to **On**.
    >
    >![](./media/image132.png)

11. By default, the **When a new email arrives** trigger in Power
    Automate may process multiple emails together if several arrive at
    once, running the flow only once for the batch.

    To ensure the flow runs separately for each email, select the When a new email arrives node, select **Settings**.
    
    Enable the **Split On** setting in the **trigger’s settings** and select **@triggerOutputs()?['body/value']** in the **dropdown array** field.
    
    With **Split On** turned on and the array field set to **@triggerOutputs()?['body/value']**, the flow will run individually for each message, even if many arrive simultaneously.

    ![](./media/image9.png)

12. Let's next add some logic to check the file type of the attachment,
    we only want to upload .PDF file attachments and not images (these
    could come from email signatures). Select the **+** icon below the
    trigger and select **Control** under the **Built in tools** section.

    ![](./media/image10.png)

13. Select the **Condition** action.

    ![](./media/image11.png)

14. Now we will configure the condition to check if the file
    attachment’s type is .PDF. In the **Choose a value** field on the
    left, select the **lightning bolt icon**.

    ![](./media/image12.png)

15. In the **Search** field type +++content type+++ and select
    the **Attachments Content-Type** parameter from the trigger

    ![](./media/image13.png)

16. Let's pause here for a moment, you probably noticed that the **For
    each** action automatically appeared.

    ![](./media/image14.png)

    This action represents looping through each attachment in the email, since the **Attachments Content-Type** parameter is tied to each attachment.
    
    Underneath the hood, it's an array and that's why the For each action was automatically added when we selected the **Attachments Content-Type** parameter in the **Condition** action.


17. Next, in the other **Choose a value** field to the right in
    the **Condition** block, type +++application/pdf+++

    This will ensure that for each file attachment, it will check the file
extension format is .PDF.

    ![](./media/image15.png)

17. Now we'll configure the **True** path to extract the file from the
    email and upload it into the **Resume** Dataverse table.

    Add a new action below in the **True** path and search for +++html to text+++. Search for and select the **Html to text** action.
    
    >[!NOte] **Note:** The HTML to text action in Power Automate is used to convert HTML-formatted content into plain text. This is especially useful when you receive data (like emails, web content, or API responses) that contains HTML tags, and you want to extract just the readable text without any formatting or code.


    ![](./media/image16.png)

18. Next, we need to create a new connection reference for the **Html to
    text** action by selecting **Create new**.

    ![](./media/image17.png)

19. The action can now be configured. Let's add the **Body** parameter
    from the trigger. In the **Content** field, select the **lightning
    bolt icon** or **fx icon** to the right.

    ![](./media/image18.png)

20. In the **Dynamic content** tab, search for +++body+++ and select
    the **Body** parameter, followed by selecting **Add**.

    ![](./media/image19.png)

21. We've completed configuring this action so let's exit from the
    action by selecting the two angle brackets («) pointing to the left
    to collapse the panel.

    ![](./media/image20.png)

22. We'll add a new action by selecting the **+ icon** underneath
    the **Html to text** action which will load the panel to add
    actions. Search for +++**Dataverse add**+++.Select the **Add a new
    row** action.

    ![](./media/image21.png)

23. Rename the action by pasting +++Add a new Resume row+++ as the name
    in the upper left-hand corner of the properties panel,

    For the **Table name** parameter, search for +++res+++ and select
the **Resumes** table.

    ![](./media/image22.png)

24. Select the **Resume Title** field next and select the **fx icon** to
    the right.

    ![](./media/image23.png)

25. In the **Function tab**, enter the following expression that uses
    the item() function.

    +++item()?['name']+++

    Select **Add** to add the expression to the **Resume Title** parameter.

    ![](./media/image24.png)

    >[!Note] **Note on item() function:**
    >
    >- When you use an **Apply to each** action, Power Automate goes through
      each element in a collection (array).
    >
    >- It’s most often used inside actions like **Apply to each** (or **For
      each**), **Select**, or **Filter array**.

26. We still need to configure several more parameters, select **Show
    all**.

    ![](./media/image25.png)

28.  In the **Cover Letter** field, select the **fx icon** to the right.

    In the **Function tab**, enter the following expression.

    +++if(greater(length(body('Html_to_text')), 2000), substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))+++

    This expression checks if the text from the **Html to text** action is longer than 2000 characters, and if so, returns only the first 2000 characters; otherwise, it returns the full text.

    ![](./media/image26.png)

28. The expression will now be added to the **Cover Letter** field.

    ![](./media/image27.png)

29. For the **Source Email Address** field, select the **lightning bolt
    icon** and select the **From** parameter from the trigger as this
    contains the email address value.

    ![](./media/image28.png)

30. For the **Upload Date** field, select the **fx icon** to the right.
    In the **Function tab**, enter, +++utcNow()+++ and select **Add**.

    **Note:**  **What is the utcNow() function?**

    - The utcnow() function in Power Automate returns the current date and
  time in Coordinated Universal Time (UTC) in an ISO 8601 format,
  like: 2025-09-23T04:32:14Z

    ![](./media/image29.png)

31. We've now completed configuring the **Add a new Resume row** action
    so let's exit from the panel by collapsing it.

    ![](./media/image30.png)

33. We'll add a new action by selecting the **+ icon** underneath
    the **Add a new Resume row** action which will load the panel to add
    actions. Search for +++**Dataverse Upload**+++. Select the **Upload
    a file or an image** action.

    ![](./media/image31.png)

33. Rename the action by pasting +++Upload Resume File+++ as the name.

    ![](./media/image32.png)

34. Select the **Content name** field (remove the Untitled message if
    that is already available) next and select the **fx icon** to the
    right.

    In the Function tab, enter the following expression that uses the item () function. This gets the name property of the current item (the attachment file).
    
    +++item()?['name']+++


    ![](./media/image33.png)

35. For the **Table name** parameter, search for +++resumes+++ and
    select the **Resumes** table.

    ![](./media/image34.png)

36. Select the **Row ID** field next and select the **lightning bolt
    icon** to the right.

    Search for +++ID+++ and select the **Resume** parameter from the **Add a new row** Dataverse action as this contains the ID value of the row to upload the PDF file to.

    ![](./media/image35.png)

37. Select the **Column name** field and select the **Resume
    PDF** option.

    ![](./media/image36.png)

38. Select the **Content** field and select the **fx icon** to the
    right.

    In the Function tab, enter the following expression that uses the item () function. This gets the contentBytes property of the current item (the attachment file). contentBytes refers to the raw binary data of a file or attachment, encoded as a Base64 string.
    
    +++item()?['contentBytes']+++

    ![](./media/image37.png)

39. We've completed configuring this action so let's exit from the
    action by selecting the two angle brackets («) pointing to the left
    to collapse the panel.

    ![](./media/image38.png)

40. Next, select the **Sends a prompt to the specified copilot for
    processing**, then drag and drop this action to be below
    the **Upload Resume File** action in the **True** path of the
    condition.

    ![](./media/image39.png)

41. Select the **Sends a prompt to the specified copilot for
    processing** to configure it.

    ![](./media/image40.png)

42. In the **Body/message** field, select all of the field content and
    clear/delete it.

    ![](./media/image41.png)

43. Copy and paste the following text into the **Body/message** field
    and highlight the **RESUME ID PLACEHOLDER** and select the
    **lightning** icon.

    ```
    Send [ResumeId (text)] = "RESUME ID PLACEHOLDER" and [ResumeTitle (text_1)] = "RESUME TITLE PLACEHOLDER" and [ResumeNumber (text_2)]= "RESUME NUMBER PLACEHOLDER" to the Tool "Notify Teams Applicant channel" in the child agent "Application Intake Agent"
    ```
    
    ![](./media/image42.png)

44. Search for +++resume+++ and select the **Resume** parameter from
    the **Add a new row** *Dataverse* action as this contains
    the ID value of the Resume row created.

    ![](./media/image43.png)

45. Highlight the **RESUME TITLE PLACEHOLDER**. Select the **lightning bolt
    icon** to the right.

    Search for +++title+++ and select the **Resume Title** parameter from the **Add a new row Dataverse** action as this contains the resume title value of the Resume row created.

    ![](./media/image44.png)

46. Highlight the **RESUME NUMBER PLACEHOLDER**. Select the **lightning bolt
    icon** to the right.

    Search for +++resume number+++ and select the **Resume Number** parameter from the **Add a new row Dataverse** action as this contains the Resume Number value of the Resume row created.

    ![](./media/image45.png)

47. We've completed configuring this action and our agent flow. Now
    let's save our event trigger flow by selecting **Save**.

    ![](./media/image46.png)

48. We now need to edit the details of the agent flow, select **Back**
    once saved.

    ![](./media/image47.png)

49. Select **Edit** in the **Details** section and update
    the **Plan** to the **Copilot Studio** option. Select **Save**.

    ![](./media/image48.png)

50. A modal will appear to ask you to confirm to switch to Copilot
    Studio plan. Select **Confirm**.

    ![](./media/image49.png)

51. The plan is now updated to **Copilot Studio**. Select **Edit** as we
    need to publish the event trigger flow for our agent.

    ![](./media/image50.png)

52. Select **Publish**.

    ![](./media/image51.png)

    The event trigger flow is now Published.

    ![](./media/image52.png)

    Let's proceed with creating a new agent flow that will be invoked by the
child **Intake Application Agent**.

### Task 2 - Notify a Teams channel using an adaptive card

We're now going to create a new agent flow for the child **Intake
Application Agent** that uses the values passed by the event trigger, to
post an adaptive card to a Teams channel. This adaptive card will alert
the HR recruitment team about the PDF that was automatically uploaded so
that they can review it.

#### Task 2.1: Create channel in Teams

In this task, you will create a Team and Channel in MS Teams which will
be used later in this lab.

1.  Login to +++https://teams.microsoft.com+++

2.  Select the **New items drop down** and select **New team**.

    ![](./media/image53.png)

3.  Provide the below details and select Create.

    - Team name - +++HR Team+++

    - First channel name - +++Applicants+++

    ![](./media/image54.png)

4.  Select Skip in the next screen.

    ![](./media/image55.png)

5.  You have now created the new Team and Channel.

    ![](./media/image56.png)

#### Task 2.2: Create the agent flow

1.  Back in the Copilot Studio, in the **Hiring Agent** select
    the **Agents** tab and select the **Application Intake Agent**

    ![](./media/image57.png)

2.  Scroll down to **Tools** and select **+ Add**.

    ![](./media/image58.png)

3.  The **Add tool** modal will appear. Select **+ New tool**.

    ![](./media/image59.png)

4.  Select **Agent flow**.

    ![](./media/image60.png)

5.  The **agent flow designer** will next load. In the **When an agent
    calls the flow** trigger, select **+ Add an input**.

    ![](./media/image61.png)

6.  Select **Text** as the type of user input.

    ![](./media/image62.png)

7.  In the input text field, enter +++ResumeId+++ as the input parameter
    name.

    ![](./media/image63.png)

8.  Repeat the same steps for the below parameters.

    Text - +++ResumeTitle+++
    
    Text - +++ResumeNumber+++
    
    ![](./media/image64.png)
    
    ![](./media/image65.png)

9.  Now, you are going to add an adaptive card in the agent flow. We're
    now going to add another action to our agent flow that will post an
    adaptive card to a Teams channel.

    Select the **+ icon** below the trigger.

    ![](./media/image66.png)

10. Search for +++**Microsoft Teams post+++** and select the **Post card
    in a chat or channel** action.

    ![](./media/image67.png)

11. A connection reference to Microsoft Teams needs to be created with
    your signed in user account. Select **Sign in**.

    ![](./media/image68.png)

12. Select your user account and then select **Allow access**.

    ![](./media/image69.png)

13. Configure according to the following input parameters:

    | Parameter   |  How to Set  | Details   |
    |:------|:----|:------|
    |  **Post as**  |  Dropdown  |  Select the **Flow bot** option  |
    |  **Post in**  |  Dropdown  |   Select the **Channel** option |
    |  **Team**  |  Dropdown  |  Select **HR Team** option  |
    |   **Team** |  Dropdown  |  Select  **Applicants** channel   |


    ![](./media/image70.png)

14. Next, we'll configure the **Adaptive Card** field. Select
    the **Adaptive Card** field.

    ![](./media/image71.png)

15. Copy the below code and paste it into the Adaptive Card field.

    ```
    {
        "type": "AdaptiveCard",
        "speak": "New Resume Uploaded",
        "body": [
            {
                "inlines": [
                    {
                        "type": "TextRun",
                        "size": "Small",
                        "text": "Resume table updated",
                        "selectAction": {
                            "url": "https://adaptivecards.io",
                            "type": "Action.OpenUrl"
                        }
                    }
                ],
                "type": "RichTextBlock"
            },
            {
                "columns": [
                    {
                        "width": "auto",
                        "items": [
                            {
                                "type": "Icon",
                                "name": "DocumentArrowUp",
                                "color": "Accent"
                            }
                        ],
                        "type": "Column"
                    },
                    {
                        "width": "stretch",
                        "items": [
                            {
                                "size": "Large",
                                "text": "New Resume Uploaded",
                                "weight": "Bolder",
                                "wrap": true,
                                "type": "TextBlock"
                            }
                        ],
                        "verticalContentAlignment": "Center",
                        "spacing": "Small",
                        "type": "Column"
                    }
                ],
                "spacing": "Small",
                "type": "ColumnSet"
            },
            {
                "type": "Table",
                "targetWidth": "AtLeast:Narrow",
                "columns": [
                    {
                        "width": 1
                    },
                    {
                        "width": 2
                    }
                ],
                "rows": [
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Resume Number",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "RESUME NUMBER PLACEHOLDER",
                                        "wrap": true
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Name",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "RESUME NAME PLACEHOLDER",
                                        "wrap": true
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Status",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Waiting for Review",
                                        "wrap": true
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Due Date",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ]
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "May 21, 2023",
                                        "wrap": true
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Priority",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "ColumnSet",
                                        "columns": [
                                            {
                                                "type": "Column",
                                                "width": "auto",
                                                "items": [
                                                    {
                                                        "type": "Icon",
                                                        "name": "Flag",
                                                        "color": "Attention",
                                                        "size": "xSmall",
                                                        "horizontalAlignment": "Center"
                                                    }
                                                ]
                                            },
                                            {
                                                "type": "Column",
                                                "width": "stretch",
                                                "items": [
                                                    {
                                                        "color": "Attention",
                                                        "text": "Important",
                                                        "wrap": true,
                                                        "spacing": "Small",
                                                        "type": "TextBlock"
                                                    }
                                                ],
                                                "spacing": "Small"
                                            }
                                        ],
                                        "spacing": "Small"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    }
                ],
                "firstRowAsHeaders": false,
                "showGridLines": false
            },
            {
                "actions": [
                    {
                        "title": "View Resume",
                        "type": "Action.OpenUrl",
                        "url": "https://adaptivecards.io/"
                    }
                ],
                "type": "ActionSet",
                "targetWidth": "AtLeast:Narrow",
                "spacing": "ExtraLarge"
            }
        ],
        "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
        "version": "1.5"
    }
    
    ```

    ![](./media/image72.png)

16. We will now replace existing values in the JSON payload with actual
    values or dynamic content.

    First, let's update the **URL** for the **url property** within the **selectAction** property. This URL will be replaced with the URL of the **Resumes** system view in the **Hiring** Hub model-driven app. This will allow the Recruiter to select the action and be directed to the Resumes system view in the model-driven app.
    Highlight the **current URL** value and delete it.


    ![](./media/image73.png)

17. In the **Hiring Hub** model-driven app, navigate to
    the **Resumes** system view using the left hand side menu and copy
    the URL. Then **navigate back** to the **agent flow**, and **paste**
    the **copied URL** into the **url** property of the within
    the selectAction property.

    ![](./media/image74.png)

18. You should see the following where highlighted in Yellow is your
    environment details of the **Hiring Hub** model-driven app.

    |  Parameter  |  Value  |   Explanation |
    |:--------|:--------|:---------|
    |  Organization URI  |   GUID |  The Dataverse/Dynamics 365 environment organization URL  |
    |  appid  | GUID   |  To open a specific model-driven app, the query parameter of either appid or appname is used. In this case, the appid is used  |
    | viewid    | GUID   |  The query parameter which is the id of the view  |



    ![](./media/image75.png)

19. Next, we'll add dynamic content values for several properties. Let's
    start with the text that will display the Resume Number reference of
    the row that was created by the event trigger autonomously.

    Select the **panel** icon to load the action panel.

    ![](./media/image76.png)

20. Scroll down to the line where you see the text property for RESUME
    NUMBER PLACEHOLDER. Highlight the placeholder value and delete it.

    ![Delete placeholder](./media/image77.png)

21. Click in-between the double quotation marks and select
    the **lightning bolt icon** from the right.

    **Note:** Make sure that the Adaptive card code block is docked to the left pane of your screen.

    ![](./media/image78.png)

23. In the **Dynamic Content** tab select
    the **ResumeNumber** parameter.

    ![](./media/image79.png)

24. The **ResumeNumber** parameter will now be added as dynamic content
    to the text property.

    ![](./media/image80.png)

25. We'll repeat the same steps for the RESUME NAME PLACEHOLDER. Scroll
    down to the line where you see the text property for RESUME NAME
    PLACEHOLDER. Highlight the placeholder value and delete it. Click
    in-between the double quotation marks and select the select
    the **lightning bolt icon** from the right.

    ![](./media/image81.png)

26. In the **Dynamic Content** tab select the **ResumeTitle** parameter.

    ![](./media/image82.png)

27. The **ResumeTitle** parameter will now be added as dynamic content
    to the text property.

    ![](./media/image83.png)

28. We'll repeat the same steps for the **Due Date** value that
    represents when a recruiter should review the resume by. Scroll down
    to the line where you see the text property for May 21, 2023.

    ![Select Allow access](./media/image84.png)

29. Delete this date placeholder value and click in-between the double
    quotation marks and select the **fx icon** from the right.

    ![](./media/image85.png)

30. In the **Function** tab, enter the following expression and
    select **Add**.

    +++addDays(utcNow(), 3, 'MMM dd, yyyy')+++

    This expression utilizes two functions.

    addDays - Adds a specified number of days to a given date and returns the resulting date in string format
    
    utcNow - Returns the current date and time in Coordinated Universal Time (UTC) format as a string.

    For the utcNow value, we are formatting the date to be month and date,
    followed by the year.

    ![](./media/image86.png)

31. The expression will now be added to the text property.

    ![](./media/image87.png)

32. Lastly, we'll update the **URL** for the **url property** within
    the **actions** array property at the bottom of the JSON payload.
    This current placeholder URL will be replaced with the URL of the
    **Resume row** in the **Hiring Hub** model-driven app. This will
    allow the Recruiter to select the **Action.OpenURL** action of the
    adaptive card and be **directed** to the **Resume** in the
    model-driven app.

    ![](./media/image88.png)

32. In the **Hiring Hub** model-driven app, open a row in
    the **Resumes** system view using the left hand side menu. The
    resume row will load as a form in the model-driven app.

    Copy the URL for the Resume row.
    
    ![](./media/image89.png)
    
    ![](./media/image90.png)

33. Then navigate back to the agent flow, highlight the current
    placeholder URL value and **delete** it.

    ![](./media/image91.png)

34. Then **paste** the **copied URL** into the **url** property of the
    within the url property.

    ![](./media/image92.png)

35. You should see the following. Delete the GUID id value at the end.
    We'll replace this dynamic content - the **ResumeId** parameter.

    ![](./media/image93.png)

36. Select the **lightning bolt icon** from the right.

    In the **Dynamic Content** tab select the **ResumeId** parameter.

    ![](./media/image94.png)

37. The **ResumeId** will be added as dynamic content. The following
    highlighted in Yellow is your environment details of the **Hiring
    Hub** model-driven app.

    |  Parameter  | Value   |  Explanation  |
    |:-----|:-------|:--------|
    | Organization URI   | GUID   |  The Dataverse/Dynamics 365 environment organization URL  |
    |   appid |  GUID  |  To open a specific model-driven app, the query parameter of either appid or appname is used. In this case, the appid is used  |
    | id   |  GUID  |    The query parameter which is the id of the Resume row    |

    ![](./media/image95.png)

38. We've completed configuring the **Post card in a chat or
    channel** action 👏🏻 Exit from the action configuration panel by
    selecting the **x** icon.

    ![](./media/image96.png)

39. Finally, we'll configure the last action, **Respond to the
    agent** by sending a text back to the agent to end the processing.

    In the **Respond to the agent** action, select **+Add an output**.

    ![](./media/image97.png)

40. Select **Text** as the type of output.

    ![](./media/image98.png)

41. Enter the following details

    - Name - +++EndConversation+++

    - Value - +++Finished+++

    ![](./media/image99.png)

42. We've now completed configuring the agent flow. Select **Save
    draft** to save the agent flow. A confirmation message will appear
    once saved.

    ![](./media/image100.png)

43. Before publishing the agent flow, we need to update the details for
    the agent flow. Select the **Overview** tab and select **Edit**.

    ![](./media/image101.png)

44. Enter the Name as +++Notify Teams Applicant channel+++ and select
    the Refresh icon under Description to update it using AI.

    ![](./media/image102.png)

45. Once the Description is populated, select **Save** to save the
    updated details for the agent flow.

    ![](./media/image103.png)

46. Navigate back to the **Designer** tab and select **Publish** to
    publish the agent flow.

    ![](./media/image104.png)

47. A confirmation message will appear once published.

    ![](./media/image105.png)

48. The agent flow now needs to be added as a tool in the **Application
    Intake Agent**. Navigate back to the **Hiring Agent** and select
    the **Agents** tab, then select the **Application Intake Agent**.

    ![](./media/image106.png)

49. In the **Details** section of the agent, we'll update
    the **Description** field. Copy the following and paste and the end
    of the description text.

    +++and also notifies the Teams Applicant channel+++

    Select **Save**.

    ![](./media/image107.png)

50. Next, we'll add the agent flow as a tool. Scroll down to
    the **tools** section and select **+ Add**.

    ![](./media/image108.png)

51. Select the **Flow** tab and choose the agent flow created
    earlier, **Notify Teams Applicant Channel**.

    ![](./media/image109.png)

52. Select **Add and configure** next.

    ![](./media/image110.png)

53. In the **Inputs** section, the three inputs we configured earlier in
    the agent flow are visible. By default, the **Fill
    using** configuration is set to **Dynamically fill with AI**. We'll
    keep this setting as-is as the prompt from the event trigger will
    contain the parameter values that AI will extract.

    ![](./media/image111.png)

54. Now that the tool has been added to the **Application Intake
    Agent**, the instructions of the agent needs to be updated. Select
    the **back arrow**.

    ![](./media/image112.png)

55. Select the **Application Intake Agent** in the **Agents** tab of
    the **Hiring Agent**.

    ![](./media/image113.png)

56. In the **Instructions** field, enter a new line
    after **Post-Upload** instructions. Copy and paste the following
    instructions.

    ```
    Process for Resume Upload via Email
    1. When you receive a message, **Send [ResumeId (text)] = "1680265f-5793-f011-b41b-7c1e525be9f7" and [ResumeTitle (text_1)] = "TAYLOR TESTPERSON (FICTITIOUS).pdf" and [ResumeNumber (text_2)]= "R01026" to the Tool "Notify Teams Applicant channel"** in the child agent "Application Intake Agent", call [AGENT FLOW PLACEHOLDER]
    ```
    ![](./media/image114.png)

57. Highlight the \[AGENT FLOW PLACEHOLDER\] text.

    ![](./media/image115.png)

58. Enter the forward slash character, /, and select the **Notify Teams
    Applicant Channel** tool.

    ![](./media/image116.png)

59. The agent flow will now be invoked by the **Application Intake
    Agent** as per the instructions, after the last action (**Sends a
    prompt to the specified copilot for processing**) in the event
    trigger sends the prompt that contains the parameter values back to
    the agent.

    Select **Save** to save the updated instructions for the **Application
Intake Agent**.

    ![](./media/image117.png)

60. The instructions will now be updated once the agent has been saved.

    ![](./media/image118.png)

61. We now need to **Publish** the **Hiring Agent**.
    Select **Publish** on the upper right, and in the **Publish this
    agent modal** that appears select **Publish**.

    ![](./media/image119.png)

    ![](./media/image120.png)

62. Once published, a confirmation message will appear that the agent
    has been published.

    ![](./media/image121.png)

    We can now test the agent!

## Exercise 2: Test event trigger

In this exercise, you will test the event trigger that is created in
this lab.

1.  To execute the event trigger, an email needs to be sent with a
    Resume pdf file. **From your mailbox** (not of the tenant credential provided here. Use mail id of your choice. You will send an email from your mailbox to the tenant mail id.), **compose a new email** message.


    |  Email Component  |  Details  |
    |:--------|:---------|
    |  To recipient  |  +++@lab.CloudCredential(M365).AdministrativeUsername+++  |
    | File attachment   |  Upload the TAYLOR TESTPERSON (FICTITIOUS) file (from **C:\LabFiles\LabFiles**   |
    |  Subject  | +++Job Application+++   |
    |  Body  |  Copy and paste the following below as the body of the email  |
    
    ```
    Dear Hiring Manager,
    
    I am writing to express my interest in the Senior Power Platform Engineer position at your organization. With over nine years of experience delivering secure and scalable solutions on Microsoft cloud platforms, I am confident in my ability to contribute effectively to your team.
    
    In my most recent role as Lead Power Platform Engineer, I developed an automated resume-intake pipeline, reducing manual triage and improving searchability. I have delivered HR case management applications, introduced solution-aware flows, and implemented PR checks to enhance deployment lead times. My expertise includes Power Apps, Power Automate, Power Pages, Dataverse, and a range of Microsoft 365 services, as well as integration with Graph/REST APIs and Azure Functions.
    
    Previously, I developed Teams approvals with adaptive cards, cutting approval times to the same day, and created robust error-handling frameworks. My background also includes migrating legacy workflows to Power Automate and building self-service portals adopted by hundreds of employees.
    
    I hold a B.Sc. in Computer Science and am certified as a Power Platform Developer (PL-400) and Solution Architect (PL-600). I am also passionate about mentoring and have volunteered with local maker groups.
    
    Please find my CV attached for your consideration. I would welcome the opportunity to discuss how my skills and experience align with your needs.
    
    Thank you for your time and consideration.
    
    Kind regards,
    Taylor Testperson
    
    ```

2.  **Send** the email once composed from your mail box.

    ![](./media/image122.png)

3.  In +++https://make.powerautomate.com/+++, for the event trigger flow, (select **Flows** -> **When a new email arrives from an applicant**) select the **Refresh** icon to view the flow run that **succeeded** for the sent email.

    ![](./media/image123.png)

4.  Back in Copilot Studio in the Hiring Agent select the **Activity**
    tab. The **Activity** tab will load which will display all the
    activities of the **Hiring Agent**. There will be an activity with
    the name value of **Automated** that has a status of **Complete**.
    This activity represents the event trigger and the agent flow that
    was invoked.

    ![](./media/image124.png)

5.  Select the activity, and select the event trigger in the activity
    map. On the right hand side panel, notice how the input parameters
    in the prompt contain the Resume Id, Resume Title and Resume
    Number parameter values from the **Dataverse** row that was created.
    This was from the dynamic content values configured earlier in
    **Automate uploading resumes to Dataverse received by email**.

    ![](./media/image125.png)

6.  Navigate back to the **Hiring Hub** model-driven app and in
    the **Resumes system view**, select **Refresh** to refresh the view.
    The newly created row for the resume that was sent by email will now
    be listed as it was created through the event trigger.

    ![](./media/image126.png)

7.  Navigate back to Copilot Studio and select the **Notify Teams
    Applicant Channel** agent flow within the **Application Intake
    Agent** in the activity map. On the right hand side panel, notice
    how the inputs have values from the Dataverse row. This was from the
    prompt sent by the last action (**Sends a prompt to the specified
    copilot for processing**) in the event trigger that contains the
    parameter values from the newly created Dataverse row. This is how
    we can pass parameter values from event triggers to agent flows.

    ![](./media/image127.png)

8.  Finally, let's take a look at the adaptive card posted to the
    channel in **Microsoft Teams**. In the channel, we'll see the
    adaptive card that displays the information about the newly created
    Resume row in Dataverse. Hover over the hyperlink at the start of
    the adaptive card, notice how the URL is the Resumes system view URL
    that we configured earlier in the JSON payload of the adaptive card.

    ![](./media/image128.png)

9.  Select the hyperlink, and you'll be directed to the Resumes system
    view in the **Hiring Hub** model-driven app on your browser.

    ![](./media/image129.png)

10. Navigate back to the adaptive card posted to the channel in
    Microsoft Teams. This time, hover over **View Resume** which is
    the Action.OpenURL action of the adaptive card. Notice how the URL
    is the Resumes row that we configured earlier in the JSON payload of
    the adaptive card.

    ![](./media/image130.png)

11. Select the action, and you'll be directed to the Resume row form in
    the Hiring Hub model-driven app on your browser.

    ![](./media/image131.png)

## Exercise 3: Test, measure, and improve AI agents

As AI agents take on critical roles in business processes, the need for
reliable, repeatable testing becomes essential. Agent evaluation lets
you generate tests that simulate real-world scenarios for your agent.
These tests cover more questions faster than manual, case-by-case
testing. Then, you can measure the accuracy, relevancy, and quality of
answers to the questions the agent is asked, based on the information
the agent can access. By using the results from the test set, you can
optimize your agent's behavior and validate that your agent meets your
business and quality requirements.

In this exercise, you will learn how to systematically test and evaluate an
AI agent using Copilot Studio’s built-in evaluation and analytics
capabilities. You will create an automated test set that simulates
real-world user scenarios, measure the quality and accuracy of agent
responses, and analyze performance data to identify gaps and improvement
opportunities. By the end of the lab, you will be able to validate that
your agent meets business, reliability, and quality standards before
production use.

### Task 1: Create a test set to evaluate your agent

Before deploying an AI agent into real business workflows, it is
critical to validate how well it responds to realistic user questions.
Manual testing is time-consuming and often misses edge cases. In this
task, you will use Copilot Studio’s agent evaluation capabilities to
automatically generate a test set that simulates real-world scenarios.
You will run these tests against your agent, review pass and fail
outcomes, and identify gaps in accuracy, relevance, or behavior that
need improvement.

1.  From the Copilot Studio, select the **Hiring agent**.

    ![](./media/image133.png)

2.  From the top menu bar, select **Evaluation**. Select **Create a test
    set**.

    ![](./media/image134.png)

3.  There are few options to create the test set. Select **Generate 10
    questions** in this case.

    ![](./media/image135.png)

4.  **Review** the test set and then **Save** the test set.

    ![](./media/image136.png)

5.  Now, click on **Evaluate** to evaluate the agent.

    ![](./media/image137.png)

6.  Select your tenant id and click on **Run**.

    ![](./media/image138.png)

7.  Wait till the execution completes.

    ![](./media/image139.png)

8.  Once the evaluation is complete, click on it to view the details.

    ![](./media/image140.png)

9.  Go through each question and see why it has failed and which ones
    have passed. This will help you enhance your agent as required.

    ![](./media/image141.png)

### Task 2: Gain insights with agent analytics

Once an agent is evaluated and actively used, ongoing monitoring is
essential to ensure consistent performance and reliability at scale. In
this task, you will explore the Analytics capabilities in Copilot Studio
to gain insights into agent usage, execution trends, and component
utilization. You will learn how analytics data helps identify
performance bottlenecks, understand user interaction patterns, and guide
continuous optimization of your agent over time.

1.  From the top menu bar, select **Analytics.**

    ![](./media/image142.png)

2.  When there are a greater number of executions and as the agent gets
    used more and more, the traffic increases, and you can find the AI
    Summary in the Analytics tab.

    ![](./media/image143.png)

3.  The **Overview** section gives an overall picture about the runs,
    and credits.

    ![](./media/image144.png)

4.  The Run outcomes gives the average duration trends.

    ![](./media/image145.png)

5.  Scroll down and under the Use section, you can find the usage of
    triggers, tools and knowledge sources.

    ![](./media/image146.png)

6.  Each of these helps you to gauge the usage of each component of the
    agent and upgrade, enhance or correct the agent functionalities
    appropriately.

In this exercise, you implemented automated evaluation and analytics to
assess the quality and reliability of an AI agent. You generated a test
set to simulate realistic user interactions, ran evaluations to measure
response accuracy and relevance, and reviewed pass/fail results to
identify areas for improvement.

You also explored agent analytics to understand usage patterns,
execution trends, and component utilization across triggers, tools, and
knowledge sources. Together, these capabilities enable you to move
beyond manual testing and adopt a scalable, data-driven approach to
agent validation. This lab demonstrates how automated testing and
analytics help ensure your agents are trustworthy, performant, and ready
for real-world business scenarios.

## Summary

In this lab,

-    You've created an event trigger that passes Dataverse parameter
    values to an agent flow.

-    Built an agent flow: consumes the Dataverse parameter values to post
    an adaptive card to a channel in Microsoft Teams to alert the HR
    recruitment team.

-  Updated child agent instructions: to invoke the flow once the event
    trigger has completed.

-    This enables the **Hiring Agent** to work autonomously whenever
    resumes are received as email attachments and notify the HR
    recruitment team for manual review.
