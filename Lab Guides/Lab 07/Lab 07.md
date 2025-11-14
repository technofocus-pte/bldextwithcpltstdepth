# Lab 07 – 創建個性化的購物助手

## 目標

本實驗室的目標是為 Contoso Electronics 創建個性化購物代理。這將使用
Dataverse
表作為代理的知識源。它將根據買家的最新購物情況向他們推薦商品類別，並在整個購物體驗中為他們提供幫助。

## 練習 1 - 創建 Dataverse 表

在本練習中，您將在 Dataverse 中創建表來存儲 **Customer**、 **Product**
和 **Order** 詳細信息。

1.  登錄 +++https://make.powerapps.com+++
    使用您的管理員租戶憑證，然後選擇 Dev One 作為您的環境。從 eft
    導航窗格中選擇 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  選擇 **+ New table 旁邊的下拉列表** ，然後選擇 **其下的 Create new
    tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  選擇 **Import an Excel file or .csv** 以創建新表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  在“導出 Excel”或“導出 .CSV 文件中，選擇 **Select from device**
    選項。

![A screenshot of a file AI-generated content may be
incorrect.](./media/image4.png)

5.  從 **C：\Labfiles** 中，選擇 excel – **Customers.xlsx**。選擇
    **Import** 以從跟蹤器導入數據並創建表格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  該表是使用跟蹤器中的數據創建的。

7.  此處，該表名稱為 **Customer
    Record**。在您的案例中，名稱可能略有不同，因為它是自動生成的。記下它，並在整個實驗室執行過程中使用適當的
    Table name。

8.  單擊表，然後選擇 **View data** 以查看添加到表中的數據。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  選擇**Save and exit**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

10. 單擊 確認對話框中的 **Save and exit。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. 重複 2 到 10 的步驟兩次，一次使用跟蹤鏈接 **Product Catalog.xlsx**
    創建表格，下次使用 **Orders.xls**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

1.  現在，我們將有 3 張表，

    - Customer Record

    - Product Record

    - Orders

## 聯繫2 – 創建 Shopping 代理

在本練習中，您將創建一個 Shopping 代理，該代理將協助客戶在 Contoso
Electronics 中購物。

### 任務 1 – 創建代理

使用 Copilot 在 Copilot Studio 中創建代理。與 Copilot
聊天，並就代理的設計和行為提供說明，以便 Copilot 為您創建代理。

1.  登錄 Copilot Studio： +++https://copilotstudio.microsoft.com/+++
    並選擇 **Dev One** 環境。

![](./media/image12.png)

2.  選擇 **代理** ，然後單擊 **+ 新建代理**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  在聊天中輸入以下內容並發送。

+++Create an agent that will assist the customers in shopping with
Contoso Electronics. Name it as "Shopping agent".+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  輸入 +++Help the users in finding products and their prices, give
    personalized suggestions and track order delivery.+++ 並按 **Enter
    鍵**.

![](./media/image15.png)

5.  輸入以下附加說明。

+++Maintain a polite tone+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  點擊 **Create** 以創建 **Shopping agent**.

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image17.png)

7.  代理已設置完畢。這可能需要幾分鐘時間。代理準備就緒後，它將顯示在
    Copilot Studio 中，如下面的屏幕截圖所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

### 任務 2 – 添加知識

向代理添加知識使其以這些知識資源為基礎，使其能夠更有效地回答用戶查詢。在此任務中，您將把在前面的練習中創建的
Dataverse 表作為知識源添加到此代理。

1.  輸入 +++What is the status of the order o1001?+++ 在 Test （測試）
    窗格中.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image19.png)

2.  響應將類似於下面的響應，因為代理沒有任何相關信息。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image20.png)

3.  現在，我們將向代理添加 knowledge source. 在 代理的主頁上，選擇
    **Knowledge** 部分**下的** Add Knowledge.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

4.  從 **可用選項列表中選擇** Dataverse。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

5.  搜索+++order+++, 選擇 **Order Record** 表，然後單擊 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  選擇 **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  添加數據源後，請等待幾分鐘，然後再次測試代理。

8.  一旦 **Order Record** 在 Knowledge 部分**下變為** Ready, 在 Test
    （測試） 窗格中提出相同的問題。

現在，您可以看到代理從數據庫中檢索信息並將其提供給用戶。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

### 任務 3 – 創建實體

1.  從代理的 Home 屏幕**中選擇** Settings 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

2.  從 **左側窗格中選擇** Entities。選擇 **Add an entity -\> + New
    entity**

![](./media/image27.png)

3.  選擇 **Closed list**.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image28.png)

4.  輸入以下詳細信息。

