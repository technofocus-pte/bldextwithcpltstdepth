# 實驗室 04 - 使用 Gen AI 功能增強房地產copilot

**實驗室持續時間** – 80 分鐘

**目的：**

在 Copilot for Real Estate
應用程序中實施實體、槽填充和變量使用。通過實施生成式 AI 來增強為 Real
Estate 應用程序創建的 copilot，以提升客戶體驗。

## 練習 1：使用實體改進 Copilot

Microsoft Copilot Studio
使用實體來瞭解用戶意圖。包含許多用於常用信息的預生成實體。您可以針對您的特定目的創建自定義實體。

### 任務 1：查看預生成實體

1.  在 !\!<https://copilotstudio.microsoft.com>!! 並打開代理 **Real
    Estate Booking Service。**

2.  選擇 屏幕右上角的 **Settings**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  選擇 **Entities** 選項卡。您可以看到預構建實體的列表。

![](./media/image2.png)

### 任務 2：創建屬性類型實體

1.  選擇 **+ Add an entity**，然後選擇 **+ New entity**。

![](./media/image3.png)

2.  選擇 **Closed list** 磁貼。

![](./media/image4.png)

3.  輸入以下詳細信息

    - 名字 - !!Property Type!!

    - 在 List items下輸入 item – !!Apartment!! - 選擇 **Add**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

4.  進入 !!Condominium!! 在 **Enter item** 字段中，然後選擇 **Add**。

5.  進入 !!Duplex!! 在 **Enter item** 字段中，然後選擇 **Add**。

6.  進入!!House!! 在 **Enter item** 字段中，然後選擇 **Add**。

![](./media/image6.png)

7.  選擇 **Apartment** 的 ** + Synonyms**，輸入 **!!Flat!!** ,然後選擇
    **+** icon 並選擇 **Done**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  選擇 **House** 的 **+ Synonyms**，輸入 **!!Single-family home!!**
    ,然後選擇 **+** ** **icon 並選擇 ** Done**。

9.  選擇 **Condominium** 的 **+ Synonyms**，輸入 !!**Townhouse**!!
    ,然後選擇 **+** icon 並選擇 **Done**。

10. 選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. 選擇 **Close**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

### 任務 3：創建臥室數量實體

1.  選擇 **+ Add an entity** ，然後選擇 **+ New entity** 。

![](./media/image10.png)

2.  選擇 **Regular expression （Regex）** 磁貼。

![](./media/image11.png)

3.  輸入以下詳細信息，然後單擊 **Save** 。

    - Name - !!**Number of Bedrooms**!!

    - Pattern - !!**\[1-5\]**!!

![A screenshot of a cell phone AI-generated content may be
incorrect.](./media/image12.png)

4.  選擇 **Close**。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image13.png)

5.  關閉 **Settings** 窗格。

![](./media/image14.png)

### 任務 4：使用實體

- 選擇 **Topics** 選項卡。選擇 **Book a Real Estate Showing** 主題。

![](./media/image15.png)

- 選擇 屬性問題節點上方的 + icon，然後選擇 **Ask a question**。

![](./media/image16.png)

> 3\. 填寫以下詳細信息。

- **Enter a message** - !!What type of property do you want to see?!!

- **Identify** – 選擇**Property Type**

- 選擇 **Select options for user** 並選中 Display 所有列表值的
  **Display** 選項。

![](./media/image17.png)

4.  在 **Save user response as** 中選擇變量 ，然後輸入
    **!!PropertyType!!** 對於 **Variable name**

![](./media/image18.png)

5\. 選擇 新問題節點下方的 **+** icon，然後選擇 **Ask a question**。

> 6\. 輸入以下詳細信息，然後單擊 **Save** 。

- **Enter a message** - !!How many bedrooms do you need?!!

- **Identify -** 選擇 **Number of Bedrooms**

- **Save user response as** - 進入!!NumberofBedrooms!! 對於 **Variable
  name**

![](./media/image19.png)

## 練習 2：創建動作

Microsoft Copilot Studio 可以使用 Power Automate 雲端流訪問 Microsoft
Dataverse 中的數據

### 任務 1：創建 Power Automate 流以檢索屬性

1.  從 頂部菜單中選擇 **Actions** 選項卡。選擇 **+ Add an action**。

![](./media/image20.png)

2.  選擇 **+ New action** -\> **New Power Automate flow**。

![](./media/image21.png)

3.  如果出現提示，請登錄到 Power Automate。

4.  在右上角，啟用切換 **New designer** 。選擇 **Save and switch**。

