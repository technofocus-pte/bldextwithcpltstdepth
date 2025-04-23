# 实验 05 - 将代理与 Dynamics 365 Customer Service 应用程序集成，并实施自动案例升级到实时代理

## 练习 1：配置 Dynamics 365 Customer Service workspace

### 任务 1：配置全渠道 Power Virtual 代理扩展

1.  打開鏈接
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com>+++，然後單擊全渠道
    Power Virtual Agent 擴展 頁面中的 立即獲取。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image3.png)

2.  在 **Select an environment** 下選擇 **CustomerService
    Trial**，選中複選框並單擊 **Install**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

3.  在 Dynamics 365 應用頁面中，單擊顯示**Update
    available**的條目，**select** **check
    box**以同意條款，然後單擊**Update**。

確保對 **Update available** 作為 Status 的**所有**條目執行此作。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

![A screenshot of a computer Description automatically
generated](./media/image6.png)

### 任务 2：在 Power Platform 管理中心配置搜索设置

1.  使用您的租戶詳細信息登錄
    +++<https://admin.powerplatform.microsoft.com/>+++。選擇
    **Environments -\> CustomerService Trial**。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  選擇 **Resource** （在頂部窗格中） 旁邊的下拉列表，然後選擇
    **Dynamics 365 apps**。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  確保 **Installed Omnichannel for Customer Service**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

4.  導航回管理中心的 **Environments -\> CustomerService
    Trial**頁面。選擇 **Settings** 從頂部窗格中。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  選擇 **Product** -\> **Features**。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  將 **Dataverse Search** 和 **Single table search** 選項切換為
    **ON。**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

向下滾動並單擊 **Save** 右下角的按鈕。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

## 练习 2：创建代理

1.  來自 Copilot Studio 主頁 !!https://copilotstudio.microsoft.com!!
    從右上角選擇 **CustomerService Trial** Environment。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  從左側窗格中選擇 **Agents**。單擊 **+ New Agent** 創建新代理。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

3.  在 Type your message text 區域中，鍵入 **!!You are a customer
    service agent who helps in identifying stores nearby.!!** 然後點擊
    **Send**。

![A screenshot of a chat Description automatically
generated](./media/image16.png)

4.  輸入消息 **!!Maintain a polite tone!!** 下一步，然後點擊**Send。**

![A screenshot of a chat Description automatically
generated](./media/image17.png)

5.  單擊 **Create**。

![A screenshot of a chat Description automatically
generated](./media/image18.png)

6.  創建的代理將打開一條消息， **Your agent is ready**。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

## 练习 3：将 Copilot 连接到 Dynamics 365 Customer Service 并配置“升级”主题

### 任务 1：配置 Escalate 主题

我们在这里重点介绍升级到实时代理的概念。因此，我们将直接朝着这个方向努力，而不会创建任何其他新主题。

1.  選擇 **Topics** 選項卡，然後選擇 **System** 選項卡。選擇
    **Escalate** 主題。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

2.  選擇主題的消息節點，並將現有內容替換為 **!!You will be transferred
    to a live agent shortly!!**

![A screenshot of a computer Description automatically
generated](./media/image21.png)

3.  單擊 + symbol以在 Message 節點旁邊添加一個節點。

4.  選擇 **Topic management** -\> **Transfer conversation**。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  留言 !!The customer wants to talk to a live agent!! 在 Transfer
    conversation 節點中。

![A screenshot of a chat Description automatically
generated](./media/image23.png)

6.  **Save** 主題。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  **Publish** 代理。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

### 任务 2：将copilot连接到 Dynamics 365 Customer Service

1.  發佈後，從 copilot 頁面右上角單擊**Settings**。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

2.  選擇 **Security**，然後在 Security下選擇 **Authentication**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  選擇 **No authentication** 選項，然後單擊 **Save** 。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  在 確認對話框中選擇 **Save** 。

![A screenshot of a computer screen Description automatically
generated](./media/image29.png)

5.  關閉 **Settings** 窗格。

6.  單擊 **Channels** （如果 Channels 不可見，請單擊 +1 以查看
    **Channels** 選項）

![A screenshot of a chat Description automatically
generated](./media/image30.png)

