# Lab 3 - Architecting intelligent agents with knowledge grounding and live connectors

**Introduction**

Modern users expect intelligent, contextual responses that go beyond
simple keyword matching. This lab will guide you through creating an
intelligent agent that can reason across multiple knowledge sources and
perform real-time actions to deliver comprehensive, accurate answers.

**Objective**

In this lab, you’ll build an intelligent assistant that goes beyond
simple Q&A to deliver contextual, multi-part responses. By the end of
the lab, you will

Create an intelligent agent using the conversational creation
experience. Configure agent tone, behavior, and instructions to reflect
your brand. Add public websites like Wikipedia as knowledge sources for
factual grounding. Disable general knowledge to reduce hallucinations
and ensure accuracy.

## Task 1: Create a new agent and add knowledge

Create Nova AI with custom instructions and Wikipedia knowledge
integration using Copilot Studio’s conversational setup experience.

1.  Open a browser and navigate to Copilot Studio at +++https://copilotstudio.microsoft.com+++ if not logged in already.

    -   Username - +++@lab.CloudCredential(M365).AdministrativeUsername+++
      
    -   Password -  +++@lab.CloudCredential(M365).AdministrativePassword+++

4.  From the Home page, select **Agent**.

    ![](./media/image48.png)

5.	Enter the Name as +++Researcher agent+++ and select **Create**.

    ![](./media/image49.png)
  	
5.  Once the agent is created, select **Edit** against **Details**.

    ![](./media/image50.png)

6.  Enter the below **Description** and select **Save**.

    - +++Answers multi-part questions by combining historical facts, biographical data, and real-time information like weather. Ideal for deep research, exploration, and knowledge synthesis+++

      ![](./media/image51.png)

7.  Select **Edit** against **Instructions**, enter the below content and select **Save**.

    >[!Note] **Note:** Use the **Copy** option and then **Paste** it in the required place in the VM (Instructions Text area in this case)

    ```
    You should answer complex questions using verified public information and real-time lookups like weather or conversions. You should give clear, concise answers and handle multiple questions one at a time. You must not speculate, share unverified or sensitive information, or compare products or companies. You should communicate clearly and professionally, using a friendly tone and light emojis when appropriate.
    ```
    
    ![](./media/image4.png)

9.  Scroll down and select **+ Add knowledge** to add a knowledge
    source.

    ![](./media/image5.png)

10. Select the **Public Website** option form the list.

    ![](./media/image6.png)

11. Enter +++https://en.wikipedia.org+++, select **Add**, and then select **Add to agent**.

    ![](./media/image7.png)
    
    ![](./media/image8.png)

14. Enter the below message in the Test pane and click **Send** and
    observe the output.

    +++Write a draft email to request refund from a toaster that is not working properly (bread keeps burning)+++

    ![](./media/image11.png)
    
    ![](./media/image12.png)

## Task 2: Add weather connector

In this task, you will add a weather connector to enable real-time data
retrieval and test generative orchestration. Ensure that the agent
provides only fact-based, controlled responses while enabling it to
perform real-time actions like weather lookups for comprehensive,
multi-step answers.

1.  Select **Tools** tab from the top menu.

    ![](./media/image13.png)

2.  Enter +++MSN Weather+++ in the search box and select **Get current
    weather**.

    ![](./media/image14.png)

3.  Select the drop down next to the **Not connected** message and
    select **Create new connection**. Then, select **Create** in the
    next screen.

    ![](./media/image15.png)
    
    ![](./media/image16.png)

4.  Select **Add and configure** to add the tool to the agent and
    configure it as required.

    ![](./media/image17.png)

5.  Once added, select **Additional details**.

    ![](./media/image18.png)

6.  Under Credentials to use, select **Maker-provided credentials**.

    **Note:** When using Maker-provided credentials, the end-user of the
agent isn’t prompted to use its own context and connection to connect to
the service. Instead, it’s using the context and connection of the
person who has configured the agent. - Only use author authentication
for actions that don’t need user-specific data, as using the credentials
from someone else can expose to data exfiltration risks. - Use user
authentication for role based access scenarios - Always review security
implications of authentication choices

    ![](./media/image19.png)

7.  Under **Inputs**, **Units**, -> **Fill using** -> select **Custom
    value**, and choose **Metric**.

    ![](./media/image20.png)

8.  Under **Inputs**, for **Location**, leave **Fill using to
    Dynamically fill with AI**, and select **Customize** to set
    description.

    ![](./media/image21.png)

9.  Set the description as below and then select **Save**.

    ```
    The location for the weather query. Valid inputs are City, State, Country. Always include city and country, and state only for locations where appropriate (e.g., in the US)
    ```
    
    ![](./media/image22.png)
    
    ![](./media/image23.png)

