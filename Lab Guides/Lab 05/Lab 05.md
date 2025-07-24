# 实验室 05 – 增强 Safe Travels 代理并实施多代理编排

## 目的

您在上一个实验中使用 Copilot Studio 中提供的模板创建了一个名为 **Safe
Travels**
的代理。在本实验中，您将了解如何增强该代理以满足特定客户的需求。

在此过程中，您将学习 Copilot Studio 中的代理流创建和多代理编排的概念。

## 练习 1 – 测试现有的 Safe Travels 代理

在本练习中，我们将测试 **Safe Travels**
代理，以了解当被问及差旅批准时，代理如何回答。

1.  从浏览器以 +++https://copilotstudio.microsoft.com+++ 打开 **Copilot
    Studio**。导航到 **Dev One** 环境并打开 **Safe Travels** 代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  选择 **Test** 图标以测试代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  在 Test 窗口中输入 +++Need travel approval +++，然后单击 **Enter**。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image3.png)

4.  您可以看到，代理使用通用指令集进行响应，以便获得旅行批准。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image4.png)

## 练习 2 – 使用公司特定的知识资产增强代理

在本练习中，我们将添加特定于 Contoso 的知识资产 - **Travel Policy** 。

1.  在代理的 概述 页面中，向下滚动并选择 **+ Add knowledge**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

2.  单击 **select to browse** 选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

3.  从 **C：\Labfiles** 文件夹中，选择 **Travel Policy.docx** 然后单击
    **Open**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

4.  单击 **Add** 以添加文件。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

> ![A screenshot of a computer error AI-generated content may be
> incorrect.](./media/image9.png)

5.  确保已添加文件。请等待状态从 **In progress** 更改为 **Ready**
    ，然后再继续下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

## 练习 3 – 在 Microsoft Teams 中创建团队和频道

在本练习中，我们将在 MS Teams
中创建一个团队和一个频道，差旅审批请求将发送到该团队和频道。

1.  打开 Microsoft Teams 并从左侧窗格中选择“**See all your
    teams**”选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

2.  选择 **Create team** 以创建新团队。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  将 团队名称 输入为 +++**HR Team**+++，将 第一个渠道名称 输入为
    +++**Travel Approval Channel**+++，然后选择 **Create**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  在 Add members to HR Team 对话框中选择 **Skip**。

![A screenshot of a email AI-generated content may be
incorrect.](./media/image15.png)

现在，团队和渠道创建已完成。

## 练习 4 – 创建代理流

在本练习中，我们将创建一个新的 AgentFlow 来将差旅请求发布到 Teams 渠道

1.  从 左侧窗格中选择 **Flows**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  选择 **New agent flow** 以创建新流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

3.  选择 **Add a trigger**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

4.  在 **AI capabilities**下选择 **When an agent calls the flow**。

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image19.png)

5.  选择 **+ Add an input**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

6.  选择 **Number** 并将其命名为 +++**Employee ID**+++。然后选择 **+ Add
    an input**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image22.png)

7.  现在，选择一个 **Text** input 并将其命名为 +++**Purpose**+++。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

8.  选择 **Add an action** 在触发器节点下方。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

9.  搜索 +++**Teams**+++，然后单击 Teams作组下的 **See more**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

10. 选择 **Post message in a chat or channel** 。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image26.png)

11. 选择 **Sign in** 并使用 您的凭证 login。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

12. 选择以下详细信息

发布为 – 选择 **User**

Post in – 选择 **Channel**

团队 – 选择 **HR Team**

Channel – 选择 **Travel Approval Channel**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image29.png)

13. 在 Message 字段中，输入以下内容

