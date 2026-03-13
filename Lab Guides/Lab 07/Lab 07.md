# 实验7 - 构建一个带有计算机使用代理（CUA）的自主金融数据检索代理

**介绍**

没有API的遗留系统为自动化设置了重大障碍。传统的RPA通常依赖于脆弱的屏幕抓取或手动变通，这会拖慢决策速度，增加错误，降低生产力。本实验室介绍了Microsoft
Copilot Studio和Computer Using
Agents（CUA）作为更智能的解决方案。通过模拟与内部系统的人工交互，CUA能够安全地访问和处理数据——无需API集成。你将学会构建一个自主代理，能够更快响应，减少人工工作负担，并实现实时、明智的决策。

目标

在这个实验室中，你将学习如何使用 Microsoft Copilot Studio
构建自主代理。该代理将模拟与遗留内部系统的人工交互，无需直接API访问即可获取金融投资组合数据。

## 任务1：创建和配置自治代理

在此任务中，您将在 Microsoft Copilot Studio
中创建一个新的自主代理，配置其身份，并使用 Microsoft 365 Outlook
连接器设置电子邮件触发器。

为了自动化组合查询，座席必须能够检测收到的邮件请求，并基于主题行过滤启动适当的自动化流程。

1.  使用您的登录凭证在 +++https://copilotstudio.microsoft.com+++ 登录
    Copilot Studio。

2.  从右上角选择Dev One环境。

    ![](./media/image1.png)

3.  选择 **Create an agent**。

    ![](./media/image2.png)

4.  代理创建后，选择“**Edit**”选项对 **Details** 信息。

    ![](./media/image3.png)

5.  输入名称为 +++Portfolio Lookup
    Agent+++，选择保存以重命名代理的默认名称。

    ![](./media/image4.png)

6.  向下滚动到触发器部分，点击 **+Add trigger**。

    ![](./media/image5.png)

