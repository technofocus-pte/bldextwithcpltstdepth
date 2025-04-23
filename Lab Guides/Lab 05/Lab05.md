# 实验 05 - 将代理与 Dynamics 365 Customer Service 应用程序集成，并实施自动案例升级到实时代理

## 练习 1：配置 Dynamics 365 Customer Service workspace

### 任务 1：配置全渠道 Power Virtual 代理扩展

1.  打开链接
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com>+++，然后单击全渠道
    Power Virtual Agent 扩展 页面中的 立即获取。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image3.png)

2.  在 **Select an environment** 下选择 **CustomerService
    Trial**，选中复选框并单击 **Install**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

3.  在 Dynamics 365 应用页面中，单击显示**Update
    available**的条目，**select** **check
    box**以同意条款，然后单击**Update**。

确保对 **Update available** 作为 Status 的**所有**条目执行此作。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

![A screenshot of a computer Description automatically
generated](./media/image6.png)

### 任务 2：在 Power Platform 管理中心配置搜索设置

1.  使用您的租户详细信息登录
    +++<https://admin.powerplatform.microsoft.com/>+++。选择
    **Environments -\> CustomerService Trial**。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  选择 **Resource** （在顶部窗格中） 旁边的下拉列表，然后选择
    **Dynamics 365 apps**。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  确保 **Installed Omnichannel for Customer Service**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

4.  导航回管理中心的 **Environments -\> CustomerService
    Trial**页面。选择 **Settings** 从顶部窗格中。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  选择 **Product** -\> **Features**。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  将 **Dataverse Search** 和 **Single table search** 选项切换为
    **ON。**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

向下滚动并单击 **Save** 右下角的按钮。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

## 练习 2：创建代理

1.  来自 Copilot Studio 主页 !!https://copilotstudio.microsoft.com!!
    从右上角选择 **CustomerService Trial** Environment。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  从左侧窗格中选择 **Agents**。单击 **+ New Agent** 创建新代理。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

3.  在 Type your message text 区域中，键入 **!!You are a customer
    service agent who helps in identifying stores nearby.!!** 然后点击
    **Send**。

![A screenshot of a chat Description automatically
generated](./media/image16.png)

4.  输入消息 **!!Maintain a polite tone!!** 下一步，然后点击**Send。**

![A screenshot of a chat Description automatically
generated](./media/image17.png)

5.  单击 **Create**。

![A screenshot of a chat Description automatically
generated](./media/image18.png)

6.  创建的代理将打开一条消息， **Your agent is ready**。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

## 练习 3：将 Copilot 连接到 Dynamics 365 Customer Service 并配置“升级”主题

### 任务 1：配置 Escalate 主题

我们在这里重点介绍升级到实时代理的概念。因此，我们将直接朝着这个方向努力，而不会创建任何其他新主题。

1.  选择 **Topics** 选项卡，然后选择 **System** 选项卡。选择
    **Escalate** 主题。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

2.  选择主题的消息节点，并将现有内容替换为 **!!You will be transferred
    to a live agent shortly!!**

![A screenshot of a computer Description automatically
generated](./media/image21.png)

3.  单击 + symbol以在 Message 节点旁边添加一个节点。

4.  选择 **Topic management** -\> **Transfer conversation**。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  留言 !!The customer wants to talk to a live agent!! 在 Transfer
    conversation 节点中。

![A screenshot of a chat Description automatically
generated](./media/image23.png)

6.  **Save** 主题。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  **Publish** 代理。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

### 任务 2：将copilot连接到 Dynamics 365 Customer Service

1.  发布后，从 copilot 页面右上角单击**Settings**。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

2.  选择 **Security**，然后在 Security下选择 **Authentication**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  选择 **No authentication** 选项，然后单击 **Save** 。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  在 确认对话框中选择 **Save** 。

![A screenshot of a computer screen Description automatically
generated](./media/image29.png)

5.  关闭 **Settings** 窗格。

6.  单击 **Channels** （如果 Channels 不可见，请单击 +1 以查看
    **Channels** 选项）

![A screenshot of a chat Description automatically
generated](./media/image30.png)

