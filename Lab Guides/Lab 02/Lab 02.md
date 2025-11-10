# Lab 02 - 配置 Dynamics 365 客户服务

## 目标

在本实验室中，您将在 Azure 中创建一个安全组以更新 Copilot Studio
中的设置，然后激活**Dynamics 365 客户服务试用**版。

## 任务1: 在 Entra ID 中创建安全组并配置 Copilot Studio 作者

1.  Navigate to +++https://portal.azure.com/+++ azure portal and login
    with your login credentials.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  在“确保帐户安全”窗口中**选择** “**Next”，然后按照提示进行作**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  如果您还没有，请在您的手机中下载 Authenticator 应用程序。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  按照提示完成设置。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  在 Azure 欢迎屏幕中，选择“**Get Started.”**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  搜索并选择 +++Microsoft EntraID+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  在左窗格中，选择 **Manage** -\> **Groups**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  选择**“New group**”以创建新的安全组。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  输入以下详细信息

- 组类型 – 选择 **Security**

- 组名 – 输入 +++**copilotagentsecurity**+++

- 可以将 Microsoft Entra 角色分配给组 - 选择 **Yes**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. 选择 **No owners selected**, 从 **Add owners** 页面选择 **MOD
    Administrator** 并单击 **Select**.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. 同样，选择 **No members selected**, ，然后从列表中添加 **MOD
    Administrator**，然后单击 **Select**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. 选择 **No roles selected**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. 搜索并选择 +++**Global admin**+++ ，然后选择 **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. 添加所有详细信息后**，**选择
    **Create，**然后在确认对话框中选择**Yes**。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. 确保您收到 **success**消息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. 从新选项卡中，导航到 +++https://powerplatform.microsoft.com+++.
    从左窗格中**选择**“管理”，然后选择“**租户设置”**选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. 从可用列表中选择 **Copilot Studio Authors**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. 单击 **“编辑”** 图标以编辑设置。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19\. 搜索并选择之前创建的 **copilotagentsecurity** 组。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. 选择 **Save**以 保存设置。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

## 任务 2: 注册 Dynamics 365 Customer Service 试用版

1.  登录到
    +++<https://dynamics.microsoft.com/en-us/customer-service/overview/+++>

2.  如果出现提示，请使用**“ Home **”选项卡中的 **Office 365 Tenant
    details **登录。

3.  点击**Try for free**

![](./media/image28.png)

4.  从“**Resources”**选项卡中输入您的**Office 365 Administrative
    Username**，选中该复选框，然后单击“**Start your free trial**”。

![](./media/image29.png)

5.  输入地区为** United
    States**，输入您的**电话号码**，然后单击**Submit**。

![](./media/image30.png)

6.  如果您看到为 Engage 客户启动试用版的选项，请点击**Launch Trial**。

![](./media/image31.png)

7.  激活后，您的 Customer Service workspace 将被打开。

![](./media/image32.png)

## 总结

在本练习中，我们激活了 Dynamics 365 Customer Service，该 Dynamics 365
Customer Service **将在实验室 04 - 将代理与 Dynamics 365 Customer
Service 应用集成，并向实时代理实施自动案例升级**。
