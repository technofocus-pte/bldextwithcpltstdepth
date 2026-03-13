# 實驗2 - 構建並增強基於模板的企業助理

**目標**

**經紀人模板**旨在幫助您開始使用**定制經紀**人。您有責任評估使用代理人模板的所有安全和法律影響，並根據您的業務進行定制。

基於**安全旅行代理模板**構建的代理是一種企業對雇員（B2E）代理，旨在為公司員工提供**旅行協助**。該代理幫助員工充分準備並充分瞭解下一次出差。該代理利用自然語言處理提供對話式界面，使員工輕鬆直觀地獲取所需信息。不過，代理目前使用的默認網站只覆蓋美國旅遊目的地。你可以用自己的知識來源替換默認網站。

在這個實驗室裡，你將從**Safe Travels模板**創建一個代理，並在Lab
05中加以增強。

## 練習0 - 在Entra ID中創建安全組並配置Copilot Studio作者

這是幫助我們在整個課程中與Copilot Studio代理無縫協作發佈的前提任務。

1.  訪問Azure門戶的+++<https://portal.azure.com/+++>，在
    **Resources** 標簽頁中使用你的租戶憑證登錄。

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  在“Keep your account secure”窗口中選擇“**Next** ”，然後按照
    **prompts**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  如果你還沒有，可以下載手機上的身份驗證器應用。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  按照提示作，完成設置。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  在 Azure 歡迎界面，選擇**“Get Started**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  搜索並選擇 +++Microsoft EntraID+++。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  在左側面板中，選擇 **Manage** -\> **Groups**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  選擇**New group** 以創建新的安全組。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  請輸入以下詳細信息

    - 組別類型 – 選擇 **Security**

    - 集團名稱 – 輸入 +++**copilotagentsecurity**+++

    - 可以將 Microsoft Entra
      角色分配給該組——選擇**“Yes**”（如果該選項不可見，請忽略此步驟）

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. 選擇“**No owners selected**”，從**Add owners** 頁面選擇 **MOD
    Administrator** ，點擊“**Select**”。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. 同樣地，選擇“**No members selected**”，然後從列表中添加 **MOD
    Administrator** ，並單擊“**Select**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. 選擇：**No roles
    selected**。如果你**沒有**看到這個**選項**，請忽略這個選項，進入下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. 搜索並選擇 **+++Global admin+++** 並選擇 **Select。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. 添加所有細節後選擇 **Create**，確認對話框中選擇**“Yes**”。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. 確保你收到**成功**信息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. 從左上角選擇 Contoso|Groups。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. 從左側窗格的“**Manage**”下選擇“**Properties**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. 將“**can manage access to all Azure subscriptions and management
    groups in this tenant** ”選項切換為“Yes”，然後單擊“**Save**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. 現在，從左側窗格的“**Manage**”下選擇“**Roles and
    administrators**”。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. 搜索 +++privileged role admin+++，然後單擊“**Privileged Role
    Administrator** ”角色（**不要選中複選框**，單擊其名稱）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

21. 選擇 **+ Add assignments**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

22. 選擇**“No members selected**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

23. 選擇 **MOD Admin id** ，然後選擇 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

24. 選擇 **Assign**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

25. 確保角色分配成功。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

26. 從新標簽頁，導航到+++<https://admin.powerplatform.microsoft.com/+++>。
    從左側窗格選擇“**Manage**”，然後選擇 **Tenant Settings** 選項。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

27. 從可用列表中選擇 **Copilot Studio Authors**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

28. 點擊**“Edit**”圖標以編輯設置。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

29. 搜索並選擇 你之前創建的 **+++copilotagentsecurity+++** 組。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

30. 選擇 **Save** 以保存設置。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

## 練習1：從模板創建安全旅行代理

在這個練習中，你將使用 Safe Travels 代理模板在 Copilot Studio
中創建代理。

1.  從瀏覽器登錄
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/)。開始免費試用頁面會打開。選擇您的國家，點擊
    **Start free trial**。

![](./media/image39.png)

2.  選擇 **Dev One** 環境。

> ![](./media/image40.png)
>
> \[!提醒\] **重要** 如果Copilot Studio沒有顯示如下截圖中選擇
> **Environment**  的選項，請按照以下步驟作。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image41.png)
>
> 打開
> +++<https://admin.powerplatform.microsoft.com/+++>。選擇“**Manage** -\> **Environments
> -\> Dev One** ”，然後選擇“**Environment ID**”的值。![A screenshot of a
> computer AI-generated content may be incorrect.](./media/image42.png)
>
> 返回 Copilot Studio 選項卡並打開
> +++<https://copilotstudio.microsoft.com/environments/>**\<
> EnvironmentID \>**+++（將 **\< EnvironmentID \>** 替換為上面獲取的值）