![](./media/image22.png)

5.  選擇屏幕左上角的 **Run a flow from Copilot** 並輸入 **!!Get
    Property!!** 作為流程名稱。

![](./media/image23.png)

6.  選擇觸發步驟從 **Run a flow from Copilot** ，然後選擇 **+ Add an
    input**。

![](./media/image24.png)

7.  選擇 **Text** 。

![](./media/image25.png)

8.  輸入以下詳細信息

    1.  **Input** – !!Bedrooms!!

    2.  **Please enter your input** - !!Number of Bedrooms!!

![](./media/image26.png)

9.  右鍵單擊 流程中兩個步驟之間的 + icon，然後選擇 **Add an action**。

![](./media/image27.png)

10. 在 **Search** 搜索字段中輸入 **!!Dataverse!!**，然後選擇查**See
    more** **Microsoft Dataverse connector**。

\![\](./media/image27.png)

11. 選擇 **List rows** action。

![](./media/image28.png)

12. 如果系統提示進行身份驗證，請選擇 **OAuth** 並選擇 **Sign in**
    。如果出現提示，請使用您的租戶 ID 登錄。

![](./media/image29.png)

13. 選擇 **Real Estate Properties** 作為表名稱。

14. 如果 所有選項未自動列出**，**請選擇 **Show all**

15. 進入 !!contoso_bedrooms eq!! 在 **Filter Rows** 字段中。

16. 在 **eq** 旁邊使用 **spacebar **以確保在空格後添加值。使用 **Dynamic
    content** 選擇 **Bedrooms** 參數，然後選擇 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

17. 選擇 **Respond to Copilot** action，然後選擇 **+ Add an output**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

18. 選擇 **Text**。

19. 輸入以下詳細信息

    - **Enter a name** - !!PropertyId!!

    - **Enter a value to respond with** - 選擇 **Insert expression**
      並輸入以下表達式:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_realestatepropertyid'\]!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

20. 選擇 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

21. 從 !\!<https://make.powerapps.com>!!,打開表 **Real Estate
    Property**。導航到其列 Property Name（這可能是 Real Estate Property
    或使用 Copilot 創建時略有不同）\>編輯列 \> 高級選項。查找 **Logical
    name** 的值。它應該類似於
    **contoso_newcolumn**。也可能略有不同。在本地保存 contoso\_
    後存在的部分 。如果 Logical name （邏輯名稱） 為
    **contoso_newcolumn**，請記下 **newcolumn** 以供下一步使用。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

22. 返回 Power Automate 流頁面，選擇 **+ Add an output**。

23. 選擇**Text**。

    - **Enter a name** - !!PropertyName!!

    - **Enter a value to respond with** - 選擇 **Insert expression**
      並輸入以下表達式:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]!!

將上述表達式中 **contoso_propertyname** 中的 **propertyname** 替換為
this（**newcolumn）** 之前的步驟中保存的值。

::: secondary 此值替換需要完成，因為此列的 Logical name
不是標準值，我們必須根據 Table 中的值進行檢查和更新. :::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

24. 選擇 **Settings** 。確保 **Asynchronous Response** 設置為 **Off**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

25. 選擇 **Save draft** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

26. 保存後，選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

27. 關閉 Power Automate 選項卡。

### 任務 2：添加用於檢索屬性的 Copilot作

1.  返回 Copilot Studio 頁面，選擇 **Refresh**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

2.  選擇 **Get Property** 流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  選擇 **Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

4.  選擇 **Topics** 選項卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  選擇 **Book a Real Estate Showing** 主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

6.  選擇 **How many bedrooms do you need question?** 下方的 **+ icon**
    node 並選擇 **Add an action**。選擇 **Get Property** 流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  為 **Bedrooms** 輸入參數選擇 **NumberofBedrooms** 變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

8.  選擇 **Which property do you want to see?**  問題節點中的 **three
    dots** ，然後選擇**Delete**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  選擇 作節點下的 + icon，然後選擇 **Send a message** 。

10. 填寫以下詳細信息

    - **Enter a message** - enter !!Property!!

    - 選擇 **Insert variable** 圖標，然後選擇 **PropertyName** 變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

11. 選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

12. 保存後，選擇 **Publish ** ，然後選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

13. 單擊 **Publish** 確認對話框中的 Publish。

![A close-up of a white background AI-generated content may be
incorrect.](./media/image50.png)

### 任務 3：創建 Power Automate 流以進行預訂

1.  選擇 **Actions** 選項卡，然後選擇 **+ Add an action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

