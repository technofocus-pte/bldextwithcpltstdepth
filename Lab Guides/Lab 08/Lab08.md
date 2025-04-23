**实验 08 - 为 Microsoft Copilot 创建对话actions**

**实验室持续时间** – 20 分钟

**目的**

Microsoft Copilot
提供开箱即用的体验，以与整个组织的内容和资源互动。在某些情况下，需要回答并与外部系统交互。使用
Microsoft Copilot Studio，您可以创作可作为 Copilot
插件发布的对话主题。在您的租户管理员批准插件后，可以将其添加到您组织的
M365 聊天体验中。

如果组织拥有相同的有效许可证，则这些作将在生产中的 Microsoft Copilot
中可用。

在本实验中，我们将学习如何创建对话作。

## **练习 1：创建对话作**

1.  使用您的租户凭据登录到
    +++**https://copilotstudio.microsoft.com/**+++（如果尚未登录）。

2.  从右上角选择 **Dev one** 作为环境。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  从 左侧窗格中选择 **Agents**。

4.  选择 **Copilot for Microsoft 365**。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

5.  选择 **Actions**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

6.  选择 **Add an action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

7.  在 **New action pane** 中选择 **Conversational**。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

8.  将作的名称设置为 !!**Conversational action**!!.选择 **Create**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  准备就绪后，创建的作将在 Authoring canvas 中打开。选择 **Topics**。

10. 如果它没有打开，请刷新页面并查看它是否列在 **Library** -\>
    **Conversation** 下。

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image7.png)

11. 打开 **Conversational action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

12. 将主题命名为 !!Holidaylist!!

![A screenshot of a computer Description automatically
generated](./media/image9.png)

13. 在 Trigger
    节点的描述中，明确描述对话插件如何帮助用户以及它可以做什么。让本主题帮助用户找到
    2025 年的假期列表。

键入 +++ **This plugin helps to retrieve the list of holidays for the
year 2025.**+++ 在 Trigger 节点的描述中。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

此描述具有功能用途，Microsoft Copilot 使用它来确定是否调用您的插件。

14. 添加包含假日列表的 message 节点。

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

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

15. 单击 **Save** 以保存插件。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

![A screenshot of a chat box Description automatically
generated](./media/image13.png)

## **练习 2：将聊天作发布到 Microsoft Copilot**

1.  发布对话插件会在 Dataverse
    注册表中为您的租户创建一个新插件。在那里可用后，租户管理员需要批准您的插件可供
    Microsoft Copilot 插件目录中的用户使用。

2.  单击 **Publish**。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

3.  选择 **Publish。**

![A screenshot of a computer program Description automatically
generated](./media/image15.png)

4.  在 **Publish latest content** 对话框中选择 **Publish** 。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

5.  发布状态显示在屏幕上。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

注意： 发布应该会很快完成。Microsoft Admin Center
中的实际可用性最多可能需要 4 小时。

**重要提示： ：** 要让管理员在管理中心列出它，公司必须持有有效的 Copilot
许可证。

6.  您的管理员可以 在 **Microsoft Admin Center** 的 设置 下找到
    **Dataverse and Microsoft Copilot Studio** 集成应用，然后选择
    **Integrations to be reviewed and approved**。

7.  租户管理员批准 Dataverse 和 Microsoft Copilot Studio
    集成应用后，它应显示在其 Microsoft Copilot UI 的用户插件列表中。

**总结：**

在本实验中，我们学习了如何创建对话作并发布它。
