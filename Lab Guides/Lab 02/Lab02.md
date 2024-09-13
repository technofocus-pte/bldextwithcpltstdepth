# Lab 02 - Enhancing the Real Estate copilot with Gen AI capabilities

**Lab duration** – 80 minutes

**Objective:**

Implement entities, slot filling and variables usage in the Copilot for
Real Estate app. Enhance the copilot created for the Real Estate app to
elevate the customer experience by implementing Generative AI.

## Exercise 1: Use entities to improve the copilot

Microsoft Copilot Studio uses entities to understand user intent. There
are many prebuilt entities included for commonly used information. You
can create custom entities for your specific purpose.

### Task 1: View prebuilt entities

1.  Select **Settings** in the top-right of the screen.

    ![](./media/image1.png)

2.  Select the **Entities** tab. You can see a list of pre-built
    entities.

    ![](./media/image2.png)

### Task 2: Create the property type entity

1.  Select **+ Add an entity** and select **+ New entity**.

    ![](./media/image3.png)

2.  Select the **Closed list** tile.

    ![](./media/image4.png)

3.  Enter the below details

    -    Name - +++**Property Type**+++
    -    **Enter item** under List items –
    -    +++**Apartment**+++ - Select **Add**

    ![](./media/image5.png)

4.  Enter +++**Condominium**+++ in the **Enter item** field and
    select **Add**.

5.  Enter +++**Duplex**+++ in the **Enter item** field and
    select **Add**.

    ![](./media/image6.png)

6.  Select **+ Synonyms** for **Apartment**, enter +++**Flat**+++, then
    select the **+** icon and select **Done**.

    ![](./media/image7.png)

7.  Select **+ Synonyms** for **House**, enter +++**Single-family
    home**+++, then select the **+** icon and select **Done**.

8.  Select **+ Synonyms** for **Condominium**,
    enter +++**Townhouse**+++, then select the **+** icon and
    select **Done**.

9.  Select **Save**.

    ![](./media/image8.png)

10. Select **Close**.

    ![](./media/image9.png)

### Task 3: Create number of bedrooms entity

1.  Select **+ Add an entity** and select **+ New entity**.

    ![](./media/image10.png)

2.  Select the **Regular expression (Regex)** tile.

    ![](./media/image11.png)

3.  Enter the below details and click on **Save**.

    - Name  - +++**Number of Bedrooms**+++ 
    
    - Pattern  - +++**\[1-5\]**+++ 

    ![](./media/image12.png)

4.  Select **Close**.

    ![](./media/image13.png)

5.  Close the **Settings** pane.

    ![](./media/image14.png)

### Task 4: Use entities

1.  Select the **Topics** tab. Select the **Book a Real Estate
    Showing** topic.

    ![](./media/image15.png)

2.  Select the **+** icon above the property question node and
    select **Ask a question**.

    ![](./media/image16.png)

3.  Fill in the below details.

    - **Enter a message** - +++What type of property do you want to see?+++
    
    - **Identify** – Select **Property Type**
    
    - Select **Select options for user** and check the **Display** option
      for all list values.

    ![](./media/image17.png)

4.  Select the variable in **Save user response as** and enter
    +++**PropertyType**+++ for **Variable name**

    ![](./media/image18.png)

5.  Select the the **+** icon below the new question node and
    select **Ask a question**.

6.  Enter the below details and click on **Save**.

    - **Enter a message** - +++How many bedrooms do you need?+++
    
    - **Identify -** Select **Number of Bedrooms**
    
    - **Save user response as** -
      Enter +++NumberofBedrooms+++ for **Variable name**

    ![](./media/image19.png)

## Exercise 2: Create Copilot actions

Microsoft Copilot Studio can access data in Microsoft Dataverse using
Power Automate cloud flows

### Task 1: Create Power Automate flow to retrieve a property

1.  Select the **Actions** tab from the top menu. Select **+ Add an
    action**.

    ![](./media/image20.png)

2.  Scroll down and select **Create a new flow**.

    ![](./media/image21.png)

3.  Sign in to Power Automate if prompted.

4.  Select **Run a flow from Copilot** in the top-left of the screen and
    enter +++**Get Property**+++ as the flow name.

    ![](./media/image22.png)

5.  Select the trigger step **Run a flow from Copilot** and select **+
    Add an input**.

    ![](./media/image23.png)

6.  Select **Text**.

    ![](./media/image24.png)

7.  Enter the below details

    - **Input** – +++Bedrooms+++
    
    - **Please enter your input** - +++Number of Bedrooms+++

    ![](./media/image25.png)

8.  Select the **+** icon between the two steps in the flow and
    select **Add an action**.

    ![](./media/image26.png)

