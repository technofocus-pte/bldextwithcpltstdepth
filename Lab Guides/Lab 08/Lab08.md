# **Lab 08 - Creating conversational actions for Microsoft Copilot**

**Lab duration** – 20 minutes

**Objective**

Microsoft Copilot provides out of the box experiences to engage with
content and resources from across your organization. In some situations,
answers and interaction with external systems are required. With
Microsoft Copilot Studio, you can author a conversational topic that can
be published as a Copilot Plugin. Once your Tenant Admin approves the
Plugin, it can be added to your organization's M365 Chat experiences.

The actions will be available in the Microsoft Copilot in production, if
the organization has valid license for the same.

In this lab, we will learn how to create a Conversational action.

## **Exercise 1: Create a Conversational action**

1.  Login to +++**https://copilotstudio.microsoft.com/**+++ using your
    tenant credentials if not already logged in.

2.  Select the environment as Dev one from top right if not selected already.

    ![](./media/image17.png)

3.	Select **Agents** from the left pane.
   
4.  Select **Copilot for Microsoft 365**.

    ![](./media/image1.png)

5.  Select **Actions**.

    ![](./media/image2.png)

6.  Select **+ Add an action**.

    ![](./media/image3.png)

7.  Select **Conversational** in the **New action** pane.

    ![](./media/image4.png)

8.  Provide the name for the action as +++**Conversational action**+++.
    Select **Create**.

    ![](./media/img31.png)

9.  Once ready, the created action opens in Authoring canvas. Select
    **Topics**.

    ![](./media/image7.png)

10.	If it does not open up, refresh the page and see if it is listed under **Library -> Conversational**.

    ![](./media/img32.png)
   	
11.  Name the topic as +++Holidaylist+++

    ![](./media/image8.png)

12.  In the Trigger node’s description, provide a clear description of how the conversational plugin can 
     help the user and what it can do. Let this topic help the user to find the list of holidays in the  
     year 2025.
     
     Type +++**This plugin helps to retrieve the list of holidays for the year 2024.**+++ in the Trigger 
 node’s description.

     ![](./media/image9.png)

     This description has functional purpose and is used by the Microsoft Copilot to determine whether to 
 invoke your plugin or not.

13. Add a message node with the list of holidays.
    Copy the below to a notepad and then paste it into the Message node from there.

    ```
    National holidays for 2025:
    - New Year’s Day:	Jan 1

    - Martin Luther King Jr. Day: Jan 20

    - Washington’s Birthday (Presidents’ Day): Feb 17

    - Memorial Day: May 26

    - Juneteenth National Independence Day: June 19

    - Independence Day: July 4

    - Labor Day: Sep 1

    - Columbus Day / Indigenous Peoples’ Day: Oct 13

    - Veterans Day: Nov 11

    - Thanksgiving Day: Nov 27

    - Christmas Day: Dec 25

    ```
    
    ![](./media/img33.png)

12. Click on **Save** to save the plugin.

    ![](./media/image11.png)

    ![](./media/image12.png)

## **Exercise 2: Publishing your conversational action to Microsoft Copilot**

1.  Publishing your conversational plugin creates a new plugin in the
    Dataverse registry for your Tenant. Once available there, your
    tenant admin needs to approve your plugin to be available to users
    in the Microsoft Copilot plugins catalog.

2.  Click on **Publish**.

    ![](./media/image13.png)

3.  Select **Publish.**

    ![](./media/image14.png)

4.  Select **Publish** on **Publish latest content** dialog.

    ![](./media/image15.png)

5.  The publish status is shown on the screen.

    ![](./media/image16.png)

    >[!Note] Note: The publish should complete quickly. The actual availability in
the Microsoft Admin Center can take up to 4 hours.

    >[!Alert] **Important:** **:** For the admin to get it listed in the admin center,
the company will have to hold a valid Copilot license.

6.  Your Admin can find the **Dataverse and Microsoft Copilot
    Studio** integrated app in the Microsoft Admin Center
    under **Settings**, then **Integrations to be reviewed and
    approved**.

7.  Once your Tenant admin approves the Dataverse and Microsoft Copilot
    Studio integrated app, it should appear in the user's list of
    plugins in their Microsoft Copilot UI.

**Summary:**

In this lab, we have learnt how to create a conversational action and to
publish it.
