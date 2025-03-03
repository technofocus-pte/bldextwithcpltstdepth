# Lab 01: Creating and using an agent from Copilot Studio for managing a Real Estate Application

**Lab Duration** – 120 minutes

**Introduction**

Contoso Real Estate specializes in the sale and management of both
commercial and residential properties. Currently, customer information
is efficiently stored within their Dataverse instance, allowing for
streamlined data management. However, the booking process presents a
significant challenge.

At present, customers can only request bookings via phone, leading to an
overwhelmed phone line and long waiting time. This situation not only
frustrates customers but also risks losing potential business as many
are unable to connect with the office to request services.

To address these issues, Contoso Real Estate is committed to developing
a comprehensive digital solution. This solution will empower customers
to easily access information about the booking process and submit
booking requests online.

**Objectives**

- Build a standalone agent for Contoso Real Estates from Copilot Studio
  (that will allow customers to discover information about the real
  estate booking process and create booking requests for the office to
  review.)

- Create Topics to set up the logic of the bookings.

- Create the Dataverse tables required for the bookings.

- Publish the agent.

>[!Alert] Important: **Lab 03** needs to be completed by the end of Day 1 in order to execute the Day 2 lab. Even if Labs 01 and 02 are not completed, please ensure to complete Lab 03 by the end of Day1.

## Exercise 0: Setting up your environment

### Task 1: Login to VM

1.  Login to the VM using the **Username** and **Password** from
    the **Home** tab.

### Task 2: Synchronize the VM clock

1.  After logging into the VM, right click on the clock at the bottom
    right corner of the screen.

2.  Select **Adjust date and time.**

    ![](./media/image1.png)

3.  On the Settings screen that opens up, click on **Sync now** under
    Additional settings.

    ![](./media/image2.png)

4.  This takes care of synchronizing the time just in case the automatic
    synchronization does not work.

5.  **Close** the Settings pane.

    ![](./media/image3.png)

## Exercise 1: Setting up Power Apps and Dataverse

### Task 1: Sign up for the Microsoft Power Apps Developer Plan

1.  Open a browser and navigate  to +++https://powerapps.microsoft.com/free/+++ and select
    **Start free** or **Try for free**.

    ![](./media/image4.png)

2.	Login using the **Administrative Username** and **Password** from the **Resources** tab if prompted. This will be your **login credentials** to all the Microsoft sites and apps for the labs.
   
    ![](./media/image127.png)
  	
3.  Under **Let's get started**, enter the **Administrative Username** from the **Resources** tab  in the text box, check the agreement box and select **Start free**.

    ![](./media/image5.png)

4.  If you see a prompt that you have an existing account with
    Microsoft. Select **Sign in**. Enter your password.

5.  If prompted, Select **Yes** to stay signed in.

6.  Click on **Environment** in the top-right corner of the screen and
    select **Dev One**.

    ![](./media/image6.png)

### Task 2: Create a solution