9.  Enter +++**Dataverse**+++ in the **Search** field and select **See
    more** for the Dataverse connector.

    ![](./media/image27.png)

10. Select the **List rows** action.

    ![](./media/image28.png)

11. If prompted for authentication, select **OAuth** and select **Sign
    in**. Sign in using your tenant id if prompted.

    ![](./media/image29.png)

12. Select **Real Estate Properties** for table name.

13. Select **Show all**.

14. Enter +++contoso_bedrooms eq+++ in the **Filter Rows** field.

15. Use **Dynamic content** to select the **Bedrooms** parameter and
    select **Add**.

    ![](./media/image30.png)

16. Select the **Respond to Copilot** action and select **+ Add an
    output**.

    ![](./media/image31.png)

17. Select **Text**.

18. Enter the below details

    - **Enter a name** - +++PropertyId+++
    
    - **Enter a value to respond with** - select **Insert Expression** and
      enter the following expression:
      +++first(outputs('List_rows')?\['body/value'\])\['contoso_realestatepropertyid'\]+++

    ![](./media/image32.png)

19. Select **Add**.

    ![](./media/image33.png)

20. Select **+ Add an output**.

21. Select **Text**.

    - **Enter a name** - +++PropertyName+++ 
    
    - **Enter a value to respond with** - select **Insert Expression** and
      enter the following expression:
      +++first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]+++

    ![](./media/image34.png)

22. Select **Settings**. Ensure that **Asynchronous Response** is set
    to **Off**.

    ![](./media/image35.png)

23. Select **Save draft**.

    ![](./media/image36.png)

24. Once save, select **Publish**.

    ![](./media/image37.png)

25. Close the Power Automate tab.

### Task 2: Add a Copilot action for retrieving a property

1.  Back in the Copilot Studio page, select **Refresh**.

    ![](./media/image38.png)

2.  Select the **Get Property** flow.

    ![](./media/image39.png)

3.  Select **Next** in the **Choose an action** screen**.**.

    ![](./media/image40.png)

4.  Select **Next** in the **Review inputs and outputs** screen.

    ![](./media/image41.png)

5.  Select **Finish** in the **Review and finish** screen.

    ![](./media/image42.png)

6.  Select the **Topics** tab. And select the **Book a Real Estate
    Showing** topic.

    ![](./media/image43.png)

7.  Select the **+** icon below the **How many bedrooms do you need
    question?** node and select **Call an action**. Select the **Get
    Property** flow.

    ![](./media/image44.png)

8.  Select the **NumberofBedrooms** variable for the **Bedrooms** input
    parameter.

    ![](./media/image45.png)

9.  Select the **three dots** in the **Which property do you want to
    see?** question node and select **Delete**.

    ![](./media/image46.png)

10. Select the the **+** icon under the action node and select **Send a
    message**.

11. Fill in the below details

    - **Enter a message** - enter +++Property+++
    
    - Select the **Insert variable** icon and select
      the **PropertyName** variable.

    ![](./media/image47.png)

12. Select **Save**.

    ![](./media/image48.png)

13. Once saved, select **Publish** and select **Publish**.

    ![](./media/image49.png)

14. Click on Publish in the Publish confirmation dialog.

    ![](./media/image50.png)

### Task 3: Create Power Automate flow to make a booking

1.  Select the **Actions** tab and select **+ Add an action**.

    ![](./media/image51.png)

2.  Scroll down and select **Create a new flow**.

    ![](./media/image52.png)

3.  Select **Run a flow from Copilot** in the top-left of the screen and
    enter Create +++**Booking Request**+++ as the flow name.

    ![](./media/image53.png)

4.  Select the trigger step **Run a flow from Copilot** and select **+
    Add an input -\> Text**.

    ![](./media/image54.png)

    ![](./media/image55.png)

5.  Enter the below details

    - Input - +++**PropertyId**+++
    
    - Please enter your input **-** +++**Property**+++

6.  Select **+ Add an input -\> Text**

    - Input - +++**ViewerName**+++
    
    - Please enter your input **-** +++**Viewer Name**+++

7.  Select **+ Add an input -\>** **Text**.

    - Input - +++**ViewerEmail**+++
    
    - Please enter your input **-** +++**Viewer Email**+++

    ![](./media/image56.png)

8.  Select the **+** icon between the two steps in the flow and
    select **Add an action**.

    ![](./media/image57.png)

9.  Enter +++**Dataverse**+++ in the **Search** field and select **See
    more** for the Dataverse connector.

    ![](./media/image58.png)

10. Select the **Add a new row** action.

    ![](./media/image59.png)

11. Select **Booking Requests** for table name.

12. Enter +++**Copilot booking**+++ in the **Booking Name** field.

13. Select **Show all**.

    ![](./media/image60.png)