名稱 - +++Laptop+++

描述 - +++Contains products under Laptop category+++

在 List items （列表項**） 下**，輸入 +++Apple MacBook Air M3+++
，然後單擊 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

5.  同樣，添加以下項目，然後選擇 **Save （保存**）。

+++Dell XPS 13 Plus+++

+++HP Spectre x360 14+++

+++Lenovo ThinkPad X1 Carbon Gen 12+++

+++Asus ROG Zephyrus G14+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

6.  現在，對以下數據重複步驟 2 到 5。

Name - +++Desktop+++

Description - +++Contains products under Desktop category+++

Under **List items**, enter +++Apple iMac+++ and click on **Add**.

7.  要添加到列表中的其他項目，

+++Microsoft Surface Studio 2+++

+++HP Envy Desktop+++

+++Dell Inspiron Desktop+++

+++Lenovo IdeaCentre AIO 5i+++

8.  同樣，對以下數據重複步驟 2 到 5。

Name - +++Tablet+++

Description - +++Contains products under Tablet category+++

Under **List items**, enter +++Apple iPad Pro+++ and click on **Add**.

9.  要添加到列表中的其他項目，

+++Samsung Galaxy Tab S9 Ultra+++

+++Microsoft Surface Pro 10+++

+++Lenovo Tab P12 Pro+++

+++Apple iPad Air+++

## 聯繫 3 – 創建 Topic 和代理流程並設計代理

設計主題是創建代理中非常重要的部分，因為它處理如何回答用戶問題背後的邏輯以及細節的流程將如何。

### 任務 1 – 編輯對話開始主題

Conversation Start
主題是測試代理時要調用的第一個主題。默認情況下，它是您在 Copilot Studio
中創建的任何代理中可用的系統主題。現在，您將編輯此主題以繼續來自代理的問候消息的對話。

1.  在 代理的 Overview 頁面中，從 頂部菜單欄中選擇 Topics 選項卡。選擇
    **System** 以查看 System 主題列表。從列表中選擇 Conversation Start
    主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  在現有 Message 節點後，添加 **Question 節點**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  輸入以下消息，

+++Welcome to Contoso Electronics. Please enter your **Phone number** to
proceed.+++ ，然後在 **Identity** 下選擇 **User's entire response**
。單擊 **Save user response as** field **下的** Var1。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

4.  重命名 **Var 1** 到 +++MobileNumber+++ 並選擇 **Global （全域** ）
    以跨主題使用它，然後選擇 **Save （保存**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

### 任務 2 – 創建主題以處理 Customer details

1.  在代理的 Overview （概述） 頁面中，從頂部菜單欄中選擇 Topics
    （主題） 選項卡。選擇旁邊的下拉列表 **Add a topic -\> From blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  將代理命名為 +++Customer Details+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  選擇 **Change trigger** 並選擇 **It’s redirected to** 作為觸發器。