2.  選擇 **+ New action** -\> **New Power Automate flow**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

3.  選擇屏幕左上角的 **Run a flow from Copilot** 並輸入 **!!Booking
    Request!!** 作為流程名稱。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

4.  選擇觸發步驟從 **Run a flow from Copilot** ，然後選擇 **+ Add an
    input -\> Text**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

5.  輸入以下詳細信息

    - Input - !!**PropertyId**!!

    - Please enter your input **-** !!**Property**!!

6.  選擇 **+ Add an input -\> Text**

    - Input - !!**ViewerName**!!

    - Please enter your input **-** !!**Viewer Name**!!

7.  選擇 **+ Add an input -\>** **Text**.

    - Input - !!**ViewerEmail**!!

    - Please enter your input **-** !!**Viewer Email**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  選擇 流中兩個步驟之間的 **+** icon，然後選擇 **Add an action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

9.  在 **Search** 字段中輸入 **!!Dataverse!!**，然後選擇 **See more**
    Dataverse connector。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

10. 選擇 **Add a new row** action。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

11. 選擇 **Booking Requests** 作為表名稱。

12. 進入 **!!Copilot booking!!** 在 **Booking Name** 字段中。

13. 選擇 **Show all**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

14. 進入 !!contoso_bookingrequests()!! 在 **Property （Real Estate
    Properties）** 字段中，將光標移動到括號內，並使用 **Dynamic
    content**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

15. 選擇 **PropertyId** 參數。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

16. 使用 **Dynamic content** 為 **Viewer Name** 字段選擇 **ViewerName**
    參數 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

17. 使用 **Dynamic content** 為 **Viewer Email** 字段選擇
    **ViewerEmail** 參數 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

18. 這些參數現在看起來與下面屏幕截圖中的參數類似。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

19. 選擇  **Respond to Copilot** 作。選擇 **Settings** 並確保
    **Asynchronous Response** 設置為 **Close**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

20. 選擇 **Save draft**。![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image67.png)

21. 保存後，選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

22. 關閉 Power Automate 選項卡。

### 任務 4：添加用於創建預訂請求的 Copilot作

1.  返回 Copilot Studio 頁面，選擇 **Refresh**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

2.  選擇 **Booking Request** 流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

3.  選擇 **Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

4.  在 Review inputs and outputs 中選擇 **Next** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

5.  在 **Review and finish** 屏幕中選擇 **Finish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

6.  選擇 **Topics** 選項卡，然後選擇 **Book a Real Estate Showing**
    主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

7.  選擇 **What date and time do you want to see the
    property?** 節點下方的 + icon，然後選擇 **Add an action**。

8.  選擇 **Booking Request** 流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

9.  為 **PropertyId** 輸入參數選擇 **PropertyId** 變量。

為 **ViewerName** 輸入參數選擇 **Name** 變量。

為 **ViewerEmail** 輸入參數選擇 **EmailAddress** 變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

10. 選擇 作節點下方的 + icon。選擇 **Topic management，**然後選擇  **Go
    to another topic **並選擇 **End of conversation**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

11. 選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

12. 保存後，選擇 **Publish** ，然後在 確認對話框中再次選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 練習 3：測試代理

### 任務 1：測試代理並發出預訂請求

1.  選擇 屏幕右上角的 **Test** 按鈕以打開測試面板。選擇
    屏幕右上角的測試面板頂部的 **three dots**。選擇 **Track between
    topics**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  當 **Conversation Start** 消息出現時，您的代理將啟動對話。

3.  作為響應，輸入您創建的主題的觸發短語:

!!I want to book a real estate showing!!

4.  Copilot 回答說：**What is your name?"** 問題。

5.  輸入您的姓名。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image82.png)

6.  然後在系統提示輸入電子郵件時輸入您的電子郵件。輸入詳細信息後，將提示一個問題，詢問信息是否正確，以及選擇
    **Yes** 或 **No** 的選項。選擇 **Yes**。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image83.png)

7.  選擇 **House** 作為屬性提示的類型。

8.  進入 !!**2**!! 以獲取 Number of Bedrooms 提示。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image84.png)

9.  進入 !!Tomorrow 2:00 PM!! 到 **What date and time you want to see
    the property？** 提示。

10. 選擇 **Yes** 到 Did **that answer your question？** 提示。

11. 選擇任意評級。

12. 對 **Can I help with anything else?** 選擇 **No** 提示。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image85.png)

### 任務 2：驗證預訂請求

