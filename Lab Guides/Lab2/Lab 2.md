# Lab 02 - Configure the Dynamics 365 Customer Service

**Objective**

In this lab, you will create a security group in Azure to update
settings in Copilot Studio and then activate the **Dynamics 365 Customer
Service trial**.

## Task 1: Create Security Group in Entra ID and Configure Copilot Studio Authors

1.  Navigate to the Azure portal at
    +++<https://portal.azure.com/+++%C2%A0and> login with your tenant
    credentials present in the Resources tab.

    ![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

    ![A screenshot of a computer login AI-generated content may be incorrect.](./media/image2.jpeg)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image3.png)

2.  Select **Next** in the Keep your account secure window and follow
    the **prompts**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Download the Authenticator app in your phone if you do not have it
    already.

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  Follow the prompts and complete the setup.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image7.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  In the Azure welcome screen, select **Get Started**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  Search for and select +++Microsoft EntraID+++.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  From the left pane, select **Manage** -\> **Groups**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  Select **New group** to create a new security group.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  Enter the below details

    - Group type – Select **Security**

    - Group name – Enter +++**copilotagentsecurity**+++

    - Microsoft Entra roles can be assigned to the group –
      Select **Yes** (If this option is not visible, ignore this step)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. Select **No owners selected**, select the **MOD Administrator** from
    the **Add owners** page and click on **Select**.

    ![A screenshot of a group AI-generated content may be
    incorrect.](./media/image15.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image16.png)

11. Similarly, select **No members selected**, and add the **MOD
    Administrator** from the list and click on **Select**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. Select **No roles selected**. If you **do not** see this **option**,
    ignore this and the next step.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. Search for and select +++**Global admin**+++ and select **Select**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. Select **Create** once all the details are added and
    select **Yes** in the confirmation dialog.

    ![A screenshot of a group AI-generated content may be
    incorrect.](./media/image20.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image21.png)

15. Ensure that you get a **success** message.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. Select Contoso|Groups from the top left.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

17. Select **Properties** under **Manage** from the left pane.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image24.png)

18. Toggle Yes in **can manage access to all Azure subscriptions and
    management groups in this tenant** option and then click **Save**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image25.png)

19. Now, select **Roles and administrators** under **Manage** from the
    left pane.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

20. Search for +++privileged role admin+++ and select the **Privileged
    Role Administrator** role.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image27.png)

21. Select **+ Add assignments**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image28.png)

22. Select the **MOD Admin id** and select **Add**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image29.png)

23. From a new tab, navigate to
    +++https://admin.powerplatform.microsoft.com/+++.
    Select **Manage** from the left pane and then select the **Tenant
    Settings** option.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

24. Select **Copilot Studio Authors** from the list available.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

25. Click on the **Edit** icon to edit the settings.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

26. Search for and select the **+++copilotagentsecurity+++** group that
    you created earlier.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

27. Select **Save** to save the settings.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

## Task 2: Sign up for Dynamics 365 Customer Service trial

1.  Login to
    +++https://dynamics.microsoft.com/en-us/customer-service/overview/+++

2.  Login using the **Office 365 Tenant details** from
    the **Resources** tab if prompted.

3.  Click on **Try for free**

    ![A person in a vest and glasses AI-generated content may be
incorrect.](./media/image35.png)

4.  Enter your **Office 365 Administrative Username** from
    the **Resources** tab, select the check box and click on **Start
    your free trial**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

5.  Enter the region as **United States**, enter your **Phone
    number** and click on **Submit**.

    ![](./media/image37.png)

6.  If you see an option to Launch Trial for Engage customers, click
    on **Launch Trial**.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image38.png)

7.  Once activated, your Customer Service workspace will get opened.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

**Summary**

In this lab, we have activated the Dynamics 365 Customer Service which
will be used in the **Lab 04 - Integrate an agent with the Dynamics 365
Customer Service app and implement automated case escalation to the live
agent**. 
