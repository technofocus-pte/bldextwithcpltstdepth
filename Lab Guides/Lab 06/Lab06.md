# **实验室06_Creating和从 Teams 部署 Microsoft Copilot Studio Copilot**

**实验室持续时间** – 30 分钟

**目的:**

在本实验中，您将在 Microsoft Teams 中安装 Copilot Studio
应用程序，在团队中创建新的 Copilot 并对其进行测试。

## **练习 1： 在 Microsoft Teams 中安装 Copilot Studio 应用程序**

1.  从 VM 中选择 **Start** 菜单，搜索 +++teams+++，然后选择 **Microsoft
    Teams apps** 。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  从 **Resources** 选项卡中使用您的凭证登录。

![A screenshot of a sign in Description automatically
generated](./media/image2.png)

3.  点击 **Apps**。搜索 +++**Copilot Studio**+++ 并选择 **Microsoft
    Copilot Studio** ，然后单击 **Add**。

**注意：** 如果您找不到 Copilot Studio，则必须搜索并选择 **Power Virtual
agent** 并添加它。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![](./media/image4.png)

4.  点击 **Open**。

![A screenshot of a phone Description automatically
generated](./media/image5.png)

5.  单击 **Start now** 。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

## **练习 2：在团队中创建新的 Copilot**

1.  使用 **Office 365 tenant credentials 登录到** **Teams**。

> ![A screenshot of a sign in Description automatically
> generated](./media/image7.png)

2.  点击 **Apps**。搜索 +++**Copilot Studio**+++ 并选择 **Microsoft
    Copilot Studio** ，然后单击 **Add**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![A screenshot of a phone Description automatically
generated](./media/image4.png)

**重要提示：** 如果您找不到 Copilot Studio，则必须搜索并选择 +++**Power
Virtual agent**+++ 并添加它。

![A screenshot of a search engine Description automatically
generated](./media/image8.png)

![A screenshot of a computer Description automatically
generated](./media/image9.png)

3.  单击 **Start now**。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  选择 **Contoso** 并单击 **Continue**。

![A screenshot of a chatbot Description automatically
generated](./media/image10.png)

![A screenshot of a chatbot Description automatically
generated](./media/image11.png)

**重要提示：** 此步骤可能需要大约 10
分钟。如果花费的时间太长，请关闭它，从左侧窗格中的应用程序中选择 Copilot
Studio 或 Power Virtual Agents，然后重做步骤 4。

5.  在 Create a copilot 窗格中，将 Copilot 的名称配置为 +++**HR Support
    Copilot**+++，然后单击 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

6.  获取一条成功消息，指出 **Your chatbot is provisioned**。

![](./media/image13.png)

## **练习 3：为常见的休假查询构建员工休假主题**

1.  单击 左侧窗格中的 **Topics**。单击 **+ New topic -\> From blank。**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  暂时 **Close** Trigger phrases 窗格。

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

3.  单击 **Details** 图标。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

4.  在 Details 窗格中，为常见的休假查询提供 +++**Employee time off**+++
    （名称） 和 +++**Employee time off topic for common time-off
    queries**+++（Description）。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

5.  **关闭** Details 窗格。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

6.  点击 **Save**。

![A screenshot of a chat Description automatically
generated](./media/image19.png)

7.  单击 **Trigger phases。**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

8.  添加触发短语 +++ **I need help with time off** +++，然后单击 **+。**

![](./media/image21.png)

9.  添加以下rigger phrases。

- +++**Need information on time off**+++

- +++**How many days of paid vacation do I have**+++

- +++**What are the national holidays**+++

- +++**I need extended leave**+++

![A screenshot of a computer Description automatically
generated](./media/image22.png)

关闭 Trigger phrases 窗格。

10. 添加 Message 节点并输入文本 +++I can help with questions related to
    time-off+++.

> ![A screenshot of a chat Description automatically
> generated](./media/image23.png)

11. 作为 HR 员工，您知道最常见的休假问题是关于 **paid vacation** 时间和
    **national holidays**
    的。当添加具有用户响应选项的问题节点时，主题会自动为每个响应获取一个分叉分支。

12. 选择消息节点下方的 （**+**） 图标，然后选择 **Ask a question**
    以将问题节点添加到主题。输入 *What information are you looking
    for? *在 **Ask a question** 文本框中。

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)

13. 在 **Options for user** 下，添加 +++ Paid vacation+++ 和 +++
    National Holidays+++ 作为两个选项。

> ![A screenshot of a questionnaire Description automatically
> generated](./media/image25.png)

14. 用户选择存储在变量中，主题根据用户选择的选项进行分支。您可以重命名变量，以便在主题中更好地跟踪它。

15. 在变量上，在 **Save response as** 下，选择铅笔图标以编辑变量属性。

16. **Variable** **properties** 窗格随即打开。将变量重命名为
    +++TimeoffType+++。关闭 **Variable properties**
    窗格，您会看到创作区域中反映的更改。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

17. 为带薪休假分支添加消息节点，并向用户发送此消息: +++**For paid
    vacation time-off, go to www.contoso.com/HR/PaidTimeOff**+++ to
    submit time-off requests.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

18. 在 **National Holidays** 路径中，添加包含以下文本的消息节点:

2025 年国定假日:

- New Year’s Day: Jan 1

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

![](./media/image28.png)

19. 点击 **Save**。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

![A screenshot of a chat window Description automatically
generated](./media/image30.png)

## **练习 4：测试 Copilot 的预期行为**

1.  选择屏幕顶部的 **Copilot/Power Virtual Agent** 图标以启动测试
    Copilot 画布。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

2.  在 copilot 聊天中键入 **I need time off information**。

3.  选择 **Paid vacation**。

4.  您将根据我们的配置收到响应。

> ![A screenshot of a chat Description automatically
> generated](./media/image32.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)
>
> **总结：**
>
> 在此实验室中，我们学习了将 Copilot Studio 应用程序添加到 Teams 并在
> Teams 中创建经典机器人。