\`\`\`

> Travel Request from
>
> Employee ID - \<Employee ID\>
>
> Purpose - \<Purpose\>
>
> \`\`\`
>
> 将 **\<Employee ID\>** 和 **\<Purpose\>** 替换为动态内容变量
> **Employee ID** 和 **Purpose**，如下面的屏幕截图所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

14. Parameters 选项卡现在如下所示。

![](./media/image32.png)

15. 关闭 Parameters 选项卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

16. 在 Post message 节点后添加另一个action。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image34.png)

17. 在 **Skills** 下选择 **Respond to the agent**。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image35.png)

18. 选择 Add an output。将其命名为 +++**Output**+++，并将值输入为
    +++**Request submitted**+++。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

19. 单击 **Save draft** 以保存流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

20. 保存流程后，选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

21. 确保流程已发布。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

22. 单击 代理流程的 **Overview** 选项卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

23. 选择 **Edit，**然后在 **Details** 窗格中将流命名为 +++Request Travel
    Approval Flow+++。选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

## 练习 5 – 将代理流程作为工具添加到代理

在本练习中，我们将创建代理流程添加到代理 Safe Travels
中，以便利用流程功能。

1.  从左侧窗格中，选择 **Agents**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

2.  选择 **Safe Travels** 代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

3.  在 Overview 页面中向下滚动，然后选择 **Add tool**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

4.  选择已创建的 **Request Travel Approval Flow**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

5.  选择 **Add to agent**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

6.  添加后，该流将列在代理的 **Overview** 页面的 **Tools** 部分下。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

## 练习 6 – 创建主题

在本练习中，我们将创建一个 Topic 以使用创建的差旅审批流程。

1.  从 顶部菜单中选择 Topics。选择 **+ Add a topic -\> Add from
    description with Copilot**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

2.  输入以下详细信息，然后选择 **Create**。

**Name** - +++Travel Approval+++

**Create a topic to** - +++This topic should get the Employee ID
(Number) and Purpose of travel (Text) details from the user and invoke
the Tool "Request Travel Approval Flow"+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

3.  **主题**将按如下方式创建。

![](./media/image50.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image51.png)

4.  查看是否实际调用了 Flow。在这种情况下，仅添加一个 Message
    节点，说明已调用流。在这种情况下，请删除此类 Message
    节点，然后单击向用户请求 Purpose 的节点后的 Add a node 图标。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

5.  选择 **Add a tool** -\> **Request Travel Approval Flow**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  为流变量 **Employee ID** 添加变量 **EmployeeID。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  同样，添加 Purpose of travel 输入。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  添加 **Send a message** 节点，并向其添加 Output
    Variable，如下面的屏幕截图所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  选择 **Save**，然后选择 **Publish** 以发布代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image60.png)

10. 在 确认对话框中选择 **Publish**。

![A close-up of a white background AI-generated content may be
incorrect.](./media/image61.png)

11. 选择 测试 图标，输入 +++Travel Approval +++ 并从测试窗格发送。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

12. 通过向代理提供以下详细信息进行交谈

> 员工 ID – +++1234+++
>
> 旅行目的 - +++Client meeting for finalizing proposal of XYZ project+++

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image63.png)

13. 您将从代理处收到 **Request submitted** 消息。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image64.png)

14. 打开 Teams 频道，您将看到那里发布的旅行批准的详细信息。

![](./media/image65.png)

## 练习 7 – 创建 Leave Management 代理 

在本练习中，我们将构建一个休假管理代理，该代理可用于了解休假、员工的休假余额等。

1.  在 Copilot Studio 主页上，选择 **Agents -\> + New agent**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

2.  选择 **Skip to configure**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  在配置页面中，输入以下详细信息，然后选择 **Create**。

    - 名字 - +++Leave Manager Agent+++

    - 描述 - +++This agent is to track the leaves of all the employees,
      their leave balance and leave history to approve or reject any new
      leave requests.+++

    - 指示 - +++Track the leaves of employees. Track their leave
      balance. Apply/Reject leaves based on their balance.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  创建代理后，在 概述 页面中向下滚动，然后选择 **Knowledge** 部分下的
    **Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  点击 **select to browse**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  从 C：\Labfiles 中选择文件 **Leave balance Tracker**，然后单击
    **Open**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  选择 **Add** 将跟踪链接添加到代理。

![](./media/image72.png)

8.  文件已添加。请等待状态为 Ready，然后再继续下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

9.  从主题选项卡中选择 **+ Add a topic -\> Add from description with
    Copilot**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

10. 输入以下详细信息，然后单击 **Create**。

- 名字 - +++Leave Balance Checker+++

- 创建主题以 - +++Get the Employee ID from the user and check and reply
  with the leave balance based on the tracker added as knowledge
  source+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

11. 检查主题是否具有用于获取员工 ID 的节点，然后单击
    **Save**。在这里，我们有一个用于获取 Employee ID 的节点和一个
    Message 节点，用于声明正在检索余额。

> 检查主题一次，然后删除除上述节点之外已创建的其他节点。

然后 **Save** 主题。

![](./media/image76.png)

12. 发送消息 +++ Check Leave balance+++ 从 Test 窗格中。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image77.png)

13. 输入 +++1234+++ 作为员工 ID。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image78.png)

14. 检查代理的响应。这是从添加到代理的知识资产中检索的。

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image79.png)

15. 选择 Publish 并等待代理发布。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 练习 8 - 在 Copilot Studio 中实施多代理编排

组织现在可以在 Copilot
Studio（预览版）中构建多代理系统，而不是依赖单个代理来完成所有工作，或在孤岛中管理断开连接的代理，代理可以在其中相互委派任务。这包括使用
Microsoft 365 代理生成器、Microsoft Azure AI 代理服务和 Microsoft Fabric
构建的设备。这些代理现在可以协同工作以实现一个共同的目标：完成跨系统、团队和工作流的复杂关键业务任务。

在本练习中，我们将把 Leave management 代理添加到 Safe Travels
代理中，该代理可用于在计划旅行时了解休假。

1.  从 Copilot Studio 中选择 **Safe Travels** 代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  我们将首先测试这个代理，看看它可以在 leaves 上提供什么信息。在 Test
    窗格中，输入 +++Check Leave balance+++ 并按 Enter。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

3.  您可以看到，代理会提供有关如何检查休假余额的一般信息。在执行此作时，它还引用了
    Travel Policy 文档。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image83.png)

4.  从 顶部菜单中选择 **Agents** 选项卡，然后选择 **+ Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

5.  在 **“Choose how do you want to extend your agent”** 下，选择
    **“Copilot Studio**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

6.  从列表中，选择 **Leave Manager
    Agent**。只有在发布后才能添加它。如果它正在发布过程中，请稍候。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

7.  选择 **Add agent** 将此代理添加到 **Safe Travels**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

8.  添加代理后等待几分钟，然后单击 **Publish**。

![](./media/image89.png)

9.  发布代理后再等待几分钟，然后在 **Safe Travels** 代理的 Test
    窗格中输入 +++Check Leave balance+++。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

10. 您可以看到 **Leave Manager** 代理是自动访问的，并且代理回答了
    **Leave Manager** 代理主题中的 **Enter Employee ID** 问题。

11. 将员工 ID 输入为
    +++1234+++，您可以看到座席根据休假管理器座席的知识资产进行回复。

![](./media/image91.png)

## 总结

在本实验中，我们学习了如何增强从模板创建的代理以满足个人需求。我们还学习了在
Copilot Studio 中实施多代理编排
