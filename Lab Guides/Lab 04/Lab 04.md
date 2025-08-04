# 实验 04 - 将代理与 Dynamics 365 Customer Service 应用程序集成，并实施自动案例升级到实时代理

## 目的

此实验室详细介绍了将对话从代理升级到人工代理的步骤。

**[！重要提示**：仅当已按照**实验 02 - 配置 Dynamics 365** 客户服务启用
Dynamics 365 试用版时，才能执行此实验

## 练习 1：配置 Dynamics 365 Customer Service 工作区

### 任务 1：配置全渠道 Power Virtual 代理扩展

1.  打开链接
    +++https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++ ，然后单击
    全渠道 Power Virtual 代理扩展 页面中的 Get it now。

    ![](./media/image1.png)

2.  使用 **Resources** 选项卡中的租户凭证登录。

    ![](./media/image2.png)

3.  单击 **Get it now**。

    ![](./media/image3.png)

4.  在 **Select an environment** 下选择 **CustomerService
    Trial**，选中复选框并单击 **Install**。

    ![](./media/image4.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

## 任务 2：在 Power Platform 管理中心配置搜索设置

1.  使用您的租户详细信息登录
    +++https://admin.powerplatform.microsoft.com/+++。从左侧窗格中选择
    **Manage**，然后从环境列表中选择 **CustomerService Trial**
    environment。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  选择 **Settings**从顶部窗格中。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  选择 **Product** -\> **Features**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  将 **Dataverse Search** 和 **Single table search** 选项切换为
    **ON**，然后选择**Save**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

## 练习 2：创建代理

1.  在 Copilot Studio 主页
    +++https://copilotstudio.microsoft.com/+++
    中，从右上角选择 **CustomerService Trial** 环境。

    ![](./media/image10.png)

2.  从左侧窗格中选择 **Agents**。单击 **+ New Agent** 创建新代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  在 Type your message text 区域中，键入 **+++You are a Customer
    service agent that help identify some stores.+++**
    然后点击**send**。

    ![](./media/image12.png)

4.  代理可能会为正在创建的代理建议
    **Name**。要么接受它，要么建议一个新名字。

5.  输入消息 **+++Maintain a polite tone+++**接下来，然后点击 **Send**。

    ![](./media/image13.png)

6.  单击 **Create**。

    ![](./media/image14.png)

7.  创建的代理将打开一条消息，**Your agent is ready**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## 练习 3：将 Copilot 连接到 Dynamics 365 Customer Service 并配置“升级”主题

### 任务 1：配置 Escalate 主题

我们在这里重点介绍升级到实时代理的概念。因此，我们将直接朝着这个方向努力，而不会创建任何其他新主题。

1.  选择 **Topics** 选项卡，然后选择 **System** 选项卡。选择
    **Escalate** 主题。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  选择主题的 message 节点，并将现有内容替换为 +++You will be
    transferred to a live agent shortly+++

    ![](./media/image17.png)

3.  单击 + 符号以在 Message 节点旁边添加一个节点。

4.  选择 **Topic management** -\> **Transfer conversation**。

    ![](./media/image18.png)

5.  发送消息 +++The customer wants to talk to a live agent+++在 Transfer
    conversation 节点中。

    ![ ](./media/image19.png)

6.  **Save** 主题。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  **Publish** 代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### 任务 2：将 Copilot 连接到 Dynamics 365 Customer Service

1.  发布后，从 copilot 页面右上角单击“**Settings**”。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  选择 **“Security**”，然后在 **“Security”** 下选择
    “**Authentication**”。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  选择 **No authentication** 选项，然后单击 **Save** 。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  在 确认对话框中选择 **Save** 。

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  关闭 **Settings** 窗格。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

6.  单击 **Channels** （如果 Channels 不可见，请单击 +1 以查看
    **Channels** 选项）

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  从 Customer engagement 中心窗格中选择 **Dynamics 365 Customer
    Service**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  在 Dynamics 365 Customer Service 页面上，单击 **Connect**。

    ![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  收到 **successfully connected** 的消息后，单击 **Close**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## 练习 4：在 Dynamics 365 管理中心中创建工作流和渠道

### 任务 1：在 Customer Service 全渠道中管理用户

1.  使用您的管理员租户凭据登录到
    +++https://admin.powerplatform.microsoft.com+++/。从左侧窗格中选择
    **Manage**。在 **Environments**下选择 **CustomerService Trial**
    environment。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  单击 **Environment URL** 下的 **url value**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  从标题栏中选择 **Customer Service workspace**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  这将打开 **Apps** 页面。从中选择 **Customer Service admin center**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  这将打开 **Dynamics 365 Customer Service admin center** 页面。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

### 任务 2：配置工作流

1.  在管理中心页面中，从左侧窗格中的 **Customer
    support** 下选择**Workstreams** ，然后选择 **+ New
    workstream** 选项。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

2.  选择 **Inbound**

    ![](./media/image37.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

3.  填写以下详细信息，向下滚动并单击 **Create**。

    - 名字 - +++**New Workstream**+++

    - 所有者 – **MOD Administrator** (默认选中)

    - 类型 – **Messaging**

    - 渠道 – **Chat**

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image39.png)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  创建工作流后，单击 **Set up chat ** 以设置聊天渠道。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  在 **Live chat setup – Channel details** 屏幕中，填写以下详细信息。

    - 名字 - +++**Chat Channel**+++

    - 语言 – **英语 - 美国**

    ![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  向下滚动并单击 **Next**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  接受接下来 2 页中的默认值，直到您到达 Chat widget 屏幕。在 Live chat
    setup – Chat 小部件屏幕中，提供名称 **+++Store Locator
    Assistant+++**，接受其他默认值，然后单击 **Next**。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  在 **Live chat setup – Behaviors** 屏幕中，接受默认值，然后单击
    **Next**。

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  在 **Live chat setup – User features** 屏幕中，将 **File
    attachment** and **Voice and video calls** 选项切换为
    **off**，然后单击 **Next**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. 接受 Notification 屏幕中的默认值，然后单击 **Next** 。

11. 在 **Live chat setup – Review and finish** 屏幕中，选择 **Create
    channel**。

    ![](./media/image47.png)

12. **复制 Live chat setup – Success** 屏幕中显示的小组件的值
    ，并将其**Save**
    在记事本中，以将其添加到即将进行的练习中的网页中。然后，单击
    **Done** 完成配置。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### 任务 3：将代理添加到工作流

1.  返回 **New Workstream** 页面，向下滚动并单击 Bot 部分中的 **+ Add
    bot**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  从 添加机器人 屏幕上的副驾驶列表中，选择 **Store Locator Assistant**
    代理，然后单击 **Connect**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  确保将机器人添加到工作流中，如下面的屏幕截图所示。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  从左侧窗格中，选择 **AI Agents**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  确保 **Store locator** 代理已连接。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## 练习 5：创建网页并测试升级到代理

1.  使用您的租户管理员凭据[登录到
    +++https://make.powerpages.microsoft.com/+++>。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  确保您处于 **CustomerService Trial**环境中。

3.  单击 **Get started**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  单击  **Tell us about yourself** 页面中的 **Skip**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  在下一页向下滚动，然后单击 **Start with a template**
    选项以开始使用模板创建站点。

    ![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  选择一个模板，然后单击 **Choose this template**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  在 为您的网站命名 文本框中，输入名称 **+++Contoso Store
    assistant+++**，接受其他默认值，然后单击 **Done**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  创建站点后，单击 **Edit**。

    ![](./media/image60.png)

9.  单击 **Company name** 标题中的 ** Edit site header** 。

    ![](./media/image61.png)

10. 在 **Edit site header** 窗格中，将 站点标题 提供为 **+++Contoso
    Store assistant+++** 并关闭对话框。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. 单击 页面右上角的 **Edit code**。

    ![](./media/image63.png)

12. 单击 **Open Visual Studio Code**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

13. 单击 **Allow**。 如果需要，请使用您的租户凭据 **Login**。

    ![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

14. 网页的 Home page 将在 Visual Studio Code 中打开。

    ![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

15. 滚动到文件末尾。将
    创建工作流时复制的 **script** 添加到此文件的最后一行之后。

    ![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

16. 保存文件，关闭 Visual Studio Code 选项卡并返回到 Power 页面。单击
    **Sync**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. 同步完成后，选择 **Preview** -\> **Desktop。**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

18. 您的网页将在新选项卡中打开。在 网页右下角找到嵌入到页面的 **Store
    Locator Assistant**。**点击**它。

    ![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

19. 输入 +++Talk to agent+++。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

20. 在 Customer Service admin 页面中，单击 **Customer Service admin
    center**，然后从中选择应用 **Customer Service workspace**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

21. 在 Customer Service workspace 页面中，您将收到一个 **chat
    request**。 **接受**它。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

22. 接受后，聊天屏幕将打开，其中包含我们在 Escalate
    主题中提供的消息。我们还可以将用户在此处提供的任何其他信息添加到实时代理中。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

23. 如果您想了解实时代理与客户之间的聊天，请模拟其工作原理，然后结束。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image77.png)

## 总结

在本实验中，我们学习了

- 从 Copilot Studio 构建代理并配置 Escalate 主题。

- 将代理发布到 Dynamics 365 工作区，并将其集成到网页中。

