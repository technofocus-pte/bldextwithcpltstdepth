<img width="540" height="361" alt="image" src="https://github.com/user-attachments/assets/f5f3e088-7880-4ebc-9362-5efd52c7e4a5" /># Lab 03 – Create Safe Travels agent from Template

**Objective**

**Agent templates** are designed to help you get started with a **custom agent**. You are responsible for assessing all safety and legal implications of using an agent template and customizing it as appropriate for your business.

An agent built from the **Safe Travels agent template** is a Business-to-Employee (B2E) agent designed to provide employees of a company with **travel assistance**. This agent helps ensure employees are well-prepared and informed for their next work trip. This agent uses natural language processing to offer a conversational interface, making it easy and intuitive for employees to access the information they need. However, the default website used by the agent currently only covers US travel destinations. You can replace the default website with your own knowledge source.

In this lab, you will create an agent from the **Safe Travels template** and enhance it in Lab 05.


## Exercise 1: Create Safe Travels agent from template

In this exercise, you will create the agent in Copilot Studio using the Safe Travels agent template.

1.  From a browser, login to +++https://copilotstudio.microsoft.com+++.
    The Start free trial page opens up. Select your country and click
    **Start free trial**.

    ![](./media/image1.png)

2.  Select the **Dev One** environment.

    ![image](https://github.com/user-attachments/assets/7a2b18ab-7d57-44f6-a6a4-2993d60bbcd8)

    >[!Alert] **Important** If the Copilot Studio does not show up the option to select **Environment** as in the below screenshot, then follow the below steps.
    >
    >![A screenshot of a computer AI-generated content may be incorrect.](./media/im30.png)
    >
    > Open +++https://admin.powerplatform.microsoft.com/+++. Select **Manage** -> **Environments -> Dev One** and select the value of the **Environment ID**.
    >![A screenshot of a computer AI-generated content may be incorrect.](./media/im6.png)
    >
    > Navigate back to the Copilot Studio tab and open +++https://copilotstudio.microsoft.com/environments/**< EnvironmentID >**+++   (Replacing **< EnvironmentID >** with the value fetched above)

3.  Select Skip in the Welcome screen.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im31.png)
    
3.  Select **Agents** from the left pane and then select the **Safe Travels** template under **Start with an agent template**. 

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im32.png)

5.  The Safe Travels template creates a new agent that is designed to
    provide employees of a company with travel assistance. 

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  Browse through the set-up page. Under **Knowledge**, you can find
    that **US Travel Website** is already added as a Knowledge source.
    It can be edited if needed. Here, we are using the same website.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  Select **Create** to create the Safe Travels agent. We are not
    changing anything here and using the template as such. At any point,
    the agent can be upgraded as per the user requirements.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  The **agent** gets **created** and opens up automatically showing up
    the **Overview** page.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

9.  In the Test pane, enter +++How to apply for passport?+++ and hit
    **Send**.

    The Test pane is open by default. If not, click on the Test icon on top
right.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

10. You can see that the agent provides information on how to apply for
    the passport from its knowledge source.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image10.png)

## Exercise 2: Publish the agent to Teams and Microsoft 365 Copilot

In this exercise, you will **publish** the agent created in Copilot Studio to the **Microsoft Teams** and **Microsoft 365 Copilot** channel.

1.  Open **MS Teams** +++https://teams.microsoft.com/v2/+++ from a browser and **login** using your tenant credentials from the **Resources** tab.

1.  Back in the Copilot Studio, select **Publish** from the top right of the agent page.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im33.png)

2.  Check the **Force newest version** checkbox and then select **Publish** in the confirmation dialog.

    ![](./media/im34.png)

    ![](./media/im35.png)
    
4.  Select **Channels** from the top navigation bar.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

5.  Select **Teams and Microsoft 365 Copilot** from the list of
    available channels.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

6.  Select **Add channel**.

    ![](./media/image15.png)

7.  Click on the **See agent in Teams** option add the agent to the
    Teams.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

8.  This opens up the agent in the Microsoft Teams. Select **Cancel** in the **This site is trying to open Microsoft Teams** pop up and then select **Use the Web App instead** option.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

9.  Select **Add** to add the agent.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

10.  Once added, you will get an option to open the agent. Select
    **Open**.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image19.png)

11.  Test the agent from Teams.

    ![](./media/image20.png)

11. Back in the Copilot Studio, close the Teams and Microsoft 365
    Copilot channel window.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)














