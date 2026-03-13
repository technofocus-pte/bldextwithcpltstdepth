# Lab 8 - 在 Copilot Studio 中使用 Dataverse 創建代理 MCP服務器

在 Copilot Studio 中創建並配置 Copilot 代理，並集成 Dataverse MCP
服務器，以簡化業務工作流程。

完成本實驗室後，參與者將能夠在 Copilot Studio 中創建和配置 Copilot
代理，集成 Dataverse MCP
服務器以讀取和更新賬戶與聯繫表中的賬戶信息，構建代理響應以提升清晰度和業務價值，並將這些技能應用於解決常見的業務挑戰。

## 任務1：創建並配置Copilot代理 

構建一個 Copilot 代理，通過 MCP 服務器連接 Dataverse，實現無縫數據訪問。

在本節中，你將學習如何在 Copilot Studio 中創建新的 Copilot
代理，按照正確的說明和建議提示配置它，並集成 Dataverse MCP
服務器實現實時數據連接

1.  如果尚未登錄，請使用您的登錄憑據登錄 Copilot Studio（網址為
    +++https://copilotstudio.microsoft.com+++），並確保您位於 Dev One
    環境中。

![](./media/image1.png)

2.  選擇 **Create an agent** 圖塊以創建新的代理。

![](./media/image2.png)

3.  代理配置完成後，選擇“Edit”選項，選擇“**Details**”面板。

![](./media/image3.png)

4.  輸入以下信息並選擇 **Save**。

- 名稱 - +++Contoso Agent+++

- 描述 - +++This agent will help Contoso sales reps update their
  accounts and contacts using the Dataverse MCP Server+++

> ![](./media/image4.png)

5.  編輯說明，輸入以下說明，然後選擇 **Save。**

該代理將：通過Dataverse
MCP服務器讀取Dataverse中的賬戶和連絡人表中的賬戶和聯繫信息。通過Dataverse
MCP服務器更新Dataverse中的賬戶和聯繫表中的賬戶和聯繫信息。使用 Dataverse
MCP 服務器在 Dataverse
的賬戶表和機會表中創建新賬戶和聯繫方式。不要使用外部知識。只使用Dataverse
MCP工具來創建、讀取、更新和刪除。

![](./media/image5.png)

![](./media/image6.png)

6.  向下滾動，在“Suggested prompts”部分選擇“ **+ Add suggested
    prompts**”。

![](./media/image7.png)

7.  添加以下提示，然後點擊 **Save**。

- **標題**: +++Account Search+++ **Prompt**: +++List all accounts in
  Redmond+++

- **標題**: +++Contact Search+++ **Prompt**: +++List all contacts from
  Coho Winery+++

![](./media/image8.png)

8.  從工具部分選擇 **+ Add tool**。

![](./media/image9.png)

9.  選擇“**Model Context Protocol**”選項卡，搜索“+++Dataverse MCP
    Server+++”，然後選擇“**Microsoft** **Dataverse MCP Server**”。
    注意：選擇非預覽版。請勿選擇“**Microsoft** **Dataverse MCP Server
    (Preview)**”。![](./media/image10.png)

10. 選擇 **Add and configure**。

![](./media/image11.png)

**注意：** Dataverse MCP 服務器將允許你自然語言訪問 Dataverse
中的表格。我們將在賬戶和連絡人表中使用示例數據。可用的工具包括：列表表、描述表、讀取數據、創建記錄、更新記錄、列表提示、執行提示、列出知識源和檢索知識

11. 請查看Dataverse
    MCP服務器可用的工具。你可以選擇和取消代理可用的工具。當工具執行時，列表會從MCP服務器動態更新。因此，你不能從主題調用MCP服務器。

![](./media/image12.png)

12. 在**Test**窗格中輸入+++List the accounts in the state of
    WA+++，然後單擊“**Send**”。

![](./media/image13.png)

13\. 首次運行時，您會看到一個“同意”對話框，因為該工具默認配置為使用“End
user credentials”。 請點擊“**Allow**”繼續。

![](./media/image14.png)

13. 請查看發生的一系列動作以及MCP服務器的輸出，

![](./media/image15.png)

![](./media/image16.png)

14. 如果你點擊所用的工具，你會看到該工具的輸入和輸出。

![](./media/image17.png)

## 任務2：用自定義提示構建代理響應

創建定制提示，確保你的代理給出一致且結構化的回復，提供與業務相關的信息。

1.  如果您在 Copilot
    中嘗試過不同的測試，您可能會注意到帳戶和連絡人的屬性會有所不同。如果您想要更結構化的響應，可以在“**Tools**”中創建**prompt**。在“**Tools**”選項卡中，單擊“
    **+ Add a tool**”，然後單擊“**+ New tool**”。

![](./media/image18.png)

![](./media/image19.png)

2.  選擇Prompt。

![](./media/image20.png)

3.  將頂部的**提示名稱**重命名為 +++Show Account Details+++。
    然後在**instructions**中輸入 +++Find account which
    contains+++，然後點擊 **+ Add
    content**以輸入要查找的賬戶名稱。選擇“**Text**”作為輸入框，並將其命名為“+++**Account
    Name**+++。點擊“**close**”。 ![](./media/image21.png)

![](./media/image22.png)

4.  現在我們可以從 Dataverse
    中提取特定字段，並在聊天中向最終用戶顯示。點擊返回說明，輸入 +++and
    find relevant details like: +++點擊 **+ Add
    content**。這次我們將選擇 **Dataverse** 以及 **Account**
    表中我們認為最終用戶可能希望看到的一些字段。

![](./media/image23.png)

5.  請點擊下拉菜單選擇以下內容：**賬戶名稱、賬號、地址
    1、年收入、電子郵件**和**主要電話。**點擊“**Add**”，然後點擊“**Save**”。

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

6.  選擇 **Add and configure**。

![](./media/image27.png)

7.  現在我們可以測試我們的提示了。我們回去找經紀人再測試一次。進入測試面板。

8.  輸入 +++Show account Details for Fourth
    Coffee+++，然後點擊“**Send**”。您可以看到，回復內容是帶有自定義提示的結構化回復。

![](./media/image28.png)

## 摘要

在本實驗中，您將在 Microsoft Copilot Studio 中構建一個 Copilot
代理，該代理與 **Dataverse MCP
Serve**集成，以使用自然語言安全地訪問和管理業務數據。您將配置該代理，使其能夠讀取、創建和更新
Dataverse
表中的記錄，例如**“客戶”、“連絡人”和“商機”**，而無需依賴外部知識或自定義
API。

你還將學習如何利用定制提示**構建客服響應**，確保輸出一致且業務友好，從而呈現對終端用戶最相關的數據字段。實驗室結束時，你可以設計出一個能夠簡化銷售和客戶管理工作流程、提供清晰結構化洞察，並展示MCP驅動的代理如何利用實時企業數據解決現實世界的業務挑戰。