7.  從 Customer engagement 中心窗格中選擇 **Dynamics 365 Customer
    Service。**

![](./media/image31.png)

8.  在 Dynamics 365 Customer Service 頁面上，單擊 **Connect**。

![A screenshot of a message Description automatically
generated](./media/image32.png)

9.  收到 **successfully connected**的消息後，單擊 **Close**。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

## 练习 4：在 Dynamics 365 管理中心中创建工作流和渠道

### 任务 1：在 Omnichannel for Customer Service中管理用户

1.  登錄 !!https://admin.powerplatform.microsoft.com!!
    使用您的管理員租戶憑證，然後從左側選項卡中選擇 **Environments**。
    此處將列出 **CustomerService Trial。Select**它。

![A screenshot of a computer Description automatically
generated](./media/image34.png)

2.  單擊 **Environment URL** 下的 **url value**。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

3.  這將打開 **Apps** 頁面。從中選擇 **Customer Service admin center**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

4.  這將打開 **Dynamics 365 Customer Service admin center** 頁面。

![A screenshot of a customer service Description automatically
generated](./media/image37.png)

5.  在 **Dynamics 365 Customer Service admin center**
    的站點地圖中，選擇** Customer support** 組下的 User management
    **Customer support**。

6.  在 **User management** 頁面上，選擇 **Users** 旁邊的 **Manage**。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

7.  單擊 **Enabled Users** 旁邊的下拉列表，然後選擇 **Omnichannel
    Users**。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

8.  在 **Omnichannel Users** 頁面上， 在列表中選擇用戶 **MOD
    Administrator**。

![A screenshot of a computer Description automatically
generated](./media/image40.png)

9.  在 **MOD Administrator** 頁面上，選擇 **Omnichannel** 選項卡。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

10. 確保值符合下表

\- Capacity: 100

\- Default Presence: available

![A screenshot of a computer Description automatically
generated](./media/image42.png)

11. 選擇 **Save and close**。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

### 任务 2：配置工作流 

1.  在管理中心頁面中，從左側窗格中的**Customer support**下選擇
    **Workstreams** ，然後選擇 **+ New workstream** 選項。

![A screenshot of a computer Description automatically
generated](./media/image44.png)

2.  填寫以下詳細信息，向下滾動並單擊 **Create**。

- Name - +++**New Workstream**+++

- Owner – **MOD Administrator** （默認選中）

- Type – **Messaging**

- Channel – **Chat**

> ![A screenshot of a chat Description automatically
> generated](./media/image45.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image46.png)

3.  創建工作流後，單擊 **set up the chat** 以設置聊天渠道。

![A screenshot of a chat Description automatically
generated](./media/image47.png)

4.  在 **Live chat setup – Channel details**
    屏幕中，填寫以下詳細信息，然後單擊 **Next**。

- Name - +++**Chat Channel**+++

- Language – **English -** **United States**

![A screenshot of a chat channel Description automatically
generated](./media/image48.png)

5.  在 Live chat setup – Chat 小部件屏幕中，提供名稱 +++**Store Locator
    Assistant**+++，接受其他默認值，然後單擊 **Next**。

![A screenshot of a chat Description automatically
generated](./media/image49.png)

6.  在 **Live chat setup – Behaviors** 屏幕中，接受默認值，然後單擊
    **Next**。

![A screenshot of a computer screen Description automatically
generated](./media/image50.png)

7.  在 **Live chat setup – User features** 屏幕中，將 **File
    attachment** 和 **Voice and video calls** 選項切換為
    **off**，然後單擊 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

8.  在 **Live chat setup – Review and finish**屏幕中，選擇 **Create
    channel**。

![A screenshot of a chat setup Description automatically
generated](./media/image52.png)

9.  **Copy Live chat setup – Success**屏幕
    中顯示的小組件，並將其**Save**在記事本中，以便在即將到來的練習中將其添加到網頁中。然後，單擊
    **Done** 完成配置。

![A screenshot of a chat Description automatically
generated](./media/image53.png)

### 任务 3：将 Copilot 添加到工作流

1.  返回 **New Workstream** 頁面，向下滾動並單擊 Bot 部分中的 **+ Add
    bot。**