10. Test your enhanced agent with this complex question:

    +++Who is the current CEO of the company that owns GitHub? Where did they earn their MBA? What's the average rent for a one-bedroom apartment near that campus? What's the air quality index in that area today?+++

    ![](./media/image24.png)

11. Notice how generative orchestration performs multiple searches and
    triggers the weather connector to provide a comprehensive answer

    ![](./media/image25.png)

## Task 3: Fine-tune your AI assistant for smoother conversations

Customize system topics to enhance interactions and deliver a smoother
user experience.

In this section, you’ll customize built-in system topics to improve user
interactions and create a more seamless experience beyond just knowledge
sources.

Customize your assistant’s welcome message to make it more engaging, add
suggested start prompts to guide users effectively, and refine system
topics like Escalate to ensure they align with your organization’s
needs.

1.  From the top menu, select **Topics**.

    ![](./media/image26.png)

2.  Select the **Conversation Start** topic under **System**.

    ![](./media/image27.png)

3.  In the topic’s **Message** node, enter the below message.

     +++Hi there! I'm Researcher agent, your intelligent assistant for deep  research and discovery. I can break down complex questions and combine insights from historical facts, biographies, and real-time data like the weather. What are you curious about today?+++

    ![](./media/image28.png)

4.  Still in the same node, select **+ Add** -> **Quick reply**.

    ![](./media/image29.png)

5.  Add the below question.

    +++What caused the fall of the Roman Empire?+++

    ![](./media/image30.png)

6.  Similarly add 2 more (Select **+ Add** in the quick reply **Properties** pane that gets opened).

    ![](./media/image47.png)
    
    +++Who is the current CEO of the company that owns GitHub? Where did they earn their MBA? What's the average rent for a one-bedroom apartment near that campus? What's the air quality index in that area today?+++

    +++What's the temperature in the city that hosted the last Olympic Games?+++

    ![](./media/image31.png)

8.  Once added, select **Save** to save the topic.

    ![](./media/image32.png)

9.  Customize the escalation experience. Select **Topics** -> **System** -> **Escalate**.

    ![](./media/image33.png)

10. Update the text to the below, that will more meaningfully unblock
    the end user and select **Save**.

    +++I'm sorry, but I can't seem to be able to help you. I recommend reaching out to our Microsoft Copilot Studio community at https://aka.ms/CopilotStudioCommunity or submitting a support request at https://learn.microsoft.com/en-us/power-platform/admin/get-help-support.+++

    ![](./media/image34.png)

## Task 4: Make your agent public and publish it to the demo website

In this section, you’ll remove authentication to make your agent
publicly accessible, then publish it to the demo website for testing and
sharing.Since the Researcher agent provides general information and
doesn’t handle private data, you’ll disable authentication for a
seamless user experience and publish it to the demo website to gather
feedback before deploying to your real site.

>[!Alert] **Important:** Since this is a test environment used for training purposes, there might be issues in getting the agent published, based on any recent changes to the product. If that happens, there will be issues in executing the  exercises that follow. This will not be the case in the production.

1.  Go to **Settings** .

    ![](./media/image35.png)

2.  Select **Security** -> **Authentication**. Select **No
  authentication** and then select **Save**.

    ![](./media/image36.png)

3.  Select **Save** in the confirmation prompt.

    ![](./media/image37.png)

4.  You can now close the Settings pane.

    ![](./media/image38.png)

5.  Select **Publish** to make your changes live.

    ![](./media/image39.png)

6.  Select **Publish** in the confirmation dialog.

    ![](./media/image40.png)

7.  You will get a success message once the publish is done.

    ![](./media/image41.png)

8.  Now, select **Channels** from the top menu.

    ![](./media/image42.png)

9.  Select **Demo website** from the list of channels available.

    ![](./media/image43.png)

10. Enter the Welcome message as +++Welcome to your demo website+++ and
    select **Save**.

    ![](./media/image44.png)

11. Click on **Open demo website** to open your site.

    ![](./media/image45.png)

12. You can now interact with your agent.

    ![](./media/image46.png)

## Summary

In this lab, you successfully delivered a public-facing intelligent
agent that:

- Answers complex, multi-part research questions

- Uses verified public knowledge and real-time connectors

- Minimizes hallucinations through controlled knowledge sources

- Provides a polished, user-friendly conversational experience

- Is deployed and accessible via a live demo website

This lab demonstrates how to design, enhance, and publish a
**production-ready intelligent agent** that goes beyond simple Q&A to
deliver trustworthy, real-time, and context-aware insights.