3.  在歡迎界面選擇跳過。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

4.  從左側窗格中選擇“**Agents**”，然後在“**Start with an agent
    template**”下選擇“**Safe Travels** ”模板。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

5.  安全旅行模板創建了一個新的代理，旨在為公司員工提供旅行協助。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

6.  瀏覽設置頁面。在“**Knowledge**”下，您可以看到 **US Travel
    Website** 已添加為知識庫來源。如有需要，可以進行編輯。這裡，我們也使用該網站。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

7.  選擇
    **Create **以創建安全旅行代理。我們不會更改任何內容，也不會繼續使用模板。代理可以隨時根據用戶需求進行升級。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

8.  **代理**程序**創建完成**後，會自動打開並顯示 **Overview** 頁面。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

9.  在測試窗格中，輸入+++How to apply for
    passport?+++，然後點擊“**Send**”。
    測試窗格默認打開。如果未打開，請點擊右上角的測試圖標。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

10. 你可以看到代理會根據其知識來源提供護照申請信息。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image50.png)

## 練習2：將代理發佈到Teams和Microsoft 365 Copilot

在本練習中，您將把在 Copilot Studio 中創建的代理發佈到 **Microsoft
Teams** 和 **Microsoft 365 Copilot** 頻道。

1.  從瀏覽器打開**MS Teams**
    +++<https://teams.microsoft.com/v2/+++>，然後用**Resources** 標簽中的租戶憑證**登錄**。 

2.  回到Copilot Studio，從 代理頁面右上角選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

3.  選中“**Force newest
    version** ”複選框，然後在確認對話框中選擇“**Publish** ”。

![](./media/image52.png)

![](./media/image53.png)

4.  從頂部導航欄選擇“**Channels** ”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

5.  從可用頻道列表中選擇 **Teams**和 **Microsoft 365 Copilot**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

6.  選擇 **Add channel**。

![](./media/image56.png)

7.  點擊“**See agent in Teams** ”選項，將代理添加到Teams中。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

8.  這將在 Microsoft Teams 中打開代理。在“**This site is trying to open
    Microsoft Teams**”彈出窗口中選擇“**Cancel**”，然後選擇“**Use the Web
    App instead** ”選項。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  選擇 **Add** 以添加代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

10. 添加後，你會有機會開設代理。選擇 **Open**。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image61.png)

11. 測試Teams的代理。

![](./media/image62.png)

12. 回到 Copilot Studio，關閉 Teams 和 Microsoft 365 Copilot 頻道窗口。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

## 練習3——測試現有的安全旅行代理

在本練習中，我們將測試 **Safe Travels**
代理，看看它在被問及旅行批准時的反應。

1.  回到Copilot Studio——\>安全旅行代理，選擇 **Test** 圖標來測試代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

2.  在測試窗口輸入+++Need travel approval+++，然後點擊 **Enter**。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image65.png)

3.  你可以看到客服會給出一套通用的指示，要求你按照它來獲得旅行批准。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image66.png)

## 練習4 – 用公司專屬的知識資產增強代理

在本練習中，我們將添加知識資產——Contoso 特有的**Travel Policy** 。

1.  在代理的概覽頁面，向下滾動並選擇 **+ Add knowledge**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

2.  點擊選擇 **select to browse** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

3.  從 **C：\Labfiles\Lab Files** 文件夾中，選擇** Travel
    Policy.docx**並點擊 **Open**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

4.  點擊 **Add to agent** ，添加文件。

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image70.png)

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image71.png)

5.  確保文件已添加。等待狀態從“**In
    progress**”變為“**Ready**”。如果狀態變為“就緒”需要幾分鐘時間，您可以繼續執行下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image73.png)

6.  現在，用同樣的問題測試代理，看看代理是否回復了公司根據知識資產添加的具體政策。

## 摘要

在本實驗中，您使用 Microsoft Copilot Studio 中的 **Safe Travels
代理模板**創建了一個**Business-to-Employee (B2E) 旅行援助代理**。
你探討了代理模板如何通過預配置對話功能和知識源，提供快速起點，同時仍允許未來定制以滿足組織和法律要求。
您利用內置的**美國旅遊網站作**為**知識來源**，測試了代理通過自然語言交互回答員工與旅行相關問題的能力。最後，你們將代理**發佈**到**Microsoft
Teams和Microsoft 365
Copilot**，驗證了其在Teams中的可用性，並確認員工可以在日常協作工具中直接訪問和交互Safe
Travels代理。

 