7.  从 Customer engagement 中心窗格中选择 **Dynamics 365 Customer
    Service。**

![](./media/image31.png)

8.  在 Dynamics 365 Customer Service 页面上，单击 **Connect**。

![A screenshot of a message Description automatically
generated](./media/image32.png)

9.  收到 **successfully connected**的消息后，单击 **Close**。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

## 练习 4：在 Dynamics 365 管理中心中创建工作流和渠道

### 任务 1：在 Omnichannel for Customer Service中管理用户

1.  登录 !!https://admin.powerplatform.microsoft.com!!
    使用您的管理员租户凭证，然后从左侧选项卡中选择 **Environments**。
    此处将列出 **CustomerService Trial。Select**它。

![A screenshot of a computer Description automatically
generated](./media/image34.png)

2.  单击 **Environment URL** 下的 **url value**。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

3.  这将打开 **Apps** 页面。从中选择 **Customer Service admin center**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

4.  这将打开 **Dynamics 365 Customer Service admin center** 页面。

![A screenshot of a customer service Description automatically
generated](./media/image37.png)

5.  在 **Dynamics 365 Customer Service admin center**
    的站点地图中，选择** Customer support** 组下的 User management
    **Customer support**。

6.  在 **User management** 页面上，选择 **Users** 旁边的 **Manage**。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

7.  单击 **Enabled Users** 旁边的下拉列表，然后选择 **Omnichannel
    Users**。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

8.  在 **Omnichannel Users** 页面上， 在列表中选择用户 **MOD
    Administrator**。

![A screenshot of a computer Description automatically
generated](./media/image40.png)

9.  在 **MOD Administrator** 页面上，选择 **Omnichannel** 选项卡。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

10. 确保值符合下表

\- Capacity: 100

\- Default Presence: available

![A screenshot of a computer Description automatically
generated](./media/image42.png)

11. 选择 **Save and close**。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

### 任务 2：配置工作流 

1.  在管理中心页面中，从左侧窗格中的**Customer support**下选择
    **Workstreams** ，然后选择 **+ New workstream** 选项。

![A screenshot of a computer Description automatically
generated](./media/image44.png)

2.  填写以下详细信息，向下滚动并单击 **Create**。

- Name - +++**New Workstream**+++

- Owner – **MOD Administrator** （默认选中）

- Type – **Messaging**

- Channel – **Chat**

> ![A screenshot of a chat Description automatically
> generated](./media/image45.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image46.png)

3.  创建工作流后，单击 **set up the chat** 以设置聊天渠道。

![A screenshot of a chat Description automatically
generated](./media/image47.png)

4.  在 **Live chat setup – Channel details**
    屏幕中，填写以下详细信息，然后单击 **Next**。

- Name - +++**Chat Channel**+++

- Language – **English -** **United States**

![A screenshot of a chat channel Description automatically
generated](./media/image48.png)

5.  在 Live chat setup – Chat 小部件屏幕中，提供名称 +++**Store Locator
    Assistant**+++，接受其他默认值，然后单击 **Next**。

![A screenshot of a chat Description automatically
generated](./media/image49.png)

6.  在 **Live chat setup – Behaviors** 屏幕中，接受默认值，然后单击
    **Next**。

![A screenshot of a computer screen Description automatically
generated](./media/image50.png)

7.  在 **Live chat setup – User features** 屏幕中，将 **File
    attachment** 和 **Voice and video calls** 选项切换为
    **off**，然后单击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

8.  在 **Live chat setup – Review and finish**屏幕中，选择 **Create
    channel**。

![A screenshot of a chat setup Description automatically
generated](./media/image52.png)

9.  **Copy Live chat setup – Success**屏幕
    中显示的小组件，并将其**Save**在记事本中，以便在即将到来的练习中将其添加到网页中。然后，单击
    **Done** 完成配置。

![A screenshot of a chat Description automatically
generated](./media/image53.png)

### 任务 3：将 Copilot 添加到工作流

1.  返回 **New Workstream** 页面，向下滚动并单击 Bot 部分中的 **+ Add
    bot。**

