
# Lab 9 - Test, measure, and improve AI agents

As AI agents take on critical roles in business processes, the need for
reliable, repeatable testing becomes essential. Agent evaluation lets
you generate tests that simulate real-world scenarios for your agent.
These tests cover more questions faster than manual, case-by-case
testing. Then, you can measure the accuracy, relevancy, and quality of
answers to the questions the agent is asked, based on the information
the agent can access. By using the results from the test set, you can
optimize your agent's behavior and validate that your agent meets your
business and quality requirements.

**Objective**

In this lab, you will learn how to systematically test and evaluate an
AI agent using Copilot Studio’s built-in evaluation and analytics
capabilities. You will create an automated test set that simulates
real-world user scenarios, measure the quality and accuracy of agent
responses, and analyze performance data to identify gaps and improvement
opportunities. By the end of the lab, you will be able to validate that
your agent meets business, reliability, and quality standards before
production use.

## Task 1: Create a test set to evaluate your agent

Before deploying an AI agent into real business workflows, it is
critical to validate how well it responds to realistic user questions.
Manual testing is time-consuming and often misses edge cases. In this
task, you will use Copilot Studio’s agent evaluation capabilities to
automatically generate a test set that simulates real-world scenarios.
You will run these tests against your agent, review pass and fail
outcomes, and identify gaps in accuracy, relevance, or behavior that
need improvement.

1.  From the Copilot Studio, select the **Hiring agent**.

![](./media/image1.png)

2.  From the top menu bar, select **Evaluation**. Select **Create a test
    set**.

![](./media/image2.png)

3.  There are few options to create the test set. Select **Generate 10
    questions** in this case.

![](./media/image3.png)

4.  **Review** the test set and then **Save** the test set.

![](./media/image4.png)

5.  Now, click on **Evaluate** to evaluate the agent.

![](./media/image5.png)

6.  Select your tenant id and click on **Run**.

![](./media/image6.png)

7.  Wait till the execution completes.

![](./media/image7.png)

8.  Once the evaluation is complete, click on it to view the details.

![](./media/image8.png)

9.  Go through each question and see why it has failed and which ones
    have passed. This will help you enhance your agent as required.

![](./media/image9.png)

## Task 2: Gain insights with agent analytics

Once an agent is evaluated and actively used, ongoing monitoring is
essential to ensure consistent performance and reliability at scale. In
this task, you will explore the Analytics capabilities in Copilot Studio
to gain insights into agent usage, execution trends, and component
utilization. You will learn how analytics data helps identify
performance bottlenecks, understand user interaction patterns, and guide
continuous optimization of your agent over time.

1.  From the top menu bar, select **Analytics.**

> ![](./media/image10.png)

2.  When there are a greater number of executions and as the agent gets
    used more and more, the traffic increases, and you can find the AI
    Summary in the Analytics tab.

> ![](./media/image11.png)

3.  The **Overview** section gives an overall picture about the runs,
    and credits.

> ![](./media/image12.png)

4.  The Run outcomes gives the average duration trends.

> ![](./media/image13.png)

5.  Scroll down and under the Use section, you can find the usage of
    triggers, tools and knowledge sources.

> ![](./media/image14.png)

6.  Each of these helps you to gauge the usage of each component of the
    agent and upgrade, enhance or correct the agent functionalities
    appropriately.

## Summary

In this lab, you implemented automated evaluation and analytics to
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
