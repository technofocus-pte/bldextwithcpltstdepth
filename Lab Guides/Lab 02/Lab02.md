# 实验 02 – 构建自治代理来跟踪在 OneDrive 中创建的新文件

**介绍**

组织的 OneDrive For Business
一直在其中创建多个文件，管理员很难跟踪它们。

**目的**

构建一个自治代理，将新添加的文件的详细信息输入到 File Details
（文件详细信息） 跟踪器中。这解决了跟踪文件添加的问题，并且 File details
（文件详细信息） 跟踪器将包含所有新创建文件的详细信息。

## 练习 1：设置环境

1.  使用 Resources 选项卡中的密码登录到 VM。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

### 任务 1：设置 OneDrive

1.  打开浏览器并导航到 +++**https://office.com**+++。 使用 **Resources**
    选项卡中的凭证登录

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  从 左侧菜单中选择 **OneDrive**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

3.  单击 左上角的 + icon，然后选择 **Files upload**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

4.  从 **C：\LabFiles** 中选择文件 **File details** 并选择 **Open**。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  上传文件后，窗口中会弹出一条成功消息。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

6.  单击左侧菜单中的 **My files**，您可以看到新文件在那里可用。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

### 任务 2 ：创建开发环境

1.  使用 Resources 选项卡中的租户详细信息[登录到
    +++](https://admin.powerplatform.microsoft.com/)
    <https://admin.powerplatform.microsoft.com/>+++。

2.  选择 **Environments** 从左侧导航窗格中，然后单击 **+ Newv。**

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  在打开的 New environment （新建环境）
    窗口中，填写以下详细信息，然后单击 **Next**。

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image9.png)

![A screenshot of a computer Description automatically
generated](./media/image10.png)

4.  在 **Add Dataverse** 窗口中，接受默认值，然后单击 **Save** 。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

5.  新创建的环境将在管理中心列出，其状态在 Environments 窗格中。

6.  **Status** 为 **ready**
    后，环境即可使用。我们将在即将到来的练习中使用此环境。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

### 任务 3：启用 Copilot Studio 试用版

1.  在新选项卡中，打开 +++**https://copilotstudio.microsoft.com/**+++。

2.  使用 实验室 VM 的 **Resources** 选项卡下提供的 **Credentials**
    登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  登录后，**Welcome to Microsoft Copilot Studio**
    页面，将国家/地区保留为 **United States** ，然后单击 **Get Started**
    。

![A person sitting at a computer Description automatically
generated](./media/image14.png)

4.  在 **Welcome** 屏幕中选择 **Skip** 。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

## 练习 2：构建和测试自治代理

### 任务 1：从 Copilot Studio 创建代理

1.  单击打开的 Agent creation 页面中的 Skip to configure 选项。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

2.  在代理创建窗格中，输入以下详细信息，然后单击 **Create**。

- **Name** - +++New file tracker agent+++

&nbsp;

- **Description** - +++每次在 OneDrive
  中创建新文件时，此代理都会更新放置在 OneDrive 中的 File details
  tracker

![A screenshot of a computer Description automatically
generated](./media/image17.png)

### 任务 2：向代理添加触发器

1.  创建代理后，向下滚动以找到 **Trigger** 部分。选择 **+ Add
    trigger。**

![A screenshot of a computer Description automatically
generated](./media/image18.png)

2.  在 **Turn on generative orchestration to continue** 对话框中，选择
    **Turn it on**。我们需要将此选项设置为 on 才能添加触发器。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

3.  从 Add trigger 菜单中，选择 **When a file is created** 触发器。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  在 **Add trigger** 屏幕中，选择 Continue 。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  在下一个屏幕中，请注意 **Trigger name** 已填充。等待 与 **Microsoft
    Copilot Studio** 和 **OneDrive for Business**
    建立连接（每个连接器都有一个绿色勾号）。然后，单击 **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  选择以下详细信息。

- **Folder** – Root

- **Include subfolders** – Yes

> 将其他字段保留为默认字段，然后选择 **Create trigger**。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  创建触发器后，将显示 **Time to test your trigger** 消息。 **Close**
    它。我们将稍微调整触发器的基本流程以实现功能，然后对其进行测试。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

### 任务 3：向触发器添加逻辑

1.  在 **New file track agent** 页面中，向下滚动到触发器部分。

2.  单击触发器 **When a file is created**上的 3 个点，然后选择 **Edit in
    Power Automate**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  选择 **+** icon **When the file is created** 和 **Sends a prompt
    action** ，然后选择 **Add an action**。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  搜索 +++add a row+++，然后选择 **Add a row into the table**。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

5.  为每行选择以下值，然后单击 **Save** 。

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image30.png)

![A screenshot of a computer Description automatically
generated](./media/image31.png)

6.  该流现在将类似于以下屏幕截图中的流。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  保存流程并 **publish** 它。

### 任务 4：发布触发器

1.  返回 Copilot Studio，选择 **Settings**。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

2.  选择 **Security** -\> **Authentication** -\> **No authentication**
    ，然后单击 **Save**。

![A screenshot of a computer Description automatically
generated](./media/image34.png)

3.  在 确认对话框中选择 **Save**。

![A screenshot of a computer error Description automatically
generated](./media/image35.png)

4.  现在，选择 **Publish** 以发布代理。

![](./media/image36.png)

5.  在 确认对话框中选择 **Publish**。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

### 任务 5：测试触发器

1.  在浏览器中导航回 **OneDrive** 。点击 **+** 并选择 **Word
    document。**

![A screenshot of a computer Description automatically
generated](./media/image38.png)

2.  为文档 **name** ，然后选择 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

3.  单击 **Close** 关闭隐私选项。

![A screenshot of a computer screen Description automatically
generated](./media/image40.png)

4.  以类似方式添加更多文件。

5.  现在，从 OneDrive 打开 File details.xlsx
    并观察所创建文件的详细信息是否已添加到跟踪器中。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

6.  在 OneDrive 中创建文件时，将调用触发器，该触发器反过来会在 **When a
    file is added** 执行流并更新跟踪器。

7.  您还可以在 Copilot Studio 的 Activity
    选项卡中查看自治代理的详细信息。

**总结**

在本实验中，我们学习了如何从 Copilot Studio 创建、发布和测试自主代理。