![Screens screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

4.  選擇 **Save** 以保存主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

### 任務 3 – 創建 Agent 流以獲取客戶的詳細信息

在此任務中，您將創建一個代理流程，將客戶輸入的電話號碼作為輸入傳遞給該流程，並設計流程以檢查用戶是否存在，並檢索信息並將詳細信息返回給代理。

1.  在 Trigger 節點下，添加一個節點，選擇 **Add a tool** -\> **New Agent
    flow**.

![](./media/image39.png)

2.  代理流程設計器隨即打開。選擇 **Save draft** 以保存流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  選擇 **Overview** 從頂部菜單中，單擊 **Edit （編輯** ）
    並輸入流的名稱 +++GetCustomer+++. 然後選擇 **Save**. ![A screenshot
    of a computer AI-generated content may be
    incorrect.](./media/image41.png)

4.  再次導航到 **Designer （設計器**） 選項卡以設計流程。選擇節點
    **當代理調用流時**，然後選擇 **+ Add an input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  選擇 **Text**.

![](./media/image43.png)

6.  將輸入為 +++Phone number+++，然後折疊 **Parameters** 選項卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  單擊 **Add an action** between the 2 nodes in the flow.搜索 +++List
    rows+++ ，然後選擇 **Microsoft Dataverse** 下的 列出行**作**。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

8.  將連接名稱輸入為 +++Dataverse+++，然後單擊 **登錄**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  使用您的管理員租戶憑據**登錄**，並在 **出現提示時單擊** Allow access
    。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. 導航到 PowerApps，網址為 +++https://make.powerapps.com/+++ 並打開
    **Customer Record** 表。單擊 **Mobile number**
    字段旁邊的下拉列表，然後選擇 **Edit column**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. 向下滾動和下方 **Advanced options**, 有一個名為 **Logical name**
    的字段。在記事本中記下它的值。

**重要:** 每個字段在 Dataverse 中都有一個關聯的邏輯名稱。在 Agent
流中使用它時，您只需為所有字段指定邏輯名稱。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. 在這種情況下，對於 Phone number （電話號碼），它是
    **cr6dd_mobilecontact**。記下它

13. 導航回 Copilot Studio – 代理流程選項卡。打開 Getcustomer
    流程，然後選擇列出 **行** 作。

14. 在 Filter rows （篩選行） 下，輸入 **\<Logical name of Mobile
    number\> eq ' '**.將 **\<Logical name\>**
    替換為您在前面的步驟中檢索到的值。將光標保留在引號內，並添加 Phone
    number – dynamic 變量。

在這種情況下，它將cr6dd_mobilecontact **eq 'Phone number'**

![](./media/image50.png)

![](./media/image51.png)

15. 在 List rows 節點下，添加 **Condition** 節點。

![](./media/image52.png)

16. 輸入 **/** 並選擇 **Insert expression**。

![](./media/image53.png)

17. 輸入+++length(outputs('List_rows')?\['body'\]?\['value'\])+++
    ，然後選擇 **Add**.這將檢查 List rows 是否返回值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

18. 點擊 **Add an action** 在 添加的條件的 True 分支下，然後添加新的
    **Condition** 節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

19. 輸入 +++not(empty(first(outputs('List_rows')?\['body/value'\])?\[
    cr6dd_lastpurchasedproduct '\]))+++ 在 Condition 的 function area
    中。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

> **重要** – 確保將 **cr6dd_lastpurchasedproduct** 替換為 **Customer
> Record** 表中**的 Recent Products Purchased** 字段 **的**邏輯名稱
>
> ![](./media/image58.png)

20. 將條件設置為 **等於 true**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

21. 在 Condition1 的 **True** 路徑**下添加新作** ，然後選擇 **Respond to
    the agent** 節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

22. 選擇添加的 **Respond to the agent （響應代理） 節點** 並將其重命名為
    +++If the customer has made a previous purchase+++ 並選擇 **+ Add an
    output**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

23. 選擇 **Text**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

24. 進入 +++Customer ID+++ 作為名稱，然後單擊 **Insert expression**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

25. 輸入
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
    +++ **cr6dd_customeridentifier** 是 Customer Record 表的 Customer ID
    的邏輯名稱。 **將其替換為**您的值。

26. 選擇 **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

27. 同樣，將以下輸出變量和表達式添加到每個變量中。對於每個變量，請確保將邏輯名稱替換為您的變量。

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_lastpurchasedproduct'\]+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

28. **Respond to the agent （響應代理）** 節點將具有 3
    個輸出變量，如下面的屏幕截圖所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

29. 在 Condition1 **節點的** False **路徑**下添加 Respond to agent
    節點。將其重命名為 +++If the customer has not made a previous
    purchase+++. 點擊 **+ Add an output**.

![](./media/image68.png)

30. 輸入以下輸出變量，將列邏輯名稱替換為相應列的邏輯名稱。

- +++Customer ID+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
  +++

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ - +++’1’+++

31. False **路徑下的 Respond to the agent** 節點
    將類似於下面屏幕截圖中的節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

32. 現在，在 Condition 節點的 **False 路徑下添加一個** Respond to the
    agent **節點** ，將其重命名為 +++If the customer does not exist+++
    and add outputs to it as below.

- +++Customer ID+++ - +++’1’+++

- +++Customer Name+++ - +++’1’+++

- +++Product Category+++ - +++’1’+++

![](./media/image70.png)

33. **GetCustomer** 流將類似於下面屏幕截圖中的流。

![](./media/image71.png)

34. 右鍵單擊 **流末尾作為常見**代理的 Respond to the agent
    （響應代理），然後選擇 **Delete （刪除**） 將其刪除。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

35. 選擇 **Save Draft** 以保存實驗室。保存後，單擊 **Publish （發佈** ）
    以發佈流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

### 任務 4 – 創建代理流程以添加客戶

在此任務中，您將創建一個代理流，以便在客戶是新客戶時將新客戶添加到
Dataverse 中。

1.  從 **Agent flows** 選項卡中，選擇 **+ New agent flow。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  選擇 **Add a trigger node** 並將其替換為 **When an agent calls the
    flow** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

3.  選擇 **+ Add an input** 並添加 **Text** input。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

4.  輸入 +++Name+++ 作為輸入名稱。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

5.  同樣，添加以下輸入值。

+++Phone Number+++

+++Email ID+++

+++Address+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image79.png)

6.  在節點下方添加作，然後選擇 **Add a new row**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

7.  選擇 Table Name（表名稱）作為 **Customer
    Record（客戶記錄**），然後在 **Advanced
    parameters（高級參數）中選擇** Show all（全部顯示）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

8.  單擊 **Address** 字段，選擇 **Dynamic 值** ，然後選擇 **Address**
    動態值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image83.png)

9.  同樣，添加

- 客戶名稱 – Name

- Email ID – Email ID

- 手機號碼 - Phone Number

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

10. 打開 Customer ID **的 insert 表達式**，輸入 +++guid()+++ ，然後選擇
    **Add**。這是為了添加唯一值作為客戶的 ID。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

11. 添加新作，然後選擇 **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

12. 添加名為 +++Customer ID+++ 並插入表達式並輸入
    +++string(outputs('Add_a_new_row')?\['body/cr6dd_customeridentifier'\])+++
    as the value.

將 **cr6dd_customeridentifier 替換為列 Customer ID 的邏輯名稱**。

選擇 **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

13. 選擇 **Save draft** 以保存流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

14. 保存流程後，選擇 **Publish （發佈** ） 以發佈流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

15. 選擇 **Overview** tab. **點擊 Edit.** 將流的名稱輸入為 +++Add
    Customer+++ ，然後選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

### 任務 5 – 添加流程並設計 Customer Details 主題

在此任務中，您將設計客戶詳細信息主題，該主題將獲取客戶的電話號碼，檢查
Dataverse 中是否已存在詳細信息，如果尚不存在，則添加詳細信息。

1.  導航回 **Customer Details** 主題。

2.  在 Trigger 節點下添加節點，選擇 **Add a tool -\> GetCustomer**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

3.  在 Inputs （輸入） 中，選擇變量 **MobileNumber**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

4.  選擇 **輸出** 變量，並將 Customer ID 和 ProductCategory 標記為
    **Global** ，如下面的屏幕截圖所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

5.  在 **Action （作** ） 節點下，添加一個 **condition** （條件） 節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

6.  選擇 **CustomerID** in **Select a variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

7.  選擇條件 as **不等於** 並輸入 +++ '1'+++ 在 **Value**
    字段中。這將檢查數據庫中是否已存在客戶詳細信息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

8.  在 condition 節點下，添加 **Set a variable** 節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

9.  單擊 **Select a variable** ，然後選擇 **Create a new variable**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

10. 將變量命名為 +++IsNewCustomer+++ 並將其標記為 **Global**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

11. 將值設置為 +++‘No’+++. 這意味著客戶是其數據已存在於 Dataverse
    中的老客戶。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

12. 您將在變量節點旁邊添加一個新節點，並向客戶提供 Welcome 消息。

13. 選擇 Add a node ，然後選擇 **Send a message** node
    。在消息區域中，鍵入 +++Welcome+++ 然後單擊 {x} 圖標以選擇變量。選擇
    **Customer Name** 變量。

![](./media/image101.png)

現在，我們已經調用了代理流程
**GetCustomer**，檢查客戶記錄是否已經存在，如果是，則向客戶添加了歡迎消息。

現在，如果客戶記錄尚不存在，我們將設計主題的部分。

14. 在 **All other conditions** 節點下，添加 Set a variable 節點，並將
    **isNewCustomer** 變量的值設置為 +++’Yes’+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

15. 在變量節點旁邊，添加 **Message** 節點並輸入 +++We do not have your
    details in our system. Please fill in your details below to help us
    serve you better.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

16. 在 Message 節點旁邊，添加 **Ask with adaptive card** 節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

17. 單擊屏幕右上角的 3 個點，然後選擇 **Properties（屬性**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

18. 選擇 **“編輯自適應卡**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

19. 在 **Card payload editor** 區域中輸入以下 **JSON**。選擇 **Save
    （保存**）。

> {
>
> "type": "AdaptiveCard",
>
> "body": \[
>
> {
>
> "type": "TextBlock",
>
> "size": "Medium",
>
> "weight": "Bolder",
>
> "text": "Please enter your details"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Name",
>
> "label": "Name"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Mobile Number",
>
> "label": "Mobile Number"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Email ID",
>
> "label": "Email ID"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Address",
>
> "label": "Address"
>
> }
>
> \],
>
> "actions": \[
>
> {
>
> "type": "Action.Submit",
>
> "title": "Submit"
>
> }
>
> \],
>
> "version": "1.5",
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json"
>
> }
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image107.png)

20. 選擇 **Close** 關閉編輯器。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

21. 展開創建的自適應卡片節點的 Outputs 部分，選擇 Mobile Number
    值，然後選擇 Global.MobileNumber 變量以保存用戶輸入的電話號碼值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

22. 將其他值保留為默認值。

23. 自適應卡已準備好表單以獲取客戶詳細信息。

24. 在 自適應卡 節點旁邊，調用流 **添加客戶.**

![](./media/image110.png)

25. 單擊 Enter **中的**三個點**，或選擇一個值**，然後選擇
    **CustomerName** 變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

26. 同樣，為要傳遞給流的其他字段添加輸入變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

27. 選擇 **Global.CustomerID** 作為輸出變量，流的輸出將保存到該變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

28. 在 action 節點後，添加 **Message 節點** 並輸入值, +++Thank You!
    Customer detail has been added to the database. Please select a
    product type to shop.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

29. **保存** 主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

30. 打開 Conversation Start 主題，然後從那裡調用 Customer Details 主題。

31. 在主題中的 Question 節點後添加一個節點。選擇 **Topic management -\>
    Go to another topic（主題管理轉到其他主題**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

32. 選擇 **Customer Details** 主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

33. 選擇 **Save （保存**） 以保存主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### 任務 6 – 創建代理流程以獲取產品詳細信息

在此任務中，您將創建一個代理流，該流將根據所選產品從 Dataverse
獲取產品詳細信息。

1.  從 Copilot Studio **中選擇** 流 選項卡，然後選擇 **+ 新建代理流**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  選擇觸發器節點，然後選擇 **When an agent calls the flow** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  添加 Text input 並將其命名為 +++Product Name+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

4.  選擇 **Save draft （保存草稿** ） 以保存流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

5.  選擇 **Overview** 選項卡，然後單擊 **Edit**。將名稱輸入為
    +++GetProductDetails+++ ，然後選擇 **Save （保存**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

6.  導航回 **Designer** 選項卡，然後選擇 **When an agent calls the
    flow** 節點下的 **Add an action**。搜索 +++list rows+++ ，然後選擇
    **Microsoft Dataverse** 下的 列出行**作**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

7.  輸入以下值

- **表名稱 –** 選擇 **產品記錄**

篩選行 – +++cr6dd_producttitle eq '**\<Product Name\>**'+++ 將 \<Product
Name\> 替換為動態值 ProductName。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image125.png)

1.  在 List rows **節點下添加** Respond to the agent **節點** 。選擇 **+
    Add an output** 並添加 Text Output 變量。輸入以下值，然後單擊 Add in
    **insert expression。**

- 輸入名稱 – Enter +++Product Name+++

> 表達 -
> +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_producttitle'\]+++
> (將 **cr6dd_producttitle** 替換為表中 tha 列 Product Name 的邏輯名稱。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image126.png)

2.  同樣，添加另一個具有以下詳細信息的輸出節點

- 輸入名稱 – Enter +++Price+++

- 表達 -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_productprice'\]+++
  Replace **cr6dd_productprice** with the logical name of the column
  **Price** in your table

> 節點現在應如下所示。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image127.png)

1.  選擇 **Save draft （保存草稿**） 以保存主題，然後選擇 **Publish
    （發佈**） 以發佈流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

### 任務 7 – 創建主題以從客戶處檢索 Product category

1.  從 Copilot Studio 主題選項卡中，選擇 **+ Add a topic -\> From
    blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

2.  將主題重命名為 +++Place Order+++. 將觸發器節點的觸發器更改為 **It's
    redirected to**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

3.  **保存** 主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image131.png)

4.  從 Copilot Studio 主題選項卡中，選擇 **+ Add a topic -\> From
    blank**.

![](./media/image129.png)

5.  將主題重命名為 +++Get Product Categories+++. 在 **Trigger
    節點中選擇** Change trigger **選項** ，然後選擇 **It's redirect to**
    選項。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

6.  在 **Trigger** 節點下，添加 **Condition** 節點。

選擇全局變量 **IsNewCustomer** 並添加條件 **IsNewCustomer** **is equal
to** +++**'Yes'**+++.

選擇 **+ New condition.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

7.  選擇 **Or**.

在 Or 條件下，選擇全局變量 **ProductCategory** 添加條件，等於 +++'1'+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

![](./media/image136.png)

8.  在 Condition 節點下，添加一個 question 節點並輸入 +++Select a
    category+++ 並選擇 **+ 新建選項**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

9.  輸入選項 +++Laptop+++ ，然後再次選擇 + 新建選項。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

10. 同樣，添加兩個其他選項 +++**Desktop**+++ and +++**Tablet**+++. 在
    Save user response as （將用戶響應另存為**）
    下選擇變量**，並將變量命名為 +++**ProdCatchoice**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

11. 在 question 節點下，添加 **Set a variable value** 節點，以將從
    question 節點收到的選擇轉換為 String （字符串）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

12. 在 Set variable （設置變量） 下選擇全局變量 **ProductCategory**。在
    **To value** 字段中，單擊 3 個點，選擇 **Formula**
    選項卡。輸入表達式 +++Text(Topic.ProdCatchoice)+++ and select
    **Insert**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

13. 在 Set variable value 節點下，添加新節點 **Topic management** -\>
    **Go to another topic** -\> **Place Order**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

14. 現在，一條路徑已完全完成。它將從用戶那裡獲取類別並調用 Place Order
    主題。

15. 導航回本主題的開頭。在所有其他條件下，添加 **Question （問題** ）
    節點。添加消息 +++Based on your recent purchase we suggest you
    products in \<Product Category\> category. Would you like to
    continue?+++

在消息中，將 **\<Product Category\>** 替換為 **Global.ProductCategory**
變量。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image143.png)

16. 添加 2 個選項, +++Yes+++ and +++No+++. 單擊將用戶響應另存為 （Save
    user response as） 下的變量，並將其重命名為
    +++Userschoiceofcategory+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

17. 在 **question** 節點下，添加 **condition** 節點。

將第一個條件設置為 **Userschoiceofcategory is equal to Yes**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

18. 在此節點下，添加 **Topic management 節點** 並調用 **Place Order**
    主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

19. 在 condition 節點中，選擇 condition 節點右上角的三個點，然後選擇
    **Insert new condition** 。

![](./media/image147.png)

20. 添加條件, **Userschoiceofcategory is equal to No**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

21. 在 Condition 節點下，添加一個 question 節點並輸入 +++Select a
    category+++ 並選擇 **+ 新建選項**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

22. 輸入選項 +++Laptop+++ and select + 又是新選項。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

23. 同樣，添加兩個其他選項 +++**Desktop**+++ and +++**Tablet**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

24. 在 question 節點下，添加 **Set a variable value** 節點，以將從
    question 節點收到的選擇轉換為 String （字符串）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

25. 在 Set variable （設置變量） 下選擇全局變量 **ProductCategory**。在
    **To value** 字段中，單擊 3 個點，選擇 **Formula**
    選項卡。輸入表達式 +++Text(Topic.Var1)+++ ，然後選擇 **Insert**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

26. 在 Set variable value 節點下，添加新節點 **Topic management** -\>
    **Go to another topic** -\> **Place Order**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

27. 選擇 **Save** 以保存主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image151.png)

28. 打開 Customer **Details** 主題並移至最後一個節點。

29. **添加新節點** 以調用主題 **Get Product Categories**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image152.png)

30. 選擇 **Save** 以保存主題。

![](./media/image153.png)

### 任務 8 – Create Agent flow 來下訂單

在此任務中，您將創建一個代理流程，以根據客戶選擇的產品下訂單。

1.  從 **Agent flows** 選項卡中，選擇 **+ New agent flow。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image154.png)

2.  單擊 **Add a trigger 節點** ，然後選擇 **When an agent calls the
    flow** 節點時。

![](./media/image155.png)

3.  添加 2 個 **Text** 變量 +++Product Name+++ and +++Customer ID+++
    作為 **Input**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image156.png)

4.  單擊 **Save Draft** 以保存流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image157.png)

5.  從 **頂部菜單中選擇** Overview ，單擊 **Edit** 並輸入流的名稱
    +++PlaceOrder+++. 然後選擇 **Save （保存**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image158.png)

6.  導航回 **設計器** 選項卡。選擇 添加新作 ，然後在 **Dataverse
    下**選擇 添加新行。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image159.png)

7.  選擇 Table name 作為 **Order Record**，然後單擊 **Advanced
    parameters 下的** Show all。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image160.png)

8.  輸入以下值。

客戶標識符 - **客戶 ID** （動態值）

Order identifier – 在 Insert expression 中輸入 guid（）

訂單狀態 - +++**Order Placed**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image161.png)

9.  添加節點, **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image162.png)

10. 添加輸出 Text 變量並將其命名為 +++Order ID+++.

將其值輸入為 +++
string(outputs('Add_a_new_row')?\['body/cr6dd_orderidentifier'\])+++
（將 **cr6dd_orderidentifier** 替換為 Order Record 表中列 Order ID
的邏輯名稱值。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image163.png)

11. 單擊 **Save Draft** 以保存流程，然後單擊 **Publish** 以發佈流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image164.png)

### 任務 9 – 設計 Place Order 主題 

在此任務中，您將設計主題來下訂單並更新 Dataverse 表。

1.  從 Agent 的 **Topic** 選項卡中**打開主題** Place Order 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image165.png)

2.  添加包含消息 +++Options based on the category will be listed
    below.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image166.png)

3.  添加 condition 節點。輸入條件 ProductCategory（全局變量） 等於
    +++Laptop+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image167.png)

4.  在節點下，添加 question 節點並輸入消息 +++Select a Laptop
    product+++. 在 **Identity** 下選擇 **Laptop** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image168.png)

5.  單擊 **Select** options for user 並選擇所有 5 個可用選項。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image169.png)

6.  將變量名稱輸入為 +++ProdNameLapChoice+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image170.png)

7.  現在，按照相同的過程並為 ProductCategory 等於 +++Desktop+++ and
    +++Tablet+++.

8.  將值保存在變量名稱中。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image171.png)

9.  在 Select a Laptop product **問題節點**下選擇 **Set variable value**
    節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image172.png)

10. 將創建的變量重命名為 +++ProdNameSelected+++ 並將其設置為
    **Global**.![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image173.png)

11. 將 Formula （公式） 字段中的值設置為
    +++Text(Topic.ProdNameLapChoice)+++
    （如果您使用了其他變量名稱，請替換變量名稱）

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image174.png)

12. 同樣，在 **Desktop** 和 **Tablet 分支下添加** Set variable value
    **節點** 。選擇 **將變量**值設置為 **ProdNameSelected**，然後插入 To
    value 字段的表達式，其中包含您所使用的變量名稱。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image175.png)

13. 在所有這些共同節點下添加一個 Action 節點，並調用 GetProductDetails
    流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image176.png)

14. 選擇要傳遞到流的 **ProdNameSelected**
    輸入變量。將其他值保留為默認值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image177.png)

15. 在 Action （作） 下方添加 Message （消息）
    節點，然後輸入以下消息。將 \<roductName\> 和 \<Price\>
    替換為相應的變量名稱

產品詳情

- 產品名稱 - \<ProductName\>

> ​

- 價格 - \<Price\>

​

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image178.png)

16. 在 message 節點下方，添加帶有 **消息的** Question 節點, +++Would you
    like to place order for this item?+++ in it. 添加選項 **Yes** 和
    **No** 到它，並將變量命名為 +++PlaceOrder+++.

![](./media/image179.png)

17. 在 Question 節點下，添加一個 condition
    節點，並在一個分支中添加一個條件 **PlaceOrder isequal to Yes**
    ，所有其他 **條件** 將成為 **第二個分支**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image180.png)

18. 調用流 **PlaceOrder** 作為下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image181.png)

19. 選擇 **ProductName** 和 **CustomerID** 作為流的輸入。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image182.png)

20. 現在，在此下方添加一個消息節點，其中包含消息, +++Your order is
    placed. This is your Order ID for reference -\<OrderID\>+++ (將
    **\<OrderID\>** 替換為變量 **OrderID** （流的輸出變量）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image183.png)

21. 這樣，**PlaceOrder isequal to Yes**
    分支就完成了。現在，導航到**所有其他條件分支**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image184.png)

22. 在此下方，添加一個 Question 節點，其中包含消息, +++Do you want to go
    to the main menu?+++ 使用選項 **Yes （是**） 和 **No**
    （否）。將變量命名為 +++**GoToMainMenu**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image185.png)

23. 在此節點下，添加一個條件節點，並在一個分支中添加一個條件，其中
    **GoToMainMenu is equal to Yes**。此條件的另一個分支將是 **All other
    conditions**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image186.png)

24. 在此 condition 節點下，添加一個帶有 message 的 question 節點
    +++**Select Product Category**+++ 並添加 3 個選項, +++**Laptop**+++,
    +++**Desktop**+++ 和 +++**Tablet**+++.

記下保存結果的變量名稱。我們將在下一步中將其轉換為文本。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image187.png)

25. 添加 **設置變量值** 節點，然後在 **設置變量 下選擇** ProductCategory
    **變量** ，然後輸入值作為 +++**Text(Topic.Var1)**+++ 在下面 **公式**
    標簽。

如果變量名稱不同，**請將** Var1 替換為變量名稱。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image188.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image189.png)

26. 在 Set variable value 節點下，添加 **Go to step** 節點。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image190.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image191.png)

27. 添加節點後，您必須選擇**步驟**，此時**控件應傳遞到**該步驟。
    **向上滾動**並選擇**本主題開頭的 Message
    節點**，因為您現在已從客戶那裡獲得
    **ProductCategory**，需要從頭開始執行。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image192.png)

28. 在帶有消息的末尾添加一個公共消息節點 +++Thank you for shopping with
    us! Please visit again!+++ 然後選擇 **Save （保存**） 以保存主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image193.png)

## 練習 4 – 添加觸發器 

在本練習中，您將添加一個觸發器，以便在 Order
表添加新行或修改現有行時啟動，並自動向客戶發送電子郵件。這定義了代理在此場景中的自主能力，

1.  選擇代理的 Overview （概述） 選項卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image194.png)

2.  向下滾動頁面，然後選擇 **Add trigger。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image195.png)

3.  選擇 **When a row is added, modified or deleted** 選項，然後選擇
    **Next**.

![](./media/image196.png)

4.  連接 Microsoft Copilot Studio **和** Dataverse **後** ，單擊下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image196.png)

5.  選擇以下選項，將其餘選項保留為默認值，然後選擇 **Create
    trigger（創建觸發器**）。

- Change Type – Added or Modified or Deleted

- Table name – Order Record

- 範圍 - 組織

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image197.png)

6.  這可能需要幾分鐘才能完成。完成後，在 **Add trigger 對話框中**選擇
    Close。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image198.png)

7.  在代理的 概述 頁面**的 觸發器 部分中** ，單擊 **添加的觸發器旁邊的**
    3 個點，然後選擇 **在 Power Automate 中編輯**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image199.png)

8.  選擇流程中的第一個節點並添加列名稱 +++cr6dd_orderidentifier,
    cr6dd_customeridentifier+++ 在 **Select columns**
    下。（將它們**替換為** Order Record 表中 **Order ID** 和 **Customer
    ID** 列的**邏輯名稱**）。

![](./media/image200.png)

9.  添加新節點，然後選擇 **List rows** 作。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image201.png)

10. 在 List rows （列出行）作中，選擇 **Table name （表名稱** ） 作為
    **Customer Record （客戶記錄**）。

在 Filter rows （篩選行**） 下**，輸入 +++**cr6dd_customeridentifier eq
''**+++, 將列名稱替換為您的客戶 **ID
的邏輯名稱**。將**光標保持在單引號內**。

![A screenshot of a list AI-generated content may be
incorrect.](./media/image202.png)

11. 選擇 Insert expression（插入表達式），輸入
    +++String(triggerOutputs()?\['body/cr6dd_customeridentifier'\])+++,
    將 **cr6dd_customeridentifier** 替換為 CustomerID
    的邏輯名稱，然後選擇 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image203.png)

12. 在 **List 行**旁邊，添加作 **Send an email （V2）。**

![A screenshot of a mail box AI-generated content may be
incorrect.](./media/image204.png)

13. 單擊 **Sign in （登錄** ） 並使用您的憑證登錄。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image205.png)

14. 在 **To** 字段中，插入表達式並輸入
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_emailaddress'\]+++，將
    **cr6dd_emailaddress** 替換為客戶記錄表中電子郵件 ID
    字段的邏輯名稱，然後選擇 **添加**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image206.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image207.png)

15. 輸入以下詳細信息，

主題 - +++Order Placement+++

內容 –

Hi,

這是為了通知您您的訂單已下達。感謝您在我們這裡購物。

謝謝。

16. 保存流程，然後選擇 Publish it 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image208.png)

17. 返回 Copilot Studio 代理頁面，選擇 **發佈** 以發佈代理。

![](./media/image209.png)

18. 在 確認對話框中選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image210.png)

19. ewqewqew

## 練習5 – 測試代理

在本練習中，您將測試代理的工作原理。

1.  在代理頁面中，選擇 **Test （測試**） 以打開 Test （測試） 窗格。

2.  輸入 +++3148987666+++. 這是現有客戶的電話號碼。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image211.png)

3.  從 **給定的選項**中選擇 Yes。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image212.png)

4.  從給定的選項**中選擇一個**產品。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image213.png)

5.  從給定的選項中選擇 Yes。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image214.png)

6.  下訂單並將參考 ID 提供給客戶。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image215.png)

7.  您還可以詢問其他問題，例如跟蹤您收到的 ID
    的訂單交付。雖然我們沒有為此配置主題，但它會根據知識來源給你回復。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image216.png)

通過選擇不同的選項來測試其他方案。添加新客戶，並檢查您的電子郵件 ID
中是否已收到已添加到 Customer Record 表的郵件。

## 總結:

在本實驗中，您學習了如何設計自主購物代理。涵蓋的主題包括：

- 變量

- 實體

- 主題

- 代理流程

- 觸發

- 知識來源

&nbsp;

- 