7.  搜索并选择“**When a new email arrives (V3) (Office 365
    Outlook**”，然后单击“**Next**”。

![](./media/image6.png)

8.  将触发器重命名为 +++When a portfolio lookup email
    arrives+++，确保已建立 Copilot Studio 和 Outlook
    的连接，然后单击“**Next**”。

    ![](./media/image7.png)

9.  在 **Subject Filter (Optional)**
    字段中，在主题行中输入+++Portfolio+++。

    ![](./media/image8.png)

10. 一旦触发器创建，你可以 **Close** 时间来测试触发对话框。

    ![](./media/image9.png)

## 任务 2：添加计算机使用工具 

在这项任务中，你将配置一个计算机使用工具，登录电脑，浏览网站，搜索并检索财务资产组合数据。然后用Office
365的Outlook连接器回复所需数据。

1.  在顶层菜单中进入“**Tools**”。

    ![](./media/image10.png)

2.  选择 **+ Add a tool。**

    ![](./media/image11.png)

3.  选择 **+ New tool**。

    ![](./media/image12.png)

4.  选择 **Computer use (preview)。**

    ![](./media/image13.png)

5.  添加以下说明，然后选择 **Add and configure**。

    ```
    1.  访问<https://computerusedemos.blob.core.windows.net/web/Portfolio/index.html>。

    2.  在“Enter Portfolio ID”搜索字段中输入投资组合
        ID，然后点击“Search”按钮。

    3.  完全按照所示方式检索“Client Name”、“Portfolio
        Value”和“Manager”的值。

    4.  返回这三个值作为最终输出。如果找不到投资组合数据，回复说找不到指定ID的投资组合。
    ```

    ![](./media/image14.png)

6.  将计算机使用工具的 **Name** 更新为+++Look up portfolio data+++

7.  将 **Description** 更新为+++Search and retrieve financial portfolio
    data+++

    ![](./media/image15.png)

8.  在输入部分选择 **+ Add input**。

    ![](./media/image16.png)

9.  输入名称 +++Portfolio ID+++ 和描述 +++The ID of the
    portfolio+++，然后选择 **Done**。

    ![](./media/image17.png)

10. 选择 **Done**。

    ![](./media/image18.png)

## 任务 3：测试计算机使用工具

1.  在“**Instructions**”部分，选择右侧的“**Test**”按钮。

    ![](./media/image19.png)

2.  添加样本值 +++44123BCD+++ 并选择 **Test now**。

    ![](./media/image20.png)

3.  观察计算机使用工具登录并执行请求作:

    - 左侧面板显示你的作说明和工具推理和作的逐步日志。

    - 右侧面板显示了你为电脑设置的机器作预览。

    ![](./media/image21.png)

    ![](./media/image22.png)

    ![](./media/image23.png)

    ![](./media/image24.png)

    ![](./media/image25.png)

    ![](./media/image26.png)

4.  选择 **Finish testing**。

    ![](./media/image27.png)

## 任务4：设置邮件回复能力

在这个任务中，你将设置电子邮件功能。

1.  返回“**Tools**”选项卡，然后选择 **+ Add a tool**。

    ![](./media/image28.png)

2.  搜索 +++**Send an email (V2) (Office 365 Outlook)**+++并选择它。

    ![](./media/image29.png)

3.  选择 **Add and configure**。

    ![](./media/image30.png)

4.  将其**Name**更新为 +++Reply to email+++，**Description** 更新为
    +++Use this operation to reply to the email
    received+++，然后选择“**Additional details**”。

    ![](./media/image31.png)

5.  在“**Additional details**”下，将“**Credentials to
    use**”设置为“**Maker-provided credentials**”。

    ![](./media/image32.png)

6.  在“**Inputs**”部分，单击“**To**”输入旁边的“**customize**”，并将其“**Description**”设置为+++Use
    the "from" email of the triggering received email+++。

    ![](./media/image33.png)

    ![](./media/image34.png)

7.  **自定义** **Subject** 输入框，并将其 **Description** 设置为+++Write
    the email subject+++。

    ![](./media/image35.png)

8.  自定义 **Body** 输入，并将其 **Description** 设置为+++Write the
    email body using HTML and highlight the requested data+++。

    ![](./media/image36.png)

9.  点击 **“Save”** 以最终确定工具配置。

    ![](./media/image37.png)

10. 导航至“**Overview**”选项卡，然后 **Edit** 说明。

    ![](./media/image38.png)

11. 粘贴以下说明。

    ```
    When a financial portfolio related request is received, identify the Portfolio ID and search for the requested data using < Look up portfolio data >. Once you have gathered the financial portfolio information, use the < Reply to email > tool to reply to the original email you received. Do not respond with data beyond what was requested.
    ```

    ![](./media/image39.png)

12. 选择\< Look up portfolio data \>，输入 / 并选择工具
    查找投资组合数据。

    ![](./media/image40.png)

    ![](./media/image41.png)

13. 同样，将“\< Reply to email \>”替换为“**Reply to email**”工具。

14. 替换完成后，如下方截图所示，选择 **Save**。

    ![](./media/image42.png)

15. 从右上角选择 **Settings**。

    ![](./media/image43.png)

16. 在“**Knowledge**”部分下**禁用**“**Use general
    knowledge**”**选项**，然后选择“**Save**”。

    ![](./media/image44.png)

17. 关闭 **Settings** 面板。

    ![](./media/image45.png)

## 任务 5：测试你的完整代理

在这个代理中，你将测试你创建代理的完整工作。

1.  从你偏好的邮箱地址发送测试邮件到你的培训用户邮箱，使用

    主题: +++Portfolio data request+++

    正体:

    ```
    Hi! 
    I hope you're doing well! 
    I'm looking for the portfolio manager and value of portfolio #44123BCD. Much appreciated. 

    Thanks!
    ```


    ![](./media/image46.png)

2.  确保你在培训用户的收件箱里收到邮件。

3.  在“**Overview**”选项卡中，转到“**Triggers**”部分，然后选择“**Test
    trigger**”。

    ![](./media/image47.png)

4.  选择 **trigger instance**，然后 **Start testing**。

    ![](./media/image48.png)

5.  执行完成后，你可以在测试面板中看到更新和流程。

    ![](./media/image49.png)

    ![](./media/image50.png)

6.  执行完成后，请查看您的电子邮件，查看代理人的回复。

    ![](./media/image51.png)

## 摘要

在这个实验室里，你用Microsoft Copilot Studio和Computer-Using
Agents（CUA）构建了一个自主金融数据检索代理。你配置了一个事件驱动代理，自动回复邮件请求，模拟与遗留系统的人工交互以获取投资组合数据，并且无需依赖API即可返回准确结果。

你学会了:

- 设计一个自主智能体，无需直接用户交互即可作

- 使用基于电子邮件的触发器启动自动化工作流程

- 配置计算机使用代理以安全导航和提取遗留网络应用的数据

- 集成行动工具，通过电子邮件返回结果

- 通过使用AI驱动的计算机交互，减少对脆弱RPA模式的依赖

本实验室展示了如何通过CUA的自主代理现代化遗留系统访问，优化运营流程，并在API不可用的环境中实现更快、更可靠的决策。