1.  導航到 Power Apps 門戶
    !\![**https://make.powerapps.com**](https://make.powerapps.com)!!.

2.  在左側導航窗格中，選擇 **Tables** ，然後選擇 **Custom**。

3.  選擇 **Booking Request** 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

4.  在 ** Booking Request columns and data **下，您應該會看到 Copilot
    預訂請求現已創建。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

## 練習 4：設置 Generative AI

在本練習中，您將學習如何使用 Generative answers 功能來改進 Copilot
的響應。

### 任務 1：啟用 Generative AI

1.  使用您的租戶憑據登錄 Copilot Studio
    !\!<https://copilotstudio.microsoft.com>!! 如果尚未登錄。

2.  選擇代理 **Real Estate Booking Service**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

3.  選擇 屏幕右上角的 **Settings。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

4.  選擇 **Generative AI** 選項卡。

在 **How should your copilot decide how to respond**下選擇
**Generative(preview) **。

對於 **how strict should the content moderation be?**請選擇 **Medium**。

選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

5.  **關閉** Settings 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### 任務 2：啟用知識

1.  單擊 **Overview** 選項卡。

2.  驗證是否在 Knowledge 部分啟用了 general knowledge。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

### 任務 3：從網站添加知識

1.  選擇 **Knowledge** 部分下的 **+ Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

2.  選擇 **Public websites** 磁貼。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

3.  進入公共網站鏈接
    !\!<https://create.microsoft.com/templates/real-estate>!! 選擇
    **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

4.  給名字 !!Real Estate Website!! 在 Name 字段中，然後選擇 **Add** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

### 任務 4：從 Dataverse 添加知識

1.  選擇 **knowledge** 選項卡。選擇 **+ Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

2.  選擇 **Dataverse(preview)** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

3.  選擇 **Real estate Property** 表，然後選擇 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

4.  在下一個屏幕中預覽數據，然後選擇 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

5.  查看詳細信息，然後單擊 Review and finish 屏幕中的 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

### 任務 5：從文件添加知識

1.  從 **Knowledge** 選項卡中，選擇 **+ Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

2.  在 **Upload files** 部分下，選擇 **click to browse**，然後瀏覽以在
    **C：\LabFiles SummitRealtyCaseStudy.docx** 找到文件並選擇它。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

3.  選擇 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

:::danger
**Important：**文件上傳將完成，索引將需要一些時間才能完成。檢查
Knowledge 選項卡中的狀態，以確保文件可用。 :::

### 任務 6：在系統回退主題中使用生成式答案

1.  選擇 **Topics** 選項卡，然後選擇 **System**。選擇 **Fallback**
    主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

2.  選擇 消息節點中的 **three dots**，然後選擇 **Delete** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

3.  選擇 Condition 節點下的 **+** icon，選擇 **Advanced**，然後選擇
    **Generative answers**。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image107.png)

4.  選擇 **Input** 字段，在 **Select a variable** 窗格中選擇
    **System**。從中選擇 **Activity.Text**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

5.  在 **Data sources**下選擇 **Edit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

6.  選擇 **Search only selected sources**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

7.  選擇 **SummitRealtyCaseStudy** 文檔。取消選擇 **Allow the AI to use
    its own general knowledge**。選擇 **Medium** 作為 **Content
    moderation**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

8.  選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

### 任務 7：配置安全性

1.  選擇 **Overview** 選項卡。

2.  選擇 屏幕右上角的 **Settings**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

3.  選擇 **Security** 選項卡，然後選擇 **Authentication** 磁貼。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

4.  選擇使用 Microsoft 進行身份驗證 **(Entra ID authentication in Teams
    and Power App)。**

5.  選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

6.  選擇 **Save**。

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image116.png)

7.  選擇 **Close**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

8.  選擇 **Overview** 選項卡。

9.  選擇 **Publish**，然後在對話框中再次選擇 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### 任務 8：測試代理的知識

1.  選擇 屏幕右上角的 **Test** 按鈕以打開測試面板。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  選擇 **Activity map** 如果尚未選擇。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  選擇 **Refresh** 按鈕 測試 面板 **Start a new conversation**。

4.  輸入 !!What is Summit Realty group?!! 然後點擊 **Send**。

5.  您將從上傳的文件獲得響應，如下面的屏幕截圖所示，因為它已添加為要在
    Fallback 主題中查找的知識源。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

**總結：**

在本實驗中，我們學習了

- 使用實體和槽填充

- 實施 Flow actions

- 向代理添加知識

- 啟用 Generative AI

 
