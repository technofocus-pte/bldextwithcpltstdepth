## Lab 04 - Enhancing the Real Estate copilot with Gen AI capabilities

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

1.  Open the Copilot Studio at +++https://copilotstudio.microsoft.com+++
    and open the agent **Real Estate Booking Service.**

2.  Select **Settings** in the top-right of the screen.

    ![](./media/image1.png)

3.  Select the **Entities** tab. You can see a list of pre-built
    entities.

    ![](./media/image2.png)

### Task 2: Create the property type entity

1.  Select **+ Add an entity** and select **+ New entity**.

    ![](./media/image3.png)

2.  Select the **Closed list** tile.

    ![](./media/image4.png)

3.  Enter the below details

    -   Name - +++Property Type+++
    -   Enter item under List items –  +++Apartment+++ - Select Add

    ![](./media/image5.png)

4.  Enter +++**Condominium**+++ in the **Enter item** field and
    select **Add**.

5.  Enter +++**Duplex**+++ in the **Enter item** field and
    select **Add**.

6.  Enter +++**House**+++ in the **Enter item** field and
    select **Add**.

   ![](./media/image6.png)

7.  Select **+ Synonyms** for **Apartment**, enter +++**Flat**+++, then
    select the **+** icon and select **Done**.

    ![](./media/image7.png)

8.  Select **+ Synonyms** for **House**, enter +++**Single-family home**+++, then select the **+** icon and select **Done**.

9.  Select **+ Synonyms** for **Condominium**,
    enter +++**Townhouse**+++, then select the **+** icon and
    select **Done**.

10. Select **Save**.

    ![](./media/image8.png)

11. Select **Close**.

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

5.  Select the **+** icon below the new question node and select **Ask a
    question**.

6.  Enter the below details and click on **Save**.

    - **Enter a message** - +++How many bedrooms do you need?+++

    - **Identify -** Select **Number of Bedrooms**

    - **Save user response as** - Enter +++NumberofBedrooms+++ for **Variable name**

    ![](./media/image19.png)

## Exercise 2: Create Flows

Microsoft Copilot Studio can access data in Microsoft Dataverse using Agent flows

### Task 1: Create Power Automate flow to retrieve a property

