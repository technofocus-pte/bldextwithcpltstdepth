# Lab 8 - Create an agent in Copilot Studio with Dataverse MCP Server

Create and configure a Copilot Agent in Copilot Studio with Dataverse
MCP Server integration to streamline business workflows.

After completing this lab, participants will be able to create and
configure a Copilot Agent in Copilot Studio, integrate the Dataverse MCP
Server to read and update account information from the Account and
Contact table, structure agent responses for clarity and business value,
and apply these skills to solve common business challenges.

## Task 1: Create and Configure Copilot Agent 

Build a Copilot Agent that connects to Dataverse through the MCP Server
for seamless data access.

In this section, you’ll learn how to create a new Copilot Agent in
Copilot Studio, configure it with proper instructions and suggested
prompts, and integrate the Dataverse MCP Server for live data
connectivity

1.  Open a browser and navigate to Copilot Studio using the url saved in Lab 2 (+++https://copilotstudio.microsoft.com/environments/< Environment ID >+++ and login using your credentials if not done already.

    ![](./media/image1.png)

2.  Select **Create an agent** tile to create a new agent.

    ![](./media/image2.png)

3.  Once the agent is provisioned, select Edit against the **Details**
    pane.

    ![](./media/image3.png)

4.  Enter the below details and select **Save**.

    - Name - +++Zava Agent+++
    
    - Description - +++This agent will help Contoso sales reps update their accounts and contacts using the Dataverse MCP Server+++

    ![](./media/image4.png)

5.  **Edit** Instructions and enter the below set of instructions and
    select **Save**.

    ```
    This agent will: Read accounts and contact information from the Account
    and Contact Tables in Dataverse using the Dataverse MCP Server. Update
    accounts and contact information from the Account and Contact Tables in
    Dataverse using the Dataverse MCP Server. Create new accounts and
    contact information in the Account and Opportunity Tables in Dataverse
    using the Dataverse MCP Server. Do not use outside knowledge. Only use
    the Dataverse MCP Tool to create, read, update and delete.
    ```
    
    ![](./media/image5.png)
    
    ![](./media/image6.png)

6.  Select **+ Add knowledge** to add a knowledge source. Browse and choose **Account data.xlsx** from C:\LabFiles and seelct **Add to agent**.

    ![](./media/image33.png)

    ![](./media/image34.png)
    
6.  Scroll down and select **+ Add suggested prompts** in the Suggested
    prompts section.

    ![](./media/image7.png)

7.  Add the following prompts and then click **Save**.

    - **Title**: +++Account Search+++ **Prompt**: +++List all accounts in Redmond+++
    
    - **Title**: +++Contact Search+++ **Prompt**: +++List all contacts from Coho Winery+++

    ![](./media/image8.png)

8.  Select **+ Add tool** from the Tools section.

    ![](./media/image9.png)

9.  Select the **Model Context Protocol** tab, search for +++Microsoft Dataverse MCP Server (Preview)+++ and select **Microsoft Dataverse MCP Server (Preview)**.

    ![](./media/image29.png)

10. Create new connection if prompted and then select **Add and configure**.

    ![](./media/image30.png)

    ![](./media/image31.png)

    ![](./media/image32.png)

    **Note:** The Dataverse MCP Server will allow you natural language
access to your tables in Dataverse. We have sample data in the Accounts
and Contacts tables that we will use. The tools available are: list
tables, describe table, read data, create record, update record, list
prompts, execute prompt, list knowledge sources, and retrieve knowledge

12. Review the tools available for the Dataverse MCP Server. You can
    select and deselect which tools are available to the agent. When the
    tool is executed, the list is dynamically updated from the MCP
    Server. You cannot call an MCP Server from a Topic for this reason.

    ![](./media/image12.png)

13. Ensure that the **knowledge source** you had added earlier is in the **Ready** state. Open the **Test** pane and enter +++Upload data to Accounts table using the Account data tracker+++

    ![](./media/image36.png)

14. For the first run, you would get a Consent dialog as by default the
    tool is configured to use “End user credentials”. Please click **Allow** to
continue.

    ![](./media/image14.png)

15. If the knowledge source takes a very long time to get to the Ready state, copy few rows from the tracker and send it in the Test pane to be added to he Account table.

    ![](./media/image37.png)
    
13. Now, enter +++List the accounts in the state of WA+++ in the **Test**
    pane and click **Send**.

    ![](./media/image38.png)

15. See the series of actions that take place and the output from the
    MCP server.

    ![](./media/image39.png)
    
    ![](./media/image40.png)


## Task 2: Structure Agent Responses with Custom Prompts

Create custom prompts to ensure consistent, structured responses from
your agent that provide business-relevant information.

1.  To have a more structured response, you can create a **prompt**
    in the **Tools**. In the **Tools** tab, click **+ Add a tool** then, select **Prompt**.

    ![](./media/image18.png)
    
    ![](./media/image41.png)

3.  Rename the **prompt** **name** at the top to +++Show Account Details+++ .

    Then in the **instructions** enter, +++Find account which contains+++
    and then click **+ Add content** to pass in the name of the account we
    are searching for. Select **Text** for the Input and call it
    +++**Account Name**+++ . Click **close**.

    ![](./media/image21.png)

    ![](./media/image22.png)

4.  We can now grab specific fields from Dataverse to show to our end
    users in the chat. Click back in the instructions and enter +++and find relevant details like:+++ click **+ Add content**. This time we will select **Dataverse** and some of the fields in the **Account** table which we feel our end users would like to see about the account.

    ![](./media/image23.png)

5.  Let’s select the following by clicking on the dropdown: **Account
    Name**, **Account Number**, **Address 1**, **Annual Revenue**,
    **Email** and **Main Phone**. Click **Add** and then **Save**.

    ![](./media/image24.png)
    
    ![](./media/image25.png)
    
    ![](./media/image26.png)

6.  Select **Add and configure**.

    ![](./media/image27.png)

7.  Now we can test out our prompt. Let’s go back over to our agent and
    test again. Go to the test pane.

8.  Enter +++Show account Details for Northwind Traders+++ and click
    **Send**. You can see that the response is in the structured
    response with the custom prompt created.

    ![](./media/image42.png)

## Summary

In this lab, you built a Copilot Agent in Microsoft Copilot Studio that
integrates with the **Dataverse MCP Server** to securely access and
manage business data using natural language. You configured the agent to
read, create, and update records across Dataverse tables such as
**Accounts, Contacts, and Opportunities**, without relying on external
knowledge or custom APIs.

You also learnt how to **structure agent responses** using custom
prompts, ensuring consistent, business-friendly outputs that surface the
most relevant data fields for end users. Now, you can design an agent that streamlines sales and account management workflows,
delivers clear and structured insights, and demonstrates how MCP-powered
agents can solve real-world business challenges with live enterprise
data.