14. Enter +++contoso_bookingrequests()+++ in the **Property (Real Estate
    Properties)** field, move the cursor within the brackets, and
    use **Dynamic content**.

    ![](./media/image61.png)

15. Select the **PropertyId** parameter.

    ![](./media/image62.png)

16. Use **Dynamic content** to select the **ViewerName** parameter for
    the **Viewer Name** field.

    ![](./media/image63.png)

17. Use **Dynamic content** to select the **ViewerEmail** parameter for
    the **Viewer Email** field.

    ![](./media/image64.png)

18. The parameters will now look similar to those in the screenshot
    below.

    ![](./media/image65.png)

19. Select the **Respond to Copilot** action. Select **Settings** and
    ensure that **Asynchronous Response** is set to **Off**.

    ![](./media/image66.png)

20. Select **Save draft**.

    ![](./media/image67.png)

21. Once saved, select **Publish**.

    ![](./media/image68.png)

22. Close the Power Automate tab.

### Task 4: Add a Copilot action for creating a booking request

1.  Back in the Copilot Studio page, select **Refresh**.

    ![](./media/image69.png)

2.  Select the **Create Booking Request** flow.

    ![](./media/image70.png)

3.  Select **Next** in the Choose an option screen.

    ![](./media/image71.png)

4.  Select **Next** in the Review inputs and outputs .

    ![](./media/image72.png)

5.  Select **Finish** in the **Review and finish** screen.

    ![](./media/image73.png)

6.  Select the **Topics** tab and select the **Book a Real Estate
    Showing** topic.

    ![](./media/image74.png)

7.  Select the the **+** icon below the **What date and time do you want
    to see the property?** node and select **Call an action**.

8.  Select the **Booking Request** flow.

    ![](./media/image75.png)

9.  Select the **PropertyId** variable for the **PropertyId** input
    parameter.

Select the **Name** variable for the **ViewerName** input parameter.

Select the **EmailAddress** variable for the **ViewerEmail** input
parameter.

    ![](./media/image76.png)

10. Select the the **+** icon below the action node. Select **Topic
    management**, then select **Go to another topic** and select **End
    of conversation**.

    ![](./media/image77.png)

11. Select **Save**.

    ![](./media/image78.png)

12. Once saved, select **Publish** and select **Publish** again in the
    confirmation dialog.

    ![](./media/image79.png)

    ![](./media/image80.png)

## Exercise 3: Test the copilot 

### Task 1: Test the copilot and make a booking request

1.  Select the **Test** button in the top-right of the screen to open
    the testing panel. Select the **three dots** at the top of the
    testing panel in the top-right of the screen. Select **Track between
    topics**.

    ![](./media/image81.png)

2.  When the **Conversation Start** message appears, your copilot starts
    a conversation.

3.  When the **Conversation Start** message appears, your copilot starts
    a conversation.

4.  In response, enter a trigger phrase for the topic that you created:

+++I want to book a real estate showing+++

5.  The copilot responds with the "**What is your name?**" question.

6.  Enter your name.

    ![](./media/image82.png)

7.  Then enter your email when it prompts for the email. After you enter
    the details, an Adaptive Card displays the information that you
    entered, a question asking if the information is correct, and
    options to select **Yes** or **No**. Select **Yes**.

    ![](./media/image83.png)

8.  Select **House** for the type of property prompt.

9.  Enter +++**2**+++ for the number of bedrooms prompts.

    ![](./media/image84.png)

10. Enter Tomorrow 2:00 PM to the **What date and time do you want to
    see the property?** prompt.

11. Select **Yes** to the **Did that answer your question?** prompt.

12. Select any rating.

13. Select **No** to the **Can I help with anything else?** prompt.

    ![](./media/image85.png)

### Task 2: Verify booking request

1.  Navigate to the Power Apps portal at
    +++**https://make.powerapps.com**+++.

2.  In the left navigation pane, select **Tables** and
    select **Custom**.

3.  Select the **Booking Request** table.

    ![](./media/image86.png)

4.  Under **Booking Request columns and data** you should see that a
    Copilot booking request is now created.

    ![](./media/image87.png)

## Exercise 4: Set up Generative AI

In this exercise, you learn how to use the Generative answers feature to
improve your copilot's responses.

### Task 1: Enable Generative AI

1.  Login to the Copilot Studio using your tenant credentials at
    +++<https://copilotstudio.microsoft.com>+++ if not logged in
    already.

2.  Select the Copilot **Real Estate Booking Service**.

    ![](./media/image88.png)

3.  Select **Settings** in the top-right of the screen.

    ![](./media/image89.png)

