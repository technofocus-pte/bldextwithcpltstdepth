# 實驗7 - 構建一個帶有計算機使用代理（CUA）的自主金融數據檢索代理

**介紹**

沒有API的遺留系統為自動化設置了重大障礙。傳統的RPA通常依賴於脆弱的屏幕抓取或手動變通，這會拖慢決策速度，增加錯誤，降低生產力。本實驗室介紹了Microsoft
Copilot Studio和Computer Using
Agents（CUA）作為更智能的解決方案。通過模擬與內部系統的人工交互，CUA能夠安全地訪問和處理數據——無需API集成。你將學會構建一個自主代理，能夠更快響應，減少人工工作負擔，並實現實時、明智的決策。

目標

在這個實驗室中，你將學習如何使用 Microsoft Copilot Studio
構建自主代理。該代理將模擬與遺留內部系統的人工交互，無需直接API訪問即可獲取金融投資組合數據。

## 任務1：創建和配置自治代理

在此任務中，您將在 Microsoft Copilot Studio
中創建一個新的自主代理，配置其身份，並使用 Microsoft 365 Outlook
連接器設置電子郵件觸發器。

為了自動化組合查詢，座席必須能夠檢測收到的郵件請求，並基於主題行過濾啟動適當的自動化流程。

1.  使用您的登錄憑證在 +++https://copilotstudio.microsoft.com+++ 登錄
    Copilot Studio。

2.  從右上角選擇Dev One環境。

![](./media/image1.png)

3.  選擇 **Create an agent**。

![](./media/image2.png)

4.  代理創建後，選擇“**Edit**”選項對 **Details** 信息。

![](./media/image3.png)

5.  輸入名稱為 +++Portfolio Lookup
    Agent+++，選擇保存以重命名代理的默認名稱。

![](./media/image4.png)

6.  向下滾動到觸發器部分，點擊 **+Add trigger**。

![](./media/image5.png)

