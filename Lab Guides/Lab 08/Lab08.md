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

5.  Select **Agents**.

    <img width="558" alt="image" src="https://github.com/user-attachments/assets/fe25742c-82d5-48a7-8ebb-f801dd925055" />

6.  Select **New agent**.

    <img width="565" alt="image" src="https://github.com/user-attachments/assets/90b450c2-251f-4f41-a3fc-79a9b5efb0bc" />

8.  Click on **Skip to configure** in the agent creation screen.

    ![image](https://github.com/user-attachments/assets/7e096b69-e7f6-446d-900d-a2e19ccae7fd)

9.  Provide the below details and select **Create**.

    - Name - +++Conversational action+++
    - Description - +++This agent helps to retrieve the list of holidays for the year 2025+++
    - Instruction –

    ```
    Answer based on this Holiday list
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

    ![image](https://github.com/user-attachments/assets/15b063e1-0b3f-494e-9a4e-9cd3324e3947)

9.  Under **Suggested prompt** section, add a prompt with Title - +++July+++ and Prompt - +++Leaves in July?+++ and select **Save**.

    <img width="476" alt="image" src="https://github.com/user-attachments/assets/e1ceef94-9836-4a6d-b7da-bbb38bfc98b6" />

10. Under **Test Agent**, you can see the prompt. Select it to see it in action.

    ![image](https://github.com/user-attachments/assets/703ebf71-d399-4fce-84e3-f2769bee2f1f)

11.	Select **Publish**.

    <img width="476" alt="image" src="https://github.com/user-attachments/assets/5cef3535-62c6-4ae1-b45a-e8840a689dc3" />

11. Select **Publish** from the Publish pane.

    ![image](https://github.com/user-attachments/assets/5162d4af-32ea-42c7-89c7-c6eb0efaeda7)

    ![image](https://github.com/user-attachments/assets/f94170e2-0ec7-4f45-8005-9db13c64ff97)

11. Select the option, **Download zip file** and click **Done**.

    ![image](https://github.com/user-attachments/assets/40bc7e0f-29e8-4f72-8757-4f2aa499638d)

12. Open **MS Teams**.

13. Select **Apps -> Manage your apps**.

    <img width="459" alt="image" src="https://github.com/user-attachments/assets/89a629c4-1ed7-4cf6-a4f8-d5ab6068e91f" />

14. Select **Upload an app** and browse and upload the downloaded file.

    ![image](https://github.com/user-attachments/assets/a75be53d-3f7d-4319-adfb-b510da4314e4)

    ![image](https://github.com/user-attachments/assets/77b4f79f-8e42-4599-86bd-6e3e3634e82f)

15. Once uploaded, select **add**.

    ![image](https://github.com/user-attachments/assets/b7b3b076-5a04-453a-be1c-605a2a15056f)

    ![image](https://github.com/user-attachments/assets/b61f7054-511f-44af-adfb-c8567589c5c4)

16. **Open** the app once added.

    ![image](https://github.com/user-attachments/assets/2892998c-4fa7-4427-a016-01b8c6a1ee79)

17. See the agent in action.

    ![image](https://github.com/user-attachments/assets/db722127-40f0-4fc2-9316-f8e296032c4d)

    ![image](https://github.com/user-attachments/assets/9ad99afd-6982-4cc8-afff-f933c56588dd)


**Summary:**

In this lab, we have learnt how to create a conversational action and to
publish it.
