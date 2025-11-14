# 實驗 04 - 將代理與 Dynamics 365 Customer Service 應用程序集成，並實施自動案例升級到實時代理

## 目的

此實驗室詳細介紹了將對話從代理升級到人工代理的步驟。

**[！重要提示**：僅當已按照**實驗 02 - 配置 Dynamics 365** 客戶服務啟用
Dynamics 365 試用版時，才能執行此實驗

## 練習 1：配置 Dynamics 365 Customer Service 工作區

### 任務 1：配置全渠道 Power Virtual 代理擴展

1.  打開鏈接
    +++https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++ ，然後單擊
    全渠道 Power Virtual 代理擴展 頁面中的 Get it now。

    ![](./media/image1.png)

2.  使用 **Resources** 選項卡中的租戶憑證登錄。

    ![](./media/image2.png)

3.  單擊 **Get it now**。

    ![](./media/image3.png)

4.  在 **Select an environment** 下選擇 **CustomerService
    Trial**，選中複選框並單擊 **Install**。

    ![](./media/image4.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image5.png)

## 任務 2：在 Power Platform 管理中心配置搜索設置

1.  使用您的租戶詳細信息登錄
    +++<https://admin.powerplatform.microsoft.com/+++>。從左側窗格中選擇
    **Manage**，然後從環境列表中選擇 **CustomerService Trial**
    environment。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  選擇 **Settings**從頂部窗格中。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  選擇 **Product** -\> **Features**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  將 **Dataverse Search** 和 **Single table search** 選項切換為
    **ON**，然後選擇**Save**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

## 練習 2：創建代理

1.  在 Copilot Studio 主頁
    +++https://copilotstudio.microsoft.com+++/
    中，從右上角選擇 **CustomerService Trial** 環境。

    ![](./media/image10.png)

2.  從左側窗格中選擇 **Agents**。單擊 **+ New Agent** 創建新代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  在 Type your message text 區域中，鍵入 **+++You are a Customer
    service agent that help identify some stores.+++**
    然後點擊**send**。

    ![](./media/image12.png)

4.  代理可能會為正在創建的代理建議
    **Name**。要麼接受它，要麼建議一個新名字。

5.  輸入消息 **+++Maintain a polite tone+++**接下來，然後點擊 **Send**。

    ![](./media/image13.png)

6.  單擊 **Create**。

    ![](./media/image14.png)

7.  創建的代理將打開一條消息，**Your agent is ready**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## 練習 3：將 Copilot 連接到 Dynamics 365 Customer Service 並配置“升級”主題

### 任務 1：配置 Escalate 主題

我們在這裡重點介紹升級到實時代理的概念。因此，我們將直接朝著這個方向努力，而不會創建任何其他新主題。

1.  選擇 **Topics** 選項卡，然後選擇 **System** 選項卡。選擇
    **Escalate** 主題。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  選擇主題的 message 節點，並將現有內容替換為 +++You will be
    transferred to a live agent shortly+++

    ![](./media/image17.png)

3.  單擊 + 符號以在 Message 節點旁邊添加一個節點。

4.  選擇 **Topic management** -\> **Transfer conversation**。

    ![](./media/image18.png)

5.  發送消息 +++The customer wants to talk to a live agent+++在 Transfer
    conversation 節點中。

    ![ ](./media/image19.png)

6.  **Save** 主題。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  **Publish** 代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### 任務 2：將 Copilot 連接到 Dynamics 365 Customer Service

1.  發佈後，從 copilot 頁面右上角單擊“**Settings**”。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  選擇 **“Security**”，然後在 **“Security”** 下選擇
    “**Authentication**”。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  選擇 **No authentication** 選項，然後單擊 **Save** 。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  在 確認對話框中選擇 **Save** 。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  關閉 **Settings** 窗格。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

6.  單擊 **Channels** （如果 Channels 不可見，請單擊 +1 以查看
    **Channels** 選項）

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  從 Customer engagement 中心窗格中選擇 **Dynamics 365 Customer
    Service**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  在 Dynamics 365 Customer Service 頁面上，單擊 **Connect**。

    ![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  收到 **successfully connected** 的消息後，單擊 **Close**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## 練習 4：在 Dynamics 365 管理中心中創建工作流和渠道

### 任務 1：在 Customer Service 全渠道中管理用戶

1.  使用您的管理員租戶憑據登錄到
    +++https://admin.powerplatform.microsoft.com+++/。從左側窗格中選擇
    **Manage**。在 **Environments**下選擇 **CustomerService Trial**
    environment。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  單擊 **Environment URL** 下的 **url value**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  從標題欄中選擇 **Customer Service workspace**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  這將打開 **Apps** 頁面。從中選擇 **Customer Service admin center**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  這將打開 **Dynamics 365 Customer Service admin center** 頁面。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

### 任務 2：配置工作流

1.  在管理中心頁面中，從左側窗格中的 **Customer
    support** 下選擇**Workstreams** ，然後選擇 **+ New
    workstream** 選項。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

2.  選擇 **Inbound**

    ![](./media/image37.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image38.png)

3.  填寫以下詳細信息，向下滾動並單擊 **Create**。

    - 名字 - +++**New Workstream**+++

    - 所有者 – **MOD Administrator** (默認選中)

    - 類型 – **Messaging**

    - 渠道 – **Chat**

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image39.png)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  創建工作流後，單擊 **Set up chat ** 以設置聊天渠道。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  在 **Live chat setup – Channel details** 屏幕中，填寫以下詳細信息。

    - 名字 - +++**Chat Channel**+++

    &nbsp;

    - 語言 – **英語 - 美國**

    ![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  向下滾動並單擊 **Next**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  接受接下來 2 頁中的默認值，直到您到達 Chat widget 屏幕。在 Live chat
    setup – Chat 小部件屏幕中，提供名稱 **+++Store Locator
    Assistant+++**，接受其他默認值，然後單擊 **Next**。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  在 **Live chat setup – Behaviors** 屏幕中，接受默認值，然後單擊
    **Next**。

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  在 **Live chat setup – User features** 屏幕中，將 **File
    attachment** and **Voice and video calls** 選項切換為
    **off**，然後單擊 **Next**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. 接受 Notification 屏幕中的默認值，然後單擊 **Next** 。

11. 在 **Live chat setup – Review and finish** 屏幕中，選擇 **Create
    channel**。

    ![](./media/image47.png)

12. **複製 Live chat setup – Success** 屏幕中顯示的小組件的值
    ，並將其**Save**
    在記事本中，以將其添加到即將進行的練習中的網頁中。然後，單擊
    **Done** 完成配置。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### 任務 3：將代理添加到工作流

1.  返回 **New Workstream** 頁面，向下滾動並單擊 Bot 部分中的 **+ Add
    bot**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  從 添加機器人 屏幕上的副駕駛列表中，選擇 **Store Locator Assistant**
    代理，然後單擊 **Connect**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  確保將機器人添加到工作流中，如下面的屏幕截圖所示。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  從左側窗格中，選擇 **AI Agents**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  確保 **Store locator** 代理已連接。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## 練習 5：創建網頁並測試升級到代理

1.  使用您的租戶管理員憑據[登錄到
    +++https://make.powerpages.microsoft.com/+++。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  確保您處於 **CustomerService Trial**環境中。

3.  單擊 **Get started**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  單擊  **Tell us about yourself** 頁面中的 **Skip**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  在下一頁向下滾動，然後單擊 **Start with a template**
    選項以開始使用模板創建站點。

    ![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  選擇一個模板，然後單擊 **Choose this template**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  在 為您的網站命名 文本框中，輸入名稱 **+++Contoso Store
    assistant+++**，接受其他默認值，然後單擊 **Done**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  創建站點後，單擊 **Edit**。

    ![](./media/image60.png)

9.  單擊 **Company name** 標題中的 ** Edit site header** 。

    ![](./media/image61.png)

10. 在 **Edit site header** 窗格中，將 站點標題 提供為 **+++Contoso
    Store assistant+++** 並關閉對話框。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. 單擊 頁面右上角的 **Edit code**。

    ![](./media/image63.png)

12. 單擊 **Open Visual Studio Code**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

13. 單擊 **Allow**。 如果需要，請使用您的租戶憑據 **Login**。

    ![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

14. 網頁的 Home page 將在 Visual Studio Code 中打開。

    ![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

15. 滾動到文件末尾。將
    創建工作流時複製的 **script** 添加到此文件的最後一行之後。

    ![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

16. 保存文件，關閉 Visual Studio Code 選項卡並返回到 Power 頁面。單擊
    **Sync**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. 同步完成後，選擇 **Preview** -\> **Desktop。**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

18. 您的網頁將在新選項卡中打開。在 網頁右下角找到嵌入到頁面的 **Store
    Locator Assistant**。**點擊**它。

    ![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

19. 輸入 +++Talk to agent+++。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

20. 在 Customer Service admin 頁面中，單擊 **Customer Service admin
    center**，然後從中選擇應用 **Customer Service workspace**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

21. 在 Customer Service workspace 頁面中，您將收到一個 **chat
    request**。 **接受**它。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

22. 接受後，聊天屏幕將打開，其中包含我們在 Escalate
    主題中提供的消息。我們還可以將用戶在此處提供的任何其他信息添加到實時代理中。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

23. 如果您想瞭解實時代理與客戶之間的聊天，請模擬其工作原理，然後結束。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image77.png)

## 總結

在本實驗中，我們學習了

- 從 Copilot Studio 構建代理並配置 Escalate 主題。

- 將代理發佈到 Dynamics 365 工作區，並將其集成到網頁中。