![A screenshot of a computer Description automatically
generated](./media/image54.png)

2.  從 添加機器人 屏幕上的copilots列表中，選擇 **Store Locator
    Assistant** Copilot，然後單擊 **Connect**。

![A screenshot of a computer Description automatically
generated](./media/image55.png)

3.  確保將機器人添加到工作流中，如下面的屏幕截圖所示。

![A screenshot of a computer Description automatically
generated](./media/image56.png)

4.  從左側窗格中，選擇 **Bots**。

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  確保 Real Estate Booking Service Copilot已連接。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

## 练习 5：创建网页并测试升级到代理

1.  使用您的租戶管理員憑據登錄到
    +++https://make.powerpages.microsoft.com/+++。

![A screenshot of a computer Description automatically
generated](./media/image59.png)

2.  確保您處於 **CustomerService Trial** 環境中。

3.  單擊 **Get started**。

![A screenshot of a computer Description automatically
generated](./media/image60.png)

4.  單擊 **Tell us about you** 頁面中的 Skip。

![A screenshot of a computer Description automatically
generated](./media/image61.png)

5.  在下一頁向下滾動，然後單擊 **Start with a template**
    選項以開始使用模板創建站點。

![A screenshot of a web page Description automatically
generated](./media/image62.png)

6.  選擇一個模板，然後單擊 **Choose this template**。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

7.  在 為您的網站命名 文本框中，輸入名稱 +++**Contoso Store
    assistant**+++**，**接受其他默認值，然後單擊 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

8.  創建站點後，單擊 **Edit site header** in **Company name**標題。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

9.  在 **Edit site header** 窗格中，將 **Site title**設置為 **!!Contoso
    Store assistant!!.**![A screenshot of a computer Description
    automatically generated](./media/image66.png)

10. 單擊 頁面右上角的 **Edit code**。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

11. 單擊 **Open Visual Studio Code**。

![A screenshot of a computer Description automatically
generated](./media/image68.png)

12. 單擊 **Allow**。

![A black screen with white text Description automatically
generated](./media/image69.png)

13. 網頁的 Home page 將在 Visual Studio Code 中打開。

![A screenshot of a computer program Description automatically
generated](./media/image70.png)

14. 滾動到文件末尾。將
    創建工作流時複製的**script**添加到此文件的最後一行之後。

![A screen shot of a computer screen Description automatically
generated](./media/image71.png)

15. 保存文件，關閉 Visual Studio Code 選項卡並返回到 Power 頁面。單擊
    **Sync**。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

16. 同步完成後，選擇 **Preview** -\> **Desktop。**

![A screenshot of a computer Description automatically
generated](./media/image73.png)

17. 您的網頁將在新選項卡中打開。在 網頁右下角找到嵌入到頁面的 **Store
    Locator Assistan**t。**Click**它。

![A screenshot of a website Description automatically
generated](./media/image74.png)

18. 輸入 +++Talk to agent+++。

![A screenshot of a phone Description automatically
generated](./media/image75.png)

19. 在 Customer Service admin 頁面中，單擊 **Customer Service admin
    center** ，然後從中選擇應用 **Customer Service workspace** 。

![A screenshot of a computer Description automatically
generated](./media/image76.png)

![A screenshot of a computer Description automatically
generated](./media/image77.png)

20. 在 Customer Service workspace 頁面中，您將收到一個 **chat
    request**。 **Accept** 它。

![A screenshot of a computer Description automatically
generated](./media/image78.png)

21. 接受後，聊天屏幕將打開，其中包含我們在 Escalate
    主題中提供的消息。我們還可以將用戶在此處提供的任何其他信息添加到實時代理中。

![A screenshot of a chat Description automatically
generated](./media/image79.png)

22. 如果您想瞭解實時代理與客戶之間的聊天，請模擬其工作原理，然後結束。

![A screenshot of a chat Description automatically
generated](./media/image80.png)

![A screenshot of a chat Description automatically
generated](./media/image81.png)

**总结**

在本实验中，我们学习了

- 從 Copilot Studio 構建代理並配置 Escalate 主題。

- 將代理發佈到 Dynamics 365 workspace，並將其集成到網頁中。

- 配置和測試升級到實時代理。