![A screenshot of a computer Description automatically
generated](./media/image54.png)

2.  从 添加机器人 屏幕上的copilots列表中，选择 **Store Locator
    Assistant** Copilot，然后单击 **Connect**。

![A screenshot of a computer Description automatically
generated](./media/image55.png)

3.  确保将机器人添加到工作流中，如下面的屏幕截图所示。

![A screenshot of a computer Description automatically
generated](./media/image56.png)

4.  从左侧窗格中，选择 **Bots**。

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  确保 Real Estate Booking Service Copilot已连接。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

## 练习 5：创建网页并测试升级到代理

1.  使用您的租户管理员凭据登录到
    +++https://make.powerpages.microsoft.com/+++。

![A screenshot of a computer Description automatically
generated](./media/image59.png)

2.  确保您处于 **CustomerService Trial** 环境中。

3.  单击 **Get started**。

![A screenshot of a computer Description automatically
generated](./media/image60.png)

4.  单击 **Tell us about you** 页面中的 Skip。

![A screenshot of a computer Description automatically
generated](./media/image61.png)

5.  在下一页向下滚动，然后单击 **Start with a template**
    选项以开始使用模板创建站点。

![A screenshot of a web page Description automatically
generated](./media/image62.png)

6.  选择一个模板，然后单击 **Choose this template**。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

7.  在 为您的网站命名 文本框中，输入名称 +++**Contoso Store
    assistant**+++**，**接受其他默认值，然后单击 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

8.  创建站点后，单击 **Edit site header** in **Company name**标题。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

9.  在 **Edit site header** 窗格中，将 **Site title**设置为 **!!Contoso
    Store assistant!!.**![A screenshot of a computer Description
    automatically generated](./media/image66.png)

10. 单击 页面右上角的 **Edit code**。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

11. 单击 **Open Visual Studio Code**。

![A screenshot of a computer Description automatically
generated](./media/image68.png)

12. 单击 **Allow**。

![A black screen with white text Description automatically
generated](./media/image69.png)

13. 网页的 Home page 将在 Visual Studio Code 中打开。

![A screenshot of a computer program Description automatically
generated](./media/image70.png)

14. 滚动到文件末尾。将
    创建工作流时复制的**script**添加到此文件的最后一行之后。

![A screen shot of a computer screen Description automatically
generated](./media/image71.png)

15. 保存文件，关闭 Visual Studio Code 选项卡并返回到 Power 页面。单击
    **Sync**。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

16. 同步完成后，选择 **Preview** -\> **Desktop。**

![A screenshot of a computer Description automatically
generated](./media/image73.png)

17. 您的网页将在新选项卡中打开。在 网页右下角找到嵌入到页面的 **Store
    Locator Assistan**t。**Click**它。

![A screenshot of a website Description automatically
generated](./media/image74.png)

18. 输入 +++Talk to agent+++。

![A screenshot of a phone Description automatically
generated](./media/image75.png)

19. 在 Customer Service admin 页面中，单击 **Customer Service admin
    center** ，然后从中选择应用 **Customer Service workspace** 。

![A screenshot of a computer Description automatically
generated](./media/image76.png)

![A screenshot of a computer Description automatically
generated](./media/image77.png)

20. 在 Customer Service workspace 页面中，您将收到一个 **chat
    request**。 **Accept** 它。

![A screenshot of a computer Description automatically
generated](./media/image78.png)

21. 接受后，聊天屏幕将打开，其中包含我们在 Escalate
    主题中提供的消息。我们还可以将用户在此处提供的任何其他信息添加到实时代理中。

![A screenshot of a chat Description automatically
generated](./media/image79.png)

22. 如果您想了解实时代理与客户之间的聊天，请模拟其工作原理，然后结束。

![A screenshot of a chat Description automatically
generated](./media/image80.png)

![A screenshot of a chat Description automatically
generated](./media/image81.png)

**总结**

在本实验中，我们学习了

- 从 Copilot Studio 构建代理并配置 Escalate 主题。

- 将代理发布到 Dynamics 365 workspace，并将其集成到网页中。

- 配置和测试升级到实时代理。