1.  Select the **Tools** tab from the top menu. Select **+ Add a tool**.

    ![image](https://github.com/user-attachments/assets/83454cdc-a26a-49dc-b844-cea304933cb3)

2.	Select **+ New tool**.

    ![image](https://github.com/user-attachments/assets/a2678a4c-e46a-4bc5-a889-4502e6909681)

3.  Select **Agent flow**.

    ![image](https://github.com/user-attachments/assets/5d1054bb-1cb1-45ff-82c2-b9c603f9fbc8)
  	
4.	Select the trigger step **When an agent calls the flow** and select **+ Add an input**.

    ![image](https://github.com/user-attachments/assets/b5cc43f1-ff0d-4868-a2d7-870a24a334c7)

    ![image](https://github.com/user-attachments/assets/6034a2d9-9f0d-4ee1-9449-d3dceb6133f7)

5.	Select **Text**.

    ![image](https://github.com/user-attachments/assets/360cd7d0-1ecc-457b-952f-45e94efa0b56)

6.  Enter the below details

    - **Input** – +++Bedrooms+++

    - **Please enter your input** - +++Number of Bedrooms+++

    ![image](https://github.com/user-attachments/assets/552632a5-d887-47eb-965d-6ef7c7644776)

7.  Select the **+** icon between the two steps in the flow and to **Add an action**.

    ![image](https://github.com/user-attachments/assets/6e00dd75-3e9c-45b5-8cc4-74ce9a035ef3)

8. Enter +++**Dataverse**+++ in the **Search** field and select **See
    more** for the **Microsoft Dataverse connector**.

    ![image](https://github.com/user-attachments/assets/aad5dba1-852c-492f-8daa-5f630c9c9eee)

9. Select the **List rows** action.

    ![](./media/image28.png)

10. If prompted for authentication, select **OAuth** and select **Sign
    in**. Sign in using your tenant id if prompted.

    ![](./media/image29.png)

11. Select **Real Estate Properties** for table name.

12. Select **Show all** if all the options does not get listed automatically.

13. Enter +++contoso_bedrooms eq+++ in the **Filter Rows** field.

14.	Use **spacebar** next to **eq** to ensure that you are adding the value after a space. Use **Dynamic content** to select the **Bedrooms** parameter and select **Add**.

    ![image](https://github.com/user-attachments/assets/418ac548-864b-45af-9a0d-0866819a6f47)

15. Select the **Respond to Copilot** action and select **+ Add an output**.

    ![image](https://github.com/user-attachments/assets/27b791ec-d38d-4a43-8c7f-10fd4d175ac7)

16. Select **Text**.

17. Enter the below details

    - **Enter a name** - +++PropertyId+++

    - **Enter a value to respond with** - select **Insert Expression** and
  enter the following expression:
      +++first(outputs('List_rows')?['body/value'])['contoso_realestatepropertyid']+++

    ![image](https://github.com/user-attachments/assets/27102be8-1523-4bab-9d37-c7befd35ec08)

18. Select **Add**.

    ![](./media/image33.png)

19.	From +++https://make.powerapps.com+++, open the table **Real Estate Property**. Navigate to its column, Property Name(This might be Real Estate Property or slightly different when created using Copilot) -> Edit Column -> Advanced options. Look for the value of the **Logical name**. It should be something similar to **contoso_newcolumn**. It might be slightly different as well. Save the part that is there after **contoso_** locally. If the Logical name is **contoso_newcolumn**, keep a note of **newcolumn** for usage in the next step.

   	![](./media/img17.png)
   	
20. Back in the **Copilot Studio Designer** page, in the **Respond to Copilot** pane, select **+ Add an output**.

    ![image](https://github.com/user-attachments/assets/fab0f41a-dce3-40cb-aae7-4e21199254e5)

21. Select **Text**.

    - **Enter a name** - +++PropertyName+++ 

    - **Enter a value to respond with** - select **Insert Expression** and
  enter the following expression:
      +++first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]+++

    - Replace **propertyname** in **contoso_propertyname** in the above expression, with the value saved in the step before this(**newcolumn**).

    - Select **Add**.
    
    ![](./media/image34.png)

    >[!Note] **Note:**  This value replacement needs to be done since the Logical name for this column is not a standard value and we will have to check and update based on the value from the Table.

    ![image](https://github.com/user-attachments/assets/03e696a4-db82-4d0c-b95a-eec11766dedf)

22. Select **Save draft**.

    ![image](https://github.com/user-attachments/assets/559c7891-1751-4b76-bcca-2fd47551defe)

23. Once saved, select **Publish**.

    ![image](https://github.com/user-attachments/assets/d05c2be0-4f04-4778-ac74-4073c502f58c)

24.	Select **Flows** from the left pane and then select the created flow named **Untitled**.

    ![image](https://github.com/user-attachments/assets/e039d36f-d7b0-4769-bb88-8a8a7c4de86c)

25.	Select **Edit** in the **Details** pane.

    ![image](https://github.com/user-attachments/assets/e770347d-ac33-464a-af9c-c1326ab72cb1)

26.	Name the flow as +++Get Property+++ and select **Save**.

    ![image](https://github.com/user-attachments/assets/a08cfa8b-7fcf-46d3-8073-32349cd6ac82)

### Task 2: Add a Copilot action for retrieving a property

1.	Select the **Topics** tab of the agent **Real Estate Booking Service**.

    ![image](https://github.com/user-attachments/assets/a54f266f-a45a-4565-874b-7045c4ac35e1)

2.	Select the **Book a Real Estate Showing** topic.

    ![](./media/img20.png)
  	
3.  Select the **+** icon below the **How many bedrooms do you need?** question node and select **Add a tool**. Select the **Get Property** flow.

    ![image](https://github.com/user-attachments/assets/1740a089-ca0a-44d2-9730-a93c09d0707a)

4.  Select the **NumberofBedrooms** variable for the **Bedrooms** input
    parameter.

    ![](./media/image45.png)

5.  Select the **three dots** in the **Which property do you want to
    see?** question node and select **Delete**.

    ![](./media/image46.png)

6. Select the the **+** icon under the action node and select **Send a message**.

7. Fill in the below details

    - **Enter a message** - +++Property+++

    - Select the **Insert variable** icon and select
  the **PropertyName** variable.

    ![](./media/image47.png)

8. Select **Save**.

    ![](./media/image48.png)

9. Once saved, select **Publish**.

    ![](./media/image49.png)

10. Click on **Publish** in the Publish confirmation dialog.

    ![image](https://github.com/user-attachments/assets/4a018bb9-c90f-40d3-b3a7-5d00c84ceefb)

### Task 3: Create Power Automate flow to make a booking

1.  Select the **Tools** tab and select **+ Add a tool**.

    ![image](https://github.com/user-attachments/assets/1001e326-432f-40db-ac87-ee6cbf7edc42)

2.	Select **Agent flow** from the **New tool** pane.

    ![image](https://github.com/user-attachments/assets/a5525413-1e4c-4c1c-86f2-e4d10f7e117f)

3.	Select the trigger step **When Copilot Studio calls a flow** and select **+ Add an input -> Text**.

    ![image](https://github.com/user-attachments/assets/126a2024-bcb4-4578-b8bc-3a0cca2ef9bb)

    ![image](https://github.com/user-attachments/assets/5ebe42ae-bb29-4fa6-b0cc-184822fae620)


4.  Enter the below details

    - Input - +++**PropertyId**+++

    - Please enter your input **-** +++**Property**+++

5.  Select **+ Add an input -> Text**

    - Input - +++**ViewerName**+++

    - Please enter your input **-** +++**Viewer Name**+++

6.  Select **+ Add an input ->** **Text**.

    - Input - +++**ViewerEmail**+++

    - Please enter your input **-** +++**Viewer Email**+++

    ![image](https://github.com/user-attachments/assets/ce3b9312-09ae-4064-acde-e35e7fc371fa)

7.  Select the **+** icon between the two steps to **Add an action**.

    ![image](https://github.com/user-attachments/assets/30667e36-0039-403a-ad95-e81197cee81c)

8.  Enter +++**Dataverse**+++ in the **Search** field and select **See more** for the Dataverse connector.

    ![image](https://github.com/user-attachments/assets/adf523d0-0413-4173-b35f-df710393ff49)

9. Select the **Add a new row** action.

    ![image](https://github.com/user-attachments/assets/5620c785-e8f4-41f3-85a4-0a058cca6803)

10. Select **Booking Requests** for table name.

11. Enter +++**Copilot booking**+++ in the **Booking Name** field.

12. Select **Show all**.

    ![image](https://github.com/user-attachments/assets/bc44a8e8-86db-4129-a67e-15b297856390)

13. Enter +++contoso_bookingrequests()+++ in the **Property (Real Estate
    Properties)** field, move the cursor within the brackets, and
    use **Dynamic content**.

    ![image](https://github.com/user-attachments/assets/fc1ac1cd-0154-4430-8c3c-a373e15bb2a6)

14. Select the **PropertyId** parameter.

    ![image](https://github.com/user-attachments/assets/0e4bf761-6d67-4b85-b378-356f84db388e)

15. Use **Dynamic content** to select the **ViewerName** parameter for
    the **Viewer Name** field.

    ![image](https://github.com/user-attachments/assets/28330aa9-c881-497c-869d-9a7beec65475)

16. Use **Dynamic content** to select the **ViewerEmail** parameter for
    the **Viewer Email** field.

    ![image](https://github.com/user-attachments/assets/f50d3377-031a-45b9-90dd-30e4a60a8f8c)

17. The parameters will now look similar to those in the screenshot
    below.

    ![image](https://github.com/user-attachments/assets/c7654468-5a69-45c6-b099-8af4bb91381d)

18. Select **Save draft**.

    ![image](https://github.com/user-attachments/assets/152d0dc7-7381-4698-ba4b-4a6badcf5a19)

19. Once saved, select **Publish**.

    ![image](https://github.com/user-attachments/assets/866bf76e-fc89-4c8c-888c-0e4b1c1ebbca)

### Task 4: Add a Copilot action for creating a booking request

1.	Select **Flows** from the left pane and select the **Untitled** flow.

    ![image](https://github.com/user-attachments/assets/a0dd4b2d-7f4c-448a-94b0-e8bc22deacbd)

2.	Select **Edit** in the **Details** pane.

    ![image](https://github.com/user-attachments/assets/136dae62-8cae-49f7-97d7-52bcd0b39662)

3.	Provide the **Flow name** as +++Booking Request+++.

    ![image](https://github.com/user-attachments/assets/a919cc94-7f38-4499-9ca2-64ce41495fc2)

4.	Select the **Topics** tab of the **Real Estate Booking Service** agent and select the **Book a Real Estate Showing** topic.

    ![image](https://github.com/user-attachments/assets/27b77599-755e-4a6f-9535-0b2f880b219a)

5.  Select the **+** icon below the **What date and time do you want to
    see the property?** node and select **Add a tool**.

6.  Select the **Booking Request** flow.

    ![image](https://github.com/user-attachments/assets/8daf7daa-faa5-4af4-8735-1616a408d93f)

7.  Select the **PropertyId** variable for the **PropertyId** input
    parameter.

    Select the **Name** variable for the **ViewerName** input parameter.

    Select the **EmailAddress** variable for the **ViewerEmail** input
parameter.

    ![](./media/image76.png)

8. Select the **+** icon below the action node. Select **Topic
    management**, then select **Go to another topic** and select **End
    of conversation**.

    ![](./media/image77.png)

9. Select **Save**.

    ![](./media/image78.png)

10. Once saved, select **Publish** and select **Publish** again in the
    confirmation dialog.

    ![](./media/image79.png)

    ![image](https://github.com/user-attachments/assets/e65b1d1a-e965-4a19-896b-942c8fa7cbbb)

## Exercise 3: Test the agent 

### Task 1: Test the agent and make a booking request

1.  Select the **Test** button in the top-right of the screen to open
    the testing panel. Select the **three dots** at the top of the
    testing panel in the top-right of the screen. Select **Track between topics**.

    ![](./media/image81.png)

2.  When the **Conversation Start** message appears, your agent starts a
    conversation.

3.  In response, enter a trigger phrase for the topic that you created:

    +++I want to book a real estate showing+++

4.  The agent responds with the "**What is your name?**" question.

5.  Enter your name.

    ![](./media/image82.png)

6.  Then enter your email when it prompts for the email. After you enter
    the details, a question asking if the information is correct, and
    options to select **Yes** or **No** is prompted. Select **Yes**.

    ![](./media/image83.png)

7.  Select **House** for the type of property prompt.

8.  Enter +++**2**+++ for the number of bedrooms prompts.

    ![](./media/image84.png)

9.  Enter +++Tomorrow 2:00 PM+++ to the **What date and time do you want
    to see the property?** prompt.

10. Select **Yes** to the **Did that answer your question?** prompt.

11. Select any rating.

12. Select **No** to the **Can I help with anything else?** prompt.

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
improve your agent's responses.

### Task 1: Enable Generative AI

1.	Back in the **Copilot Studio** (+++https://copilotstudio.microsoft.com+++), select the agent **Real Estate Booking Service**.

2.  Select **Settings** in the top-right of the screen.

    ![](./media/image89.png)

3.  Select the **Generative AI** tab.

4.	Select **Yes** under **Use generative AI orchestration for your agent's responses?**

    ![image](https://github.com/user-attachments/assets/3443d165-7e92-4a05-b261-311947fec3ce)

5.	Scroll down and set the **content moderation** to **Moderate**.

    ![image](https://github.com/user-attachments/assets/6afe1c3b-225e-45f7-8e3b-78b20679f5be)

5.  **Close** the Settings pane.

    ![image](https://github.com/user-attachments/assets/5bd15c02-127b-43e4-be44-b6354481b2ab)

### Task 3: Add knowledge from a website

1.  Click on the **Overview** tab.

2.  Select **+ Add knowledge** under the **Knowledge** section.

    ![image](https://github.com/user-attachments/assets/e837007a-4ad5-476d-af2b-0b73590ab189)

3.  Select the **Public websites** tile.

    ![image](https://github.com/user-attachments/assets/46ebeaff-1c8e-48c7-8192-35a69da8edc1)

4.  Enter the public website link +++https://create.microsoft.com/templates/real-estate+++.
    Select **Add**.

    ![image](https://github.com/user-attachments/assets/68bf412b-96a1-40fe-a674-e670999c083e)

5.  Give the name +++Real Estate Website+++ in the **Name** field and then
    select **Add**.

    ![image](https://github.com/user-attachments/assets/a14d61e4-72d1-4ddf-9c35-e50893a9d3cc)

### Task 4: Add knowledge from Dataverse

1.  Select the **Knowledge** tab. Select **+ Add knowledge**.

    ![](./media/image97.png)

2.  Select **Dataverse**.

    ![image](https://github.com/user-attachments/assets/420eac9d-0a4d-4285-a7a4-4e5c9a9b8ced)

3.  Select the **Real Estate Property** table and select **Next**.

    ![image](https://github.com/user-attachments/assets/7495d3c6-aee1-4fb8-b411-d74cd6858f18)

4.	Select **Add**.

    ![image](https://github.com/user-attachments/assets/fad4c5bb-7ae4-42cf-b210-5a2ce5205b12)

### Task 5: Add knowledge from files

1.  From the **Knowledge** tab, select **+ Add knowledge**.

    ![](./media/image102.png)

2.	Under **Upload file** section, select **select to browse** and browse to locate the file **SummitRealtyCaseStudy.docx** at **C:\LabFiles** and select it.

    ![image](https://github.com/user-attachments/assets/7e513e99-d5c1-4175-978e-0ccfc3503ef3)

3.  Select **Add**.

    ![image](https://github.com/user-attachments/assets/a972620f-efc5-4786-9fe1-8218586832ed)

    >[!Alert] **Important:** The file upload will complete and the indexing will take some time to complete. Check the status in the Knowledge tab to ensure that the file is available. 
    
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

1.  Select the **Overview** tab.

2.  Select **Settings** in the top-right of the screen.

    ![](./media/image118.png)

3.  Select the **Security** tab and then select
    the **Authentication** tile.

    ![](./media/image119.png)

4.  Select Authenticate with Microsoft **(Entra ID authentication in
    Teams and Power App)**.

5.  Select **Save**.

    ![](./media/image120.png)

6. Select **Save**.

    ![](./media/image121.png)

7. Select **Close**.

    ![](./media/image122.png)

8. Select the **Overview** tab.

9. Select **Publish** and select **Publish** again in the dialog.

    ![](./media/image123.png)

### Task 8: Test the agent's knowledge

1.  Select the **Test** button in the top-right of the screen to open
    the testing panel.

    <img width="464" alt="image" src="https://github.com/user-attachments/assets/02150627-c16e-4acb-a166-b69abb58b5cf" />

2.	Select **Activity map** if not selected already.

    ![image](https://github.com/user-attachments/assets/bca2d292-6a00-4a0b-a52f-8be552c0ac64)

3.	Select the **Refresh** button in Test Panel to **Start a new conversation**.
   
4.	Type in +++What is Summit Realty group?+++ and hit **send**.
   
5.	You will get a response from the uploaded file as in the screenshot below since it has been added as the knowledge source to look for in the Fallback topic.

    ![image](https://github.com/user-attachments/assets/23fdd440-901c-476b-bf98-90456b95dc78)

**Summary:**

In this lab, we have learnt to

- Use entities and slot filling

- Implement Flow actions

- Add knowledge to the agent

- Enable Generative AI