4.  Select the **Generative AI** tab.
   
    -    Select **Generative** under **How should your copilot decide how to respond**.
    -    Select **Medium** for **Copilot content moderation**.
    -    Select **Save**.
    -    
    ![](./media/image90.png)

5.  **Close** the Settings pane.

    ![](./media/image91.png)

### Task 2: Enable knowledge

1.  Select your copilot in the Copilot pane on the left-hand side of the
    screen to return to the **Overview** tab.

2.  Verify that general knowledge is enabled in the Knowledge section.

    ![](./media/image92.png)

### Task 3: Add knowledge from a website

1.  Select **+ Add knowledge** under the **Knowledge** section in the
    Overview page of the copilot.

    ![](./media/image93.png)

2.  Select the **Public websites** tile.

    ![](./media/image94.png)

3.  Enter the public website
    link +++https://create.microsoft.com/templates/real-estate+++.
    Select **Add**.

    ![](./media/image95.png)

4.  Give the name +++ Real Estate Website+++ in the Name field and then
    select **Add**.

    ![](./media/image96.png)

### Task 4: Add knowledge from Dataverse

1.  Select the **Knowledge** tab. Select **+ Add knowledge**.

    ![](./media/image97.png)

2.  Select **Dataverse**.

    ![](./media/image98.png)

3.  Select the **Real Estate Property** table and select **Next**.

    ![](./media/image99.png)

4.  Preview the data in the next screen and then select **Next**.

    ![](./media/image100.png)

5.  Review the details and click on **Add** in the Review and finish
    screen.

    ![](./media/image101.png)

### Task 5: Add knowledge from files

1.  From the **Knowledge** tab, select **+ Add knowledge**.

    ![](./media/image102.png)

2.  Select **Files**.

    ![](./media/image103.png)

3.  Select Click to browse and browse to locate the file
    **SummitRealtyCaseStudy.docx** at **C:\LabFiles** and select it.

    ![](./media/image104.png)

4.  Select **Add**.

    ![](./media/image105.png)

### Task 6: Use generative answers in System fallback topic

1.  Select the **Topics** tab and select **System**. Select
    the **Fallback** topic.

    ![](./media/image106.png)

2.  Select the **three dots** in the message node and select **Delete**.

    ![](./media/image107.png)

3.  Select the **+** icon under the Condition node, select **Advanced**,
    and select **Generative answers**.

    ![](./media/image108.png)

4.  Select the **Input** field, select **System** in the **Select a
    variable** pane. Select **Activity.Text** from it.

    ![](./media/image109.png)

5.  Select **Edit** under **Data sources**.

    ![](./media/image110.png)

6.  Select **Search only selected sources**.

    ![](./media/image111.png)

7.  Select the **SummitRealtyCaseStudy** document. Deselect **Allow the
    AI to use its own general knowledge**.
    Select **Medium** for **Content moderation**.

    ![](./media/image112.png)

8.  Select **Save**.

    ![](./media/image113.png)

### Task 7: Configure Security

1.  Select your copilot in the Copilot pane on the left-hand side of the
    screen to return to the **Overview** tab.

2.  From the copilot page top menu, click on **Channels** (If the
    Channels is not visible, click on the +1 to view the **Channels**
    option)

    ![](./media/image114.png)

3.  Select **Dynamics 365 Customer Service** from the Customer
    engagement hub pane.

    ![](./media/image115.png)

4.  On the Dynamics 365 Customer Service page, click on **Disconnect**.

    ![](./media/image116.png)

5.  Once done, **close** the Dynamics 365 Customer Service pane.

    ![](./media/image117.png)

6.  Select **Settings** in the top-right of the screen.

    ![](./media/image118.png)

7.  Select the **Security** tab and then select
    the **Authentication** tile.

    ![](./media/image119.png)

8.  Select Authenticate with Microsoft **(Entra ID authentication in
    Teams and Power App)**.

9.  Select **Save**.

    ![](./media/image120.png)

10. Select **Save**.

    ![](./media/image121.png)

11. Select **Close**.

    ![](./media/image122.png)

12. Select your copilot in the Copilot pane on the left-hand side of the
    screen to return to the **Overview** tab.

13. Select **Publish** and select **Publish**.

    ![](./media/image123.png)

### Task 8: Test the copilot's knowledge

1.  Select the **Test** button in the top-right of the screen to open
    the testing panel.

    ![](./media/image124.png
    )

3.  Select the **three dots** at the top of the testing panel in the
    top-right of the screen.

4.  Select **Track between topics**.

5.  Select the **Start a new conversation** icon at the top of the
    testing panel.

6.  Explore the copilot and see how it uses the different knowledge
    sources.

**Summary:**

In this lab, we have learnt to

- Use entities and slot filling

- Implement Flow actions

- Add knowledge to the copilot

- Enable Generative AI