1.  From the Power Apps Maker
    Portal(+++https://make.powerapps.com/+++), select **Solutions**
    form the left pane.

    ![](./media/image7.png)

2.  Click on **+ New solution**.

    ![](./media/image8.png)

3.  Enter +++**Bookings**+++ for the Display name and click on **+ New
    publisher**.

    ![](./media/image9.png)

4.  Enter the below details and then click on **Save**.

    |	Property |	Value |
    |:-----|:--------|
    | Display name	|+++Contoso+++	|
    |	Name |	+++Contoso+++|
    | Prefix |+++Contoso+++	|

    ![](./media/image10.png)

    >[!Note] **Note:** If you get a message stating that **A record with matching key value already exists**, close the publisher creation pane and select the Publisher **Contoso** in the New Solution creator pane. 

5.  Select **Contoso (contoso)** under Publisher and then click on
    **Create**.

    ![](./media/image11.png)

6.  Select **Back to solutions** in the top-left of the screen.

    ![](./media/image12.png)

### Task 3: Set the preferred solution

1.  Under Solutions in the Maker portal, select **Manage** for **Set
    your preferred solution**.

    ![](./media/img1.png)

2.  Select **Bookings (contoso)** under **Unless otherwise specified,
    save my changes in** and select **Apply**.

    ![](./media/image14.png)

    ![](./media/image15.png)

### Task 4: Create the Real Estate Properties custom table

Follow these steps to create a new custom table in Dataverse for Real
Estate Properties.

1.  From the left navigation pane, select **Tables**, select the drop
    down next to **+ New table** and then select **Create** **new
    tables**.

    ![](./media/image16.png)

2.  Click on **Got it** in the **Let’s set up your data** dialog.

    ![](./media/image17.png)

3.  On the Create new tables screen, click on **+ New table -\> Add
    columns and data**.

    ![](./media/image18.png)

4.  Rename the table name from **Table1** to +++**Real Estate Property**+++ and then click on **Save and exit**.

    ![](./media/image19.png)

5.  Click on **Save and exit** in the confirmation dialog.

    ![](./media/image20.png)

6.  Once saved, click on the **Custom** tab to find the newly created
    table there. Click on the **Real Estate Property** table.

    ![](./media/image21.png)

7.  Under the **Real Estate Property columns and data**, change the name
    of the column called **New Column** (Click on the drop down next to
    **New Column** and select **Edit Column** and update the **Display
    name**) to +++**Property Name**+++ and select **Save**.

    ![](./media/image22.png)

8.  Select the **+** button to add a new column in the columns and data
    pane. In the New column pane, enter the following values, and then
    select **Save**.

    - Display name: +++**Asking Price**+++

    - Data type: Currency

    ![](./media/image23.png)

    ![](./media/image24.png)

9.  Add the following two columns.

    |	Display name | Data type	|
    |:-----|:--------|
    |+++Street+++	|	Single line of text (this value is the default)|
    |	+++City+++|	Single line of text (this value is the default)|

10. Add another column with the below values

    - **Display name**: +++Bedrooms+++

    - **Data type**: Choice -\> Choice

    ![](./media/image25.png)

    Create the choice values:
    
    Select **+ New choice** under **Sync this choice with** option

    ![](./media/image26.png)

    - Under **Choices**, provide the Display name as +++**Bedrooms**+++.
    
    - You see two entry fields titled **Label** and **Value**.
      Enter **1** under the label. Power Apps assigns a value automatically
      but you can change the value to **1**.
    
    &nbsp;
    
    - Select **+ New choice** and make **2** the new entry for Label
      and **2** for Value.
    
    &nbsp;
    
    - Select **+ New choice** and make **3** the new entry for Label
      and **3** for Value.
    
    &nbsp;
    
    - Select **+ New choice** and make **4** the new entry for Label
      and **4** for Value.
    
    &nbsp;
    
    - Select **+ New choice** and make **5** the new entry for Label
      and **5** for Value.
    
    &nbsp;
    
    - Select **Save**.

    ![](./media/image27.png)

    Select the added choice **Bedrooms**, by clicking the drop down of
**Sync this choice with**

    ![](./media/image28.png)

    Click on **Save**.

    ![](./media/image29.png)

11. Select the **+** button to add a new column in the columns and data
    pane.

12. In the New column pane, enter the following values, and then
    select **Save**:

    - **Display name**: +++Bathrooms+++

    - **Data type**: Choice -\> Choice

    ![](./media/image30.png)

    **Note:** Repeat the step 8 process with the Value +++**Bathrooms**+++.

    Create the choice values

    - Under **Choices**, provide the Display name as +++Bathrooms+++.
    
    &nbsp;
    
    - You see two entry fields titled **Label** and **Value**.
      Enter **1** under the label. Power Apps assigns a value automatically
      but you can change it to **1**.
    
    - Select **+ New choice** and make **2** the new entry for Label
      and **2** for Value.
    
    - Select **+ New choice** and make **3** the new entry for Label
      and **3** for Value.
    
    - Select **+ New choice** and make **4** the new entry for Label
      and **4** for Value.
    
    - Select **+ New choice** and make **5** the new entry for Label
      and **5** for Value.
    
    - Select **Save**.

    ![](./media/image31.png)

    Select the created choice and click on Save in the column addition pane.

    ![](./media/image32.png)

13. Add another column by selecting the **+** button again in the
    columns and data pane.

    In the New column pane, enter the following values, and then
select **Save**:

    - **Display name**: +++**Client**+++

    - **Data type**: Lookup -\> Lookup

    - **Related Table**: Contact

    ![](./media/image33.png)

14. Once the columns are all created, under **Real Estate Property
    columns and data**, enter the following test data:

    >[!Note] **Note:** If the required columns are not getting displayed, adjust the columns that are displayed by selecting the **+<number>more**

    ![](./media/image34.png)

    - Property Name: +++**1100 High Villas**+++

    - Asking Price: +++**250,000**+++

    - Bathrooms: **3**

    - Bedrooms: **2**

    - City: +++**Redmond**+++

    - Street: +++**Main Avenue**+++

    - Client: **Select any contact**

    ![](./media/image35.png)

### Task 5: Create the Bookings table

Follow these steps to create a new custom table in Dataverse for Real
Estate Property Bookings.

1.  From the left navigation pane, select **Tables**, select **Create**
    **new tables**.

    ![](./media/image36.png)

2.  On the **Create new tables** screen, click on **+ New table -\> Add
    columns and data**.

    ![](./media/image37.png)

3.  Rename the table name from **Table1** to +++**Booking Request**+++ and
    then click on **Save and exit**.

    ![](./media/image38.png)

4.  Click on **Save and exit** in the confirmation dialog.

    ![](./media/image20.png)

5.  Once saved, click on the **Custom** tab to find the newly created
    table there. Click on the **Booking Request** table.

    ![](./media/image39.png)

6.  Change the name of the column called **New Column** to +++**Booking
    Name**+++ (Click on the drop down next to **New Column** and select
    **Edit Column** and update the **Display name**).

    ![](./media/image40.png)

7.  Click on **+** symbol next to the column names.

    ![](./media/image41.png)

8.  Create the following columns with the name and data type as
    specified below. Select **Save**.

    -	Display name –  +++Property+++
    -	Data type –  Lookup -> Lookup
    -	Related Table – Real Estate Property

    ![](./media/image42.png)

    -	Display name – +++Viewer Name+++
    -	Data type – Single line of text


    -	Display name – +++Viewer Email+++
    -	Data type – Single line of text
    -	 Format – Email

    -	Display name – +++Booking Date+++
    -	Data type – Date and time

    -	Display name – +++Notes+++
    -	Data type – Multiple lines of text

    ![](./media/image43.png)

    ![](./media/image44.png)

9.  Add a choice data type column with the below details.

    -	Display name – +++Decision+++
    -	Data type – Choice -> Choice

    ![](./media/image45.png)

    Under **Sync this choice with**, click on **+ New Choice**. Enter
**Display name** as +++**Decision**+++.

    Enter the below details and click on **Save**.

    - Label – +++**Undecided**+++

    - Value – 1

    - Label – +++**Accepted**+++

    - Value – 2

    - Label – +++**Declined**+++

    - Value – 3

    ![](./media/image46.png)

    Select the added Choice **Decision** under **Sync this choice with**
field, designate **Undecided** as the **Default choice** and click on
**Save**.

    ![](./media/image47.png)

## Exercise 2: Working with Copilot Studio

### Task 1: Sign up for Copilot Studio trial

1.  Open the url +++https://copilotstudio.microsoft.com/+++.

2.  Leave the **Choose your country/region** with the **default** value
    and click on **Get Started**.

    ![](./media/image48.png)

3.  Click on **Environments** on the top left and select
    **Dev One**.

    ![](./media/image49.png)

4.  Select **Skip** if you get a Welcome to Copilot Studio! Prompt.

    ![](./media/image50.png)

### Task 2: Create the Real Estate Booking Service agent

1.  Select **Create** from the left navigation pane and select the **New
    agent** tile.

    ![](./media/image51.png)

2.  Select **Skip to configure**.

    ![](./media/image52.png)

3.  Fill in the below details.

    - Name - +++**Real Estate Booking Service**+++
    
    - Description - +++**Create bookings for real estate properties**+++
    
    - Instructions - +++**Create a copilot for topics relating to creating
      bookings for real estate properties+++**
    
    - Language **–** Select **English**

    ![](./media/image53.png)

4.  Select the three dots next to the Create button in the top-right of
    the screen and select **Edit advanced settings**.

    ![](./media/image54.png)

5.  Select the **Bookings** solution and select **Save**.

    ![](./media/image55.png)

6.  In the top-right of the screen, select **Create**.

    ![](./media/image56.png)

7.  Once the agent is created, in the Test your copilot pane, enter
    +++**How do I make a booking?+++** and click **Enter** and observe the
    response.

    ![](./media/image57.png)

### Task 3: Configure Security

1.  Select **Settings** in the top-right of the screen.

    ![](./media/image58.png)

2.  Select the **Security** tab and then select
    the **Authentication** tile.

    ![](./media/image59.png)

3.  Select **No authentication** and click on **Save**.

    ![](./media/image60.png)

4.  Select **Save** in the **Save this configuration** prompt.

    ![](./media/image61.png)

5.  Once the Authentication settings are saved, click on the **Close**
    option to close the **Settings** pane.

    ![](./media/image62.png)

### Task 4: Remove topics

Sample topics are included with new copilots. Remove these sample
topics. Disable system topics that you don't require.

1.  Select the **Topics** tab from the top menu of the Copilot Overview
    page.

    ![](./media/image63.png)

2.  You will land in the **Custom** Topics page.

3.  Select the **System** tab. Toggle **Enabled** to **Off** for the
    **Sign in** topic.

    ![](./media/image64.png)

### Task 5: Publish and test the copilot

1.  Select **Publish** and select **Publish** again.

    ![](./media/image65.png)

2.  Select **Publish** in the **Publish this copilot** dialog.

    ![](./media/image66.png)

### Task 6: Demo Website

The Demo website allows users without a license to test your copilot.
You can provide them with the URL to the demo website.

1.  Select the **three dots** next to the **Settings** or the **Publish** button in the
    top-right of the screen and select **Go to demo website**.

    ![](./media/image67.png)

2.  In the **Type your message** text box, enter +++**What information is
    needed to book a viewing for a real estate property?**+++ and observe
    the response from the copilot.

    ![](./media/image68.png)

## Exercise 3: Create and manage topics using Copilot

### Task 1: Create a topic using Copilot

Topics can be created and edited using natural language.

1.  From the **Topics** tab, select **Add a topic** and select **Create
    from description with Copilot**.

    ![](./media/image69.png)

    >[!Note] **Note:** Select **Allow** if prompted with **See text and images copied to the clipboard**
    >
    >![](./media/img10.png)
    
    
3.  Enter the below details and click on **Create**.

    - Name your topic - +++**Customer Details**+++

    - Create a topic to... - +++**Ask the customer for their name and email
  address**+++

    ![](./media/image70.png)

4.  A new topic displays with the  trigger phrases and question
    nodes.

5.  Select **Save**.

    ![](./media/image71.png)

### Task 2: Update nodes with natural language

1.  If the **Edit with copilot** pane isn't shown on the right-hand side
    of the screen, select the **Copilot** icon in the upper part of the
    authoring canvas.

2.  Select the second question node, **What is your email address?**

3.  In the **Edit with Copilot** panel, in the **What do you want to
    do?** field, enter the following text:

    +++**Update the message in this question node to say thank you to the
Name variable from the previous node and then proceed to ask the email
address question**+++

4.  Select **Update**.

    ![](./media/image72.png)

5.  Select **Save**.

    ![](./media/image73.png)

### Task 3: Add nodes with natural language

In addition to adding updating existing nodes, you can use Copilot to
add new ones.

1.  Make sure that no node is selected by clicking in the empty space
    around the nodes.

2.  In the **What do you want to do?** field, enter the following text
    and then select **Update.**

    +++**Add a new multiple-choice question to prompt the user if the details are correct with two options Yes or No**+++

    ![](./media/image74.png)

3.  A new question node is added to the end of the topic with options
    for the user to select.

4.  Select **Save**.

    ![](./media/image75.png)

### Task 4: Configure the scope of the variables

1.  Select **Variables** to open the Variables pane.

    ![](./media/image76.png)

2.  Select the right-hand check boxes for the topic variables and click
    on **Save**.

    ![](./media/image77.png)

## Exercise 4: Create and manage topics manually

### Task 1: Create a topic from blank

1.  Select the **Topics** tab.

2.  Select **Add a topic** and select **From blank**.

    ![](./media/image78.png)

3.  Select **Details** to open the Topic details dialog.

    ![](./media/image79.png)

4.  Fill in the below details and click on **Save**.

    - **Name** - +++Book a Real Estate Showing+++

    - **Display Name –** +++**Book**+++

    - **Description**  - +++Select the property and requested date and create a booking request+++

    ![](./media/image80.png)

5.  Select **Details** to close the Topic details dialog.

    ![](./media/image81.png)

### Task 2: Add trigger phrases

1.  Select **Edit** under **Phrases** in the **Trigger**. Enter +++**I
    want to book a real estate showing**+++ under **Add Phrases** and
    select the **+** icon.

    ![](./media/image82.png)

2.  Enter the below phrases one by one.

    - +++**Schedule a real estate showing**+++

    - +++**Arrange the viewing for a real estate property**+++

    - +++**Set up an appointment to view a house**+++

    - +++**Plan a property viewing**+++

3.  Once all the phrases are added, select **Save**.

    ![](./media/image83.png)

### Task 3: Add a message node

1.  Select the **+** icon under the Trigger node and select **Send a
    message**.

    ![](./media/image84.png)

2.  In the **Enter a message** field, enter the following text:

    +++Hi, I can help you with booking a real estate property showing.+++

3.  Select **Save**.

    ![](./media/image85.png)

### Task 4: Add a Topic management node

1.  Select the **+** icon under the send a message node and
    select **Topic management -\> Go to another topic**.

    ![](./media/image86.png)

2.  Select the **Customer Details** topic.

    ![](./media/image87.png)

3.  Select **Save**.

    ![](./media/image88.png)

### Task 5: Add condition node 

1.  Select the **+** icon under the topic management node and
    select **Add a condition**.

    ![](./media/image89.png)

2.  Select **DetailsCorrect** for variable.

    ![](./media/image90.png)

3.  Select the **Condition** as **is equal to**

4.  Select the **value** as **Yes**.

    ![](./media/image91.png)

5.  Select **Save**.

    ![](./media/image92.png)

### Task 6: Add question nodes

1.  Select the **+** icon under the left-hand condition node and
    select **Ask a question**. Fill in the below details and click on
    **Save**.

    - Enter a message  - +++Which property do you want to see?+++

    - **Identify** - Select **User's entire response**.

    - **Save user response as** Enter +++**PropertyName**+++ for **Variable
  name**

    ![](./media/image93.png)

2.  Select the the **+** icon under the question node and select **Ask a
    question**. Fill in the below details and click on **Save.**

    - **Enter a message** - +++What date and time do you want to see the
  property?+++

    - Identify - Select **Date and Time**

    - **Save user response as** - Enter +++**DateTime**+++ for **Variable
  name**

    ![](./media/image94.png)

### Task 7: Test the copilot

1.  Select the **Test** button in the top-right of the screen to open
    the testing panel. Select the **three dots** at the top of the
    testing panel in the top-right of the screen. Select **Track between
    topics**.

    ![](./media/image95.png)

2.  When the **Conversation Start** message appears, your copilot starts
    a conversation.

3.  In response, enter a trigger phrase for the topic that you created:

    +++I want to book a real estate showing+++

4.  The copilot responds with the "**What is your name?**" question.

5.  Enter your name.

    ![](./media/image96.png)

6.  Then enter your **email** when it prompts for the email. After you
    enter the details, a question appears asking if the information is
    correct, and options to select **Yes** or **No**. Select **Yes**.

    ![](./media/image97.png)

7.  Enter +++555 Oak Lane, Denver, CO 80203+++ to the **Which property to
    you want to see?** prompt.

8.  Enter +++**Tomorrow 10:00 AM**+++ to the **What date and time do you
    want to see the property?** prompt.

    ![](./media/image98.png)

## Exercise 5: Build an Autonomous agent that automatically sends an email when a booking is created or updated

This exercise is to showcase the **When a row is added, modified or deleted** trigger of an Autonomous agent. 

### Task 1: Create an agent

2.  Click on Agents from the left navigation pane.

    ![](./media/image99.png)

3.  Click on **+ New agent** to create a new agent.

    ![](./media/image100.png)

4.  Click on **Skip to configure** to configure the agent.

    ![](./media/image101.png)

5.  Enter the below details and click on **Create**.

    **Name** - +++Autonomous agent+++

    **Description** - +++You are an agent to detect the updates to the
Booking Requests table+++

    ![](./media/image102.png)

6.  The agent setup will take few minutes to get completed. Once done,
    the Autonomous agent opens with the **Your agent is ready** message.

    ![](./media/image103.png)

7.  Select **Settings** from the top right corner.

    ![](./media/image104.png)

8.  The Generative AI option must be enabled in order to continue with
    the Trigger creation for the agent.

9.  Select the **Generative AI** option from the list of options on the
    left side of the **Settings** screen. Under **Using generative AI in
    conversations**, select **Generative (preview)**. Click on **Save**.

    ![](./media/image105.png)

10. Close the **Settings** pane.

    ![](./media/image106.png)

### Task 2: Add trigger to the agent

1.  Back in the Autonomous agent page, scroll down to the **Triggers
    (preview)** section and select **+ Add trigger**.

    ![](./media/image107.png)

2.  Select **When a row is added, modifies or deleted** trigger from the
    **Add trigger** screen.

    ![](./media/image108.png)

3. Click on **Continue** in the next screen.

4.  Once selected, The **Trigger name** and the **Sign in options** gets
    loaded in the next screen. This will take a few minutes to get
    populated. For the trigger we selected, there will be two apps, one
    being the **Microsoft Copilot Studio** and the other one being the
    **Microsoft Dataverse**.

5.  Once loaded, ensure that the connectivity status is in **green** for
    the sign in options and then click **Next** to continue.

    ![](./media/image109.png)

6.  In the Add trigger screen, select the below details and click on
    **Create trigger**.

    - Change type – **Added or modified**

    - Table name – **Booking Requests**

    - Scope – **Organization**

    - Trigger instructions – Leave as **default**. This will return the
  entire response to the agent.

    ![](./media/image110.png)

7.  The Trigger creation may take 3 to 5 minutes to complete.

    ![](./media/image111.png)

8.  Once done, click on **Close** in the **Time to test your trigger!**
    Screen.

    ![](./media/image112.png)

9. Click on the **Actions** tab and select **+ Add an action**.

    ![](./media/image130.png)
   
10. Search for +++Send an mail+++ and select **Send an email (V2) action**.

    ![](./media/image131.png)

11.	Once the connection is established, click on **Next**.

   	![](./media/img2.png)
   	
12.	Select **End user Authentication** as **Copilot Authentication** and select **Add action**.

   	![](./media/img3.png)
   	
13.	Select the created Action.

   	![](./media/img4.png)
   	
14.	Select the **Inputs** tab.

   	![](./media/img5.png)
   	
15.	Give the email id to which the mail needs to be delivered in the **Description** field and click on **Save**. This can be any mail id you have access to.

   	![](./media/img6.png)

### Task 3: Add instructions to the agent

1.	Select **Overview** to go to the Overview page and then click on **Edit** in the Overview page

    ![](./media/img7.png)

2.	Update the instructions as below, replacing the place holder for **Your mail id** with the **mail id** to which the details needs to be sent and click on **Save**.
   
    +++a.	Read the details of the row that gets added or modified+++
    +++b.	Mail the modified information only to <Your email id> with a proper subject and body added to the email+++


    ![](./media/img8.png)

4.  Click on **Publish** to publish the agent to all the channels it is
    connected to.

    ![](./media/image115.png)

5.  Click on **Publish** in the **Publish this agent** dialog box.

    ![](./media/image116.png)

6.  Once published, you will get a success message.

    ![](./media/image117.png)

### Task 4: Update the Bookings table

1.  Login to +++https://make.powerapps.com/+++ and select **Tables** from
    the left navigation pane.

    ![](./media/image118.png)

2.  Select **Custom** and select the **Booking Request** table from
    there.

    ![](./media/image119.png)

3.  Add or update a value in the table.

    ![](./media/image120.png)

### Task 5: Test the agent

1.  From the agent page, select Test, and switch on the **Activity
    Map**.

    ![](./media/image121.png)

2.  From the agent page, select the **Test trigger** option. The update
    we made in the Bookings table would have triggered the trigger. We
    will use it to **test** from the copilot studio.

    ![](./media/image122.png)

3.  Select the latest entry and click on **Start testing**.

    ![](./media/image123.png)

4.  The trigger gets invoked.

    ![](./media/image124.png)

5.  The mail is sent to the specified mail id.

    ![](./media/image125.png)

6.	Check the corresponding mail box to see if you have received a mail as below.
   
    ![](./media/img9.png)


**Summary**

In this lab, we have learnt to

- Build an agent from the Copilot Studio and create topics in it.

- Test the agent from the Copilot Studio and publish it to the demo
  web site.

- Build an autonomous agent and test it