7.  搜索並選擇“**When a new email arrives (V3) (Office 365
    Outlook**”，然後單擊“**Next**”。

![](./media/image6.png)

8.  將觸發器重命名為 +++When a portfolio lookup email
    arrives+++，確保已建立 Copilot Studio 和 Outlook
    的連接，然後單擊“**Next**”。

![](./media/image7.png)

9.  在 **Subject Filter (Optional)**
    字段中，在主題行中輸入+++Portfolio+++。

![](./media/image8.png)

10. 一旦觸發器創建，你可以 **Close** 時間來測試觸發對話框。

![](./media/image9.png)

## 任務 2：添加計算機使用工具 

在這項任務中，你將配置一個計算機使用工具，登錄電腦，瀏覽網站，搜索並檢索財務資產組合數據。然後用Office
365的Outlook連接器回復所需數據。

1.  在頂層菜單中進入“**Tools**”。

![](./media/image10.png)

2.  選擇 **+ Add a tool。**

![](./media/image11.png)

3.  選擇 **+ New tool**。

![](./media/image12.png)

4.  選擇 **Computer use (preview)。**

![](./media/image13.png)

5.  添加以下說明，然後選擇 **Add and configure**。

&nbsp;

1.  訪問<https://computerusedemos.blob.core.windows.net/web/Portfolio/index.html>。

2.  在“Enter Portfolio ID”搜索字段中輸入投資組合
    ID，然後點擊“Search”按鈕。

3.  完全按照所示方式檢索“Client Name”、“Portfolio
    Value”和“Manager”的值。

4.  返回這三個值作為最終輸出。如果找不到投資組合數據，回復說找不到指定ID的投資組合。

![](./media/image14.png)

6.  將計算機使用工具的 **Name** 更新為+++Look up portfolio data+++

7.  將 **Description** 更新為+++Search and retrieve financial portfolio
    data+++

![](./media/image15.png)

8.  在輸入部分選擇 **+ Add input**。

![](./media/image16.png)

9.  輸入名稱 +++Portfolio ID+++ 和描述 +++The ID of the
    portfolio+++，然後選擇 **Done**。

![](./media/image17.png)

10. 選擇 **Done**。

![](./media/image18.png)

## 任務 3：測試計算機使用工具

1.  在“**Instructions**”部分，選擇右側的“**Test**”按鈕。

![](./media/image19.png)

2.  添加樣本值 +++44123BCD+++ 並選擇 **Test now**。

![](./media/image20.png)

3.  觀察計算機使用工具登錄並執行請求作:

    - 左側面板顯示你的作說明和工具推理和作的逐步日誌。

    - 右側面板顯示了你為電腦設置的機器作預覽。

![](./media/image21.png)

> ![](./media/image22.png)

![](./media/image23.png)

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

4.  選擇 **Finish testing**。

![](./media/image27.png)

## 任務4：設置郵件回復能力

在這個任務中，你將設置電子郵件功能。

1.  返回“**Tools**”選項卡，然後選擇 **+ Add a tool**。

![](./media/image28.png)

2.  搜索 +++**Send an email (V2) (Office 365 Outlook)**+++並選擇它。

![](./media/image29.png)

3.  選擇 **Add and configure**。

![](./media/image30.png)

4.  將其**Name**更新為 +++Reply to email+++，**Description** 更新為
    +++Use this operation to reply to the email
    received+++，然後選擇“**Additional details**”。

![](./media/image31.png)

5.  在“**Additional details**”下，將“**Credentials to
    use**”設置為“**Maker-provided credentials**”。

![](./media/image32.png)

6.  在“**Inputs**”部分，單擊“**To**”輸入旁邊的“**customize**”，並將其“**Description**”設置為+++Use
    the "from" email of the triggering received email+++。

![](./media/image33.png)

![](./media/image34.png)

7.  **自定義** **Subject** 輸入框，並將其 **Description** 設置為+++Write
    the email subject+++。

![](./media/image35.png)

8.  自定義 **Body** 輸入，並將其 **Description** 設置為+++Write the
    email body using HTML and highlight the requested data+++。

![](./media/image36.png)

9.  點擊 **“Save”** 以最終確定工具配置。

![](./media/image37.png)

10. 導航至“**Overview**”選項卡，然後 **Edit** 說明。

![](./media/image38.png)

11. 粘貼以下說明。

When a financial portfolio related request is received, identify the
Portfolio ID and search for the requested data using \< Look up
portfolio data \>. Once you have gathered the financial portfolio
information, use the \< Reply to email \> tool to reply to the original
email you received. Do not respond with data beyond what was requested.

![](./media/image39.png)

12. 選擇\< Look up portfolio data \>，輸入 / 並選擇工具
    查找投資組合數據。

![](./media/image40.png)

![](./media/image41.png)

13. 同樣，將“\< Reply to email \>”替換為“**Reply to email**”工具。

14. 替換完成後，如下方截圖所示，選擇 **Save**。

![](./media/image42.png)

15. 從右上角選擇 **Settings**。

![](./media/image43.png)

16. 在“**Knowledge**”部分下**禁用**“**Use general
    knowledge**”**選項**，然後選擇“**Save**”。

![](./media/image44.png)

17. 關閉 **Settings** 面板。

![](./media/image45.png)

## 任務 5：測試你的完整代理

在這個代理中，你將測試你創建代理的完整工作。

1.  從你偏好的郵箱地址發送測試郵件到你的培訓用戶郵箱，使用

主題: +++Portfolio data request+++

正體:

Hi!

I hope you're doing well!

I'm looking for the portfolio manager and value of portfolio \#44123BCD.
Much appreciated.

Thanks!

![](./media/image46.png)

2.  確保你在培訓用戶的收件箱裡收到郵件。

3.  在“**Overview**”選項卡中，轉到“**Triggers**”部分，然後選擇“**Test
    trigger**”。

![](./media/image47.png)

4.  選擇 **trigger instance**，然後 **Start testing**。

![](./media/image48.png)

5.  執行完成後，你可以在測試面板中看到更新和流程。

![](./media/image49.png)

![](./media/image50.png)

6.  執行完成後，請查看您的電子郵件，查看代理人的回復。

![](./media/image51.png)

## 摘要

在這個實驗室裡，你用Microsoft Copilot Studio和Computer-Using
Agents（CUA）構建了一個自主金融數據檢索代理。你配置了一個事件驅動代理，自動回復郵件請求，模擬與遺留系統的人工交互以獲取投資組合數據，並且無需依賴API即可返回準確結果。

你學會了:

- 設計一個自主智能體，無需直接用戶交互即可作

- 使用基於電子郵件的觸發器啟動自動化工作流程

- 配置計算機使用代理以安全導航和提取遺留網絡應用的數據

- 集成行動工具，通過電子郵件返回結果

- 通過使用AI驅動的計算機交互，減少對脆弱RPA模式的依賴

本實驗室展示了如何通過CUA的自主代理現代化遺留系統訪問，優化運營流程，並在API不可用的環境中實現更快、更可靠的決策。
