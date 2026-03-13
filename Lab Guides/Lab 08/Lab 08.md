# Lab 8 - 在 Copilot Studio 中使用 Dataverse 创建代理 MCP服务器

在 Copilot Studio 中创建并配置 Copilot 代理，并集成 Dataverse MCP
服务器，以简化业务工作流程。

完成本实验室后，参与者将能够在 Copilot Studio 中创建和配置 Copilot
代理，集成 Dataverse MCP
服务器以读取和更新账户与联系表中的账户信息，构建代理响应以提升清晰度和业务价值，并将这些技能应用于解决常见的业务挑战。

## 任务1：创建并配置Copilot代理 

构建一个 Copilot 代理，通过 MCP 服务器连接 Dataverse，实现无缝数据访问。

在本节中，你将学习如何在 Copilot Studio 中创建新的 Copilot
代理，按照正确的说明和建议提示配置它，并集成 Dataverse MCP
服务器实现实时数据连接

1.  如果尚未登录，请使用您的登录凭据登录 Copilot Studio（网址为
    +++https://copilotstudio.microsoft.com+++），并确保您位于 Dev One
    环境中。

    ![](./media/image1.png)

2.  选择 **Create an agent** 图块以创建新的代理。

    ![](./media/image2.png)

3.  代理配置完成后，选择“Edit”选项，选择“**Details**”面板。

    ![](./media/image3.png)

4.  输入以下信息并选择 **Save**。

    - 名称 - +++Contoso Agent+++

    - 描述 - +++This agent will help Contoso sales reps update their
    accounts and contacts using the Dataverse MCP Server+++

    ![](./media/image4.png)

5.  编辑说明，输入以下说明，然后选择 **Save。**

    该代理将：通过Dataverse
    MCP服务器读取Dataverse中的账户和联系人表中的账户和联系信息。通过Dataverse
    MCP服务器更新Dataverse中的账户和联系表中的账户和联系信息。使用 Dataverse
    MCP 服务器在 Dataverse
    的账户表和机会表中创建新账户和联系方式。不要使用外部知识。只使用Dataverse
    MCP工具来创建、读取、更新和删除。

    ![](./media/image5.png)

    ![](./media/image6.png)

6.  向下滚动，在“Suggested prompts”部分选择“ **+ Add suggested
    prompts**”。

    ![](./media/image7.png)

7.  添加以下提示，然后点击 **Save**。

    - **标题**: +++Account Search+++ **Prompt**: +++List all accounts in
    Redmond+++

    - **标题**: +++Contact Search+++ **Prompt**: +++List all contacts from
    Coho Winery+++

    ![](./media/image8.png)

8.  从工具部分选择 **+ Add tool**。

    ![](./media/image9.png)

9.  选择“**Model Context Protocol**”选项卡，搜索“+++Dataverse MCP
    Server+++”，然后选择“**Microsoft** **Dataverse MCP Server**”。
    注意：选择非预览版。请勿选择“**Microsoft** **Dataverse MCP Server
    (Preview)**”。![](./media/image10.png)

10. 选择 **Add and configure**。

    ![](./media/image11.png)

    **注意：** Dataverse MCP 服务器将允许你自然语言访问 Dataverse
    中的表格。我们将在账户和联系人表中使用示例数据。可用的工具包括：列表表、描述表、读取数据、创建记录、更新记录、列表提示、执行提示、列出知识源和检索知识

11. 请查看Dataverse
    MCP服务器可用的工具。你可以选择和取消代理可用的工具。当工具执行时，列表会从MCP服务器动态更新。因此，你不能从主题调用MCP服务器。

    ![](./media/image12.png)

12. 在**Test**窗格中输入+++List the accounts in the state of
    WA+++，然后单击“**Send**”。

    ![](./media/image13.png)

13. 首次运行时，您会看到一个“同意”对话框，因为该工具默认配置为使用“End
user credentials”。 请点击“**Allow**”继续。

    ![](./media/image14.png)

13. 请查看发生的一系列动作以及MCP服务器的输出，

    ![](./media/image15.png)

    ![](./media/image16.png)

14. 如果你点击所用的工具，你会看到该工具的输入和输出。

    ![](./media/image17.png)

## 任务2：用自定义提示构建代理响应

创建定制提示，确保你的代理给出一致且结构化的回复，提供与业务相关的信息。

1.  如果您在 Copilot
    中尝试过不同的测试，您可能会注意到帐户和联系人的属性会有所不同。如果您想要更结构化的响应，可以在“**Tools**”中创建**prompt**。在“**Tools**”选项卡中，单击“
    **+ Add a tool**”，然后单击“**+ New tool**”。

    ![](./media/image18.png)

    ![](./media/image19.png)

2.  选择Prompt。

    ![](./media/image20.png)

3.  将顶部的**提示名称**重命名为 +++Show Account Details+++。
    然后在**instructions**中输入 +++Find account which
    contains+++，然后点击 **+ Add
    content**以输入要查找的账户名称。选择“**Text**”作为输入框，并将其命名为“+++**Account
    Name**+++。点击“**close**”。 
    
    ![](./media/image21.png)

    ![](./media/image22.png)

4.  现在我们可以从 Dataverse
    中提取特定字段，并在聊天中向最终用户显示。点击返回说明，输入 +++and
    find relevant details like: +++点击 **+ Add
    content**。这次我们将选择 **Dataverse** 以及 **Account**
    表中我们认为最终用户可能希望看到的一些字段。

    ![](./media/image23.png)

5.  请点击下拉菜单选择以下内容：**账户名称、账号、地址
    1、年收入、电子邮件**和**主要电话。**点击“**Add**”，然后点击“**Save**”。

    ![](./media/image24.png)

    ![](./media/image25.png)

    ![](./media/image26.png)

6.  选择 **Add and configure**。

    ![](./media/image27.png)

7.  现在我们可以测试我们的提示了。我们回去找经纪人再测试一次。进入测试面板。

8.  输入 +++Show account Details for Fourth
    Coffee+++，然后点击“**Send**”。您可以看到，回复内容是带有自定义提示的结构化回复。

    ![](./media/image28.png)

## 摘要

在本实验中，您将在 Microsoft Copilot Studio 中构建一个 Copilot
代理，该代理与 **Dataverse MCP
Serve**集成，以使用自然语言安全地访问和管理业务数据。您将配置该代理，使其能够读取、创建和更新
Dataverse
表中的记录，例如**“客户”、“联系人”和“商机”**，而无需依赖外部知识或自定义
API。

你还将学习如何利用定制提示**构建客服响应**，确保输出一致且业务友好，从而呈现对终端用户最相关的数据字段。实验室结束时，你可以设计出一个能够简化销售和客户管理工作流程、提供清晰结构化洞察，并展示MCP驱动的代理如何利用实时企业数据解决现实世界的业务挑战。
