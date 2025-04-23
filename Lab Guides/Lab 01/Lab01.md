# 實驗 01：從 Copilot Studio 創建和使用代理來管理房地產應用程序

**實驗室持續時間** – 90 分鐘

**介紹**

Contoso Real Estate
專門從事商業和住宅物業的銷售和管理。目前，客戶信息有效地存儲在其
Dataverse 實例中，從而簡化了數據管理。然而，預訂過程帶來了重大挑戰。

目前，客戶只能通過電話申請預訂，導致電話線不堪重負，等待時間長。這種情況不僅讓客戶感到沮喪，而且還有可能失去潛在業務，因為許多人無法與辦公室聯繫以請求服務。

為瞭解決這些問題，Contoso Real Estate
致力於開發全面的數字解決方案。該解決方案將使客戶能夠輕鬆訪問有關預訂流程的信息並在線提交預訂請求。

**目標**

- 從 Copilot Studio 為 Contoso Real Estates
  構建獨立代理（這將允許客戶發現有關房地產預訂流程的信息，並創建預訂請求供辦公室查看。

- Create Topics （創建主題） 以設置預訂的邏輯。

- 創建預訂所需的 Dataverse 表。

- 發佈 Copilot。

:::danger **實驗 03** 需要在第 1 天結束前完成，才能執行第 2
天的實驗。即使實驗 01 和 02 未完成，也請確保在第 1 天結束時完成實驗
03。:::

## 練習 0：設置環境

### 任務 1：登錄到 VM

1.  使用 **Home** 選項卡中的 **Username** 和 **Password** 登錄到 VM。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

### 任務 2：同步 VM 時鐘

1.  登錄到 VM 後，右鍵單擊屏幕右下角的時鐘。

2.  選擇 **Adjust date and time**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  在打開的 設置 屏幕上，單擊 其他設置 下的 **Sync now 。**

![](./media/image3.png)

4.  這負責同步時間，以防自動同步不起作用。

5.  **關閉** Settings 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

6.  如果有 **Sign in required** 警報，請單擊  **Sign In** ，然後選擇
    **Sign in with a different account** ，然後使用 VM 的 **Home**
    選項卡中提供的 **admin credentials** 登錄。

![A blue screen with white text AI-generated content may be
incorrect.](./media/image5.png)

![](./media/image6.png)

7.  選擇 **Sign in to this app only** 。

![](./media/image7.png)

8.  登錄後，**關閉** **Teams** 應用程序。我們將在第 3 天的實驗中使用它。

## 練習 1：設置 Power Apps 和 Dataverse

### 任務 1：註冊 Microsoft Power Apps 開發人員計劃

1.  打開瀏覽器並導航到
    !\!<https://powerapps.microsoft.com/free/>!!，然後選擇 **Start
    free** 或 **Try for free** 。

![](./media/image8.png)

2.  如果出現提示，請在 **Home** 選項卡中使用 Office Tenant
    Credentials **Username** 和 **Password** 登錄。這將是您實驗室所有
    Microsoft 網站和應用的 **login credentials** 。

![](./media/image9.png)

3.  在 **Let's get started**
    下，在文本框中輸入 **Home** 選項卡中的 **Administrative
    Username**，選中協議框並選擇 **Start free**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

4.  如果您看到一條提示，指出您已有 Microsoft 賬戶。選擇 **Sign in**
    。輸入您的密碼。

5.  如果出現提示，請選擇 **Yes** 以保持登錄狀態。

6.  單擊 屏幕右上角的 **Environment** 並確保選中 **Dev
    One**。如果沒有，請選擇 **Dev One**。

![](./media/image11.png)

### 任務 2：創建解決方案

1.  來自 Power Apps Maker 門戶 (!\!<https://make.powerapps.com/>!!)，從
    左側窗格中選擇 **Solutions**。

![](./media/image12.png)

2.  單擊 **+ New solution**。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image13.png)

3.  進入 **!!Bookings!!** 對於顯示名稱，在 **Publisher** 下選擇
    **Contoso （contoso），**然後單擊 **Create**。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image14.png)

如果 **Contoso** 選項未列在 **Publisher** 下，請執行接下來的 2
個步驟，否則從步驟 6 繼續。

4.  如果 **Contoso** 選項未列在 **Publisher** 下，請選擇 **+ New
    Publisher。**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

5.  輸入以下詳細信息，然後單擊 **Save**。

[TABLE]

> ![](./media/image16.png)

6.  選擇 屏幕左上角的 **Back to solutions**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

### 任務 3：設置首選解決方案

1.  在 Maker 門戶中的 Solutions 下，為 **Set your preferred solution**
    選擇 **Manage**。

![](./media/image18.png)

2.  在 **Unless otherwise specified** 下選擇**“Bookings
    （contoso）”，save my changes in **，然後選擇 **Apply**。

![](./media/image19.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

### 任務 4：創建 Real Estate Properties 自定義表

有 2 種方法可以創建新表。一種是傳統的手動方法，另一種是使用 Copilot。

#### 任務 4.1：使用 Copilot 創建房地產屬性自定義表

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

創建具有以下列和數據類型的表 “Real Estate Property” -  
1. Property Name - Single line of text  
2. Asking Price - Currency   
3. Street - Single line of text  
4. City - Single line of text  
5. Client - Data type Lookup, Related table - Contact  
  
在 Real Estate Property 表中再添加兩列 Bedrooms 和 Bathrooms，每列都有
Datatype 選項 -  
1. Label - 1, Value - 1  
2. Label - 2, Value -2  
3. Label - 3, Value 3  
4. Label - 4, Value 4  
5. Label - 5, Value 5

 

使用以下列和數據類型創建表 “Booking Request” -  
1. Booking Name - Single line of text  
2. Property - Data type Lookup, Related table - real estate property  
3. View name - Single line of text  
4. Viewer Email - Single line of text  
5. Booking Date - Date and time  
6. Notes - Multiple lines of text

 

在具有數據類型選項的 Booking Requests 表中添加另一列 Decision -  
1. Label - Undecided, Value - 1  
2. Label - Accepted, Value -2  
3. Label - Declined, Value 3

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

創建所有列後，在 **Real Estate Property columns and data**
下，輸入以下測試數據：

- Property Name: !!**1100 High Villas**!!

- Asking Price: !!**250,000**!!

- Bathrooms: **3**

- Bedrooms: **2**

- City: !!**Redmond**!!

- Street: !!**Main Avenue**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

#### 任務 4.2：使用 Copilot 創建 Real Estate Properties 自定義表

按照以下步驟在 Dataverse 中手動為房地產屬性創建新的自定義表。

1.  在左側導航窗格中，選擇 **Tables，**選擇 **+ New table**
    旁邊的下拉列表 ，然後選擇 **Create new tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  單擊 **Let's set up your data** 對話框中的 **Got it** 。

![](./media/image32.png)

3.  在 Create new tables 屏幕上，單擊 **+ New table -\> Add columns and
    data**。

![](./media/image33.png)

4.  將表名稱從 **Table1** 重命名為 !!**Real Estate
    Property**!!，然後單擊 **Save and exit**。

![](./media/image34.png)

5.  單擊 確認對話框中的 **Save and exit**。

![](./media/image35.png)

6.  保存後，單擊 **Custom** 選項卡以在此處找到新創建的表。單擊 **Real
    Estate Property** 表。

![](./media/image36.png)

7.  在 **Real Estate Property columns and data**下，將名為  **New
    Column** 的列的名稱更改為 **New
    Column**（單擊新列旁邊的下拉列表**，**然後選擇 **Edit Column**
    並更新 **Display name**）更改為 !!**Property Name**!!，然後選擇
    **Save** 。

![](./media/image37.png)

8.  選擇 + 按鈕，在 columns and data 窗格中添加新列。在 New column
    窗格中，輸入以下值，然後選擇 **Save**。

    - Display name: !!**Asking Price**!!

    - Data type: Currency

![](./media/image38.png)

![](./media/image39.png)

9.  添加以下兩列。

[TABLE]

10. 添加另一個具有以下值的列

    - **Display name**: !!Bedrooms!!

    - **Data type**: Choice -\> Choice

![](./media/image40.png)

創建選擇值:

在 **Sync this choice with**下選擇 **+ New Choice**

![](./media/image41.png)

- 在 **Choices** 下，將 Display name 提供為 !!**Bedrooms**!!.

&nbsp;

- 您會看到兩個標題為 **Label** 和 **Value** 的輸入字段。 在標簽下輸入
  **1**。Power Apps 會自動分配一個值，但您可以將該值更改為 **1**。

&nbsp;

- 選擇 **+ New choice **，並將 **2** 作為 Label 的新條目，將 **2** 作為
  Value 的新條目。

 

- 選擇 **+ New choice**，並將 **3** 作為 Label 的新條目，將 **3** 作為
  Value 的新條目。

 

- 選擇 **+ New choice**，並將 **4** 作為 Label 的新條目，將 **4** 作為
  Value 的新條目。

 

- 選擇 **+ New choice**，並將 **5** 作為 Label 的新條目，將 **5** 作為
  Value 的新條目。

 

- 選擇 **Save** 。

![](./media/image42.png)

通過單擊 S**ync this choice with**的下拉列表，選擇添加的選項
**Bedrooms**

![](./media/image43.png)

點擊 **Save** 。

![](./media/image44.png)

11. 選擇 **+** 按鈕，在 columns and data 窗格中添加新列。

12. 在 New column 窗格中，輸入以下值，然後選擇 **Save** :

    - **Display name**: !!Bathrooms!!

    - **Data type**: Choice -\> Choice

![](./media/image45.png)

創建選擇值:

在 **Sync this choice with**下選擇 **+ New choice** 。

- 在 **Choices** 下，將 Display name 提供為 !!Bathrooms!!。

- 您會看到兩個標題為 **Label** 和 **Value** 的輸入字段。在標簽下輸入
  **1**。Power Apps 會自動分配一個值，但您可以將其更改為 **1**。

- 選擇 **+ New choice**，並將 **2** 作為 Label 的新條目，將 **2** 作為
  Value 的新條目。

- 選擇 **+ New choice**，並將 **3** 作為 Label 的新條目，將 **3** 作為
  Value 的新條目。

- 選擇 **+ New choice**，並將 **4** 作為 Label 的新條目，將 **4** 作為
  Value 的新條目。

- 選擇 **+ New choice**，並將 **5** 作為 Label 的新條目，將 **5** 作為
  Value 的新條目。

- 選擇 **Save**。

![](./media/image46.png)

選擇創建的選擇，然後單擊 **Save** 在列添加窗格中。

![](./media/image47.png)

13. 通過在列和數據窗格中再次選擇 **+** 按鈕來添加另一列。

在 New column 窗格中，輸入以下值，然後選擇 **Save** ：

- **Display name**: !!**Client**!!

- **Data type**: Lookup -\> Lookup

- **Related Table**: Contact

![](./media/image48.png)

14. 創建所有列後，在 **Real Estate Property columns and data**
    下，輸入以下測試數據：

:::secondary 注意：如果未顯示所需的列，請通過選擇 **+\<number\>more**
來調整顯示的列 :::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

- 屬性名稱: !!**1100 High Villas**!!

- 要價: !!**250,000**!!

- 浴室: **3**

- 臥室: **2**

- 城市: !!**Redmond**!!

- 街: !!**Main Avenue**!!

- 客戶: **選擇任何連絡人**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

:::secondary 注意：如果  **Contact** 表中沒有 **client ** 端記錄
，請忽略向該列添加數據。:::

### 任務 5：創建 Bookings 表

按照以下步驟在 Dataverse 中為房地產預訂創建新的自定義表。

1.  從左側導航窗格中，選擇 **Tables** ，然後選擇 **Create new tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

2.  在 **Create new tables** 屏幕上，單擊 **+ New table -\> Add columns
    and data**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

3.  將表名稱從 **Table1** 重命名為 !!**Booking Request**!! ，然後單擊
    **Save and exit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

4.  單擊 確認對話框中的 **Save and exit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

5.  保存後，單擊 **Custom** 選項卡以在此處找到新創建的表。單擊 **Booking
    Request** 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  將名為 **New Column 的**列的名稱更改為 !!Booking
    Name!!（單擊旁邊的下拉菜單 **New Column** 並選擇 **Edit Column**
    並更新 **Display name**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  單擊 列名稱旁邊的 **+** symbol。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  使用下面指定的名稱和數據類型創建以下列。選擇 **Save** 。

- Display name – !!Property!!

- Data type – Lookup -\> Lookup

- Related Table – Real Estate Property

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

- Display name – !!Viewer Name!!

- Data type – **Single line of text**

 

- Display name – !!Viewer Email!!

- Data type – **Single line of text**

- Format – **Email**

 

- Display name – !!Booking Date!!

- Data type – **Date and time**

 

- Display name – !!Notes!!

- Data type – **Multiple lines of text**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

1.  添加包含以下詳細信息的 choice 數據類型列。

- Display name – !!Decision!!

- Data type – Choice -\> Choice

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

在 **Sync this choice with下**，單擊 **+ New Choice**。輸入**Display
name**為 **!!Decision!!.**

輸入以下詳細信息，然後單擊 **Save** 。

- Label – !!**Undecided**!!

- Value – 1

- Label – !!**Accepted**!!

- Value – 2

- Label – !!**Declined**!!

- Value – 3

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

在 **Sync this choice with** 字段下選擇添加的 Choice **Decision**，指定
**Undecided** 作為 **Default choice**，然後單擊 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

## 練習 2：使用 Copilot Studio

### 任務 1：註冊 Copilot Studio 試用版

1.  在瀏覽器中的新選項卡中，導航到 url
    !\!<https://copilotstudio.microsoft.com/>!!.

2.  將 **Choose your country/region** 保留為 **default**，然後單擊
    **Start free trial**。

![A person sitting at a computer AI-generated content may be
incorrect.](./media/image63.png)

3.  單擊 左上角的 **Environments**，然後選擇 **Dev One**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

4.  如果您 收到 Welcome to Copilot Studio，請選擇 **Skip**！提示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

### 任務 2：創建 Real Estate Booking Service 代理

1.  從 左側導航窗格中選擇  **Create** 創建 ，然後選擇 ** New agent**
    磁貼。

![A screenshot of a software AI-generated content may be
incorrect.](./media/image66.png)

2.  選擇 **Skip to configure**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  填寫以下詳細信息。

    - Name - !!**Real Estate Booking Service**!!

    - Description - !!**Create bookings for real estate properties**!!

    - Instructions - !!**Create a copilot for topics relating to
      creating bookings for real estate properties!!**

    - Language **–** Select **English**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  選擇屏幕右上角的 Create 按鈕旁邊的三個點，然後選擇 **Edit advanced
    settings**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  選擇 **Bookings** 解決方案，然後選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  在屏幕的右上角，選擇 **Create**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  創建代理後，在 Test your copilot 窗格中，輸入 !**How do I make a
    booking?!!，**然後單擊 **Enter** 並觀察響應。您將收到一個通用響應。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

### 任務 3：配置安全性

1.  選擇 屏幕右上角的 **Settings。**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image73.png)

2.  選擇 **Security** 選項卡，然後選擇 **Authentication** 磁貼。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

3.  選擇 **No authentication** 並單擊 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

4.  在 **Save this configuration** 提示中選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

5.  保存身份驗證設置後，單擊 **Close **選項以關閉 **Settings** 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

### 任務 4：禁用您不需要的主題

示例主題包含在新的 Copilot 中。刪除這些示例主題。禁用不需要的系統主題。

1.  從 Copilot 概述頁面的頂部菜單中選擇 **Topics** 選項卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

2.  您將進入 **Custom** Topics 頁面。

3.  選擇 **System** 選項卡。將 **Sign in** 主題的 **Enabled** 切換為
    **Off**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

### 任務 5：發佈和測試 Copilot

1.  選擇 **Publish** 以發佈此代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

2.  在 **Publish this agent** 對話框中選擇 **Publish** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

### 任務 6：演示網站

Demo 網站允許沒有許可證的用戶測試您的
Copilot。您可以向他們提供演示網站的 URL。

1.  選擇 **Settings** 旁邊的 **three dots** 或 屏幕右上角的 **Publish**
    按鈕，然後選擇 **Go to demo website**。

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image82.png)

2.  在 **Type your message** 文本框中，輸入 **! !What information is
    needed to book a viewing for a real estate property?!!**
    並觀察代理的響應。

![A screenshot of a chatbot AI-generated content may be
incorrect.](./media/image83.png)

它將是通用的，類似於您在 在 Studio 中測試您的代理
中獲得的那個，因為我們尚未配置任何特定主題，也尚未為代理實施任何邏輯。我們將在即將到來的練習中執行此作。

## 練習 3：使用 Copilot 創建和管理主題

### 任務 1：使用 Copilot 創建主題

可以使用自然語言創建和編輯主題。

1.  在 **Copilot Studio** 打開的情況下導航回瀏覽器選項卡。在 **Topics **
    選項卡中，選擇 **Add a topic** ，然後選擇 **Create from description
    with Copilot.**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

:::secondary:::
**注意：**如果提示查看複製到剪貼板的文本和圖像，請選擇允許 :::

2.  輸入以下詳細信息，然後單擊 **Create**。

    - Name your topic - !!**Customer Details**!!

    - Create a topic to... - !!**Ask the customer for their name and
      email address**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

3.  此時將顯示一個新主題，其中包含觸發短語和問題節點。

4.  選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

### 任務 2：使用自然語言更新節點

1.  如果 屏幕右側未顯示 **Edit with copilot** 窗格，請選擇創作畫布上部的
    **Copilot** 圖標。

2.  選擇第二個問題節點 **What is your email address？**

3.  在 **Edit with Copilot** 面板的 **What do you want to
    do? **字段中，輸入以下文本：

!!**Update the message in this question node to say thank you to the
Name variable from the previous node and then proceed to ask the email
address question**!!

::: :::

4.  選擇 **Update**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

5.  選擇 **Save**。![A screenshot of a computer AI-generated content may
    be incorrect.](./media/image88.png)

### 任務 3：使用自然語言添加節點

除了添加更新現有節點外，您還可以使用 Copilot 添加新節點。

1.  通過單擊節點周圍的空白區域，確保未選擇任何節點。

2.  在 **What do you want to do?** 字段中，輸入以下文本，然後選擇
    **Update。**

!!**Add a new multiple-choice question to prompt the user if the details
are correct with two options Yes or No**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

3.  新的問題節點將添加到主題末尾，其中包含供用戶選擇的選項。

4.  在問題部分，內容下方的細節 **Are the details
    correct?**，輸入以下內容。

> \<h3\>Summary\</h3\>
>
> \<p\>\<strong\>Full Name:\</strong\>
>
> Name string
>
> \</p\>
>
> \<p\>\<strong\>Email Address:\</strong\>
>
> EmailAddress string
>
> \</p\>
>
> 通過選擇 **{x}** 符號，將 \<p\> 標記內的 **Name string** 和 **Email
> address string** 替換為相應的變量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

5.  選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### 任務 4：配置變量的範圍

1.  選擇 **Variables** 以打開 Variables 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

2.  我們有接收值的變量和返回值的變量。我們的 topic 變量將返回原始 topic
    的值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

3.  選中主題變量的右側複選框，然後單擊 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

## 練習 4：手動創建和管理主題

### 任務 1：從零開始創建主題

1.  選擇 **Topics** 選項卡。

2.  選擇 **Add a topic** ，然後選擇 **From blank** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

3.  選擇 **Details** 以打開 主題詳細信息 對話框。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

4.  填寫以下詳細信息，然後單擊 **Save**。

    - **Name** - !!Book a Real Estate Showing!!

    - **Display Name –** !!**Book**!!

    - **Description** - !!Select the property and requested date and
      create a booking request!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

5.  選擇 **Details** 以關閉 Topic details 對話框。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

### 任務 2：添加觸發短語

1.  在 **Trigger** 中的 **Phrases** 下選擇 **Edit** 。進入

> **!!I want to book a real estate showing!!** ，然後選擇 **+** 圖標。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

2.  逐個輸入以下短語。輸入 **+** 後選擇圖標。

    - !!**Schedule a real estate showing**!!

    - !!**Arrange the viewing for a real estate property**!!

    - !!**Set up an appointment to view a house**!!

    - !!**Plan a property viewing**!!

&nbsp;

1.  添加所有短語後，選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

### 任務 3：添加消息節點

1.  選擇 **Trigger** 節點下的 + icon，然後選擇 **Send a message**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

2.  在 **Enter a message** 字段中，輸入以下文本：

!!Hi, I can help you with booking a real estate property showing.!!

3.  選擇 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

### 任務 4：添加 Topic 管理節點

1.  選擇 **send a message** 節點下的 **+** icon，然後選擇 **Topic
    management -\> Go to another topic**。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image103.png)

2.  選擇 **Customer Details** 主題。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

3.  選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

### 任務 5：添加條件節點

1.  選擇 主題管理節點下的 + 圖標，然後選擇 **Add a condition**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

2.  選擇 **DetailsCorrect** for variable。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image107.png)

3.  選擇 **Condition** as **is equal to**

4.  選擇 **value **作為 **Yes** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

5.  選擇 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

### 任務 6：添加問題節點

1.  選擇 左側條件節點下的 **+** icon，然後選擇 **Ask a
    question**。填寫以下詳細信息，然後單擊 **Save**。

    - **Enter a message**  - !!Which property do you want to see?!!

    - **Identify** - 選擇**User's entire response**.

    &nbsp;

    - **Save user response as** Enter **!!PropertyName!!** 對於
      **Variable name**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

1.  選擇 問題節點下的 + 圖標，然後選擇 **Ask a
    question**。填寫以下詳細信息，然後單擊 **Save。**

    - **Enter a message** - !!What date and time do you want to see the
      property?!!

    - Identify - 選擇**Date and Time**

    - **Save user response as** – 單擊 **Var1** 打開 Variable properties
      窗格並輸入 **!!DateTime!!** 對於 **Variable name**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

### 任務 7：測試 Copilot

1.  選擇 屏幕右上角的 Test 按鈕以打開測試面板。選擇
    屏幕右上角的測試面板頂部的 **three dots** 。選擇 **Track between
    topics** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

2.  當 **Conversation Start** 消息出現時，您的 Copilot 將開始對話。

3.  作為響應，輸入您創建的主題的觸發短語：

!!I want to book a real estate showing!!

4.  Copilot 回答說：**"What is your name?"** 問題。

5.  輸入您的姓名。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image113.png)

6.  然後在 系統提示輸入 **email**
    時輸入您的電子郵件。輸入詳細信息後，將顯示一個問題，詢問信息是否正確，並提供用於選擇
    **Yes** 或 **No** 的選項。選擇 **Yes**。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image114.png)

7.  進入 !!555 Oak Lane, Denver, CO 80203!! 到 **Which property to you
    want to see？** 提示。

8.  進入 **!!Tomorrow 10:00 AM!!** 到 **What date and time you want to
    see the property？** 提示。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image115.png)

## 練習 5：構建一個 Autonomous 代理，在創建或更新預訂時自動發送電子郵件

本練習旨在展示 Autonomous 代理的 **When a row is added， modified or
deleted** 觸發器。

### 任務 1：創建代理

1.  單擊 左側導航窗格中的 **Agents**。

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image116.png)

2.  單擊 **+ New agent** 創建新代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

3.  單擊 **Skip to configure** 以配置代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

4.  輸入以下詳細信息，然後單擊 **Create**。

**Name** - !!Autonomous agent!!

**Description** - !!You are an agent to detect the updates to the
Booking Requests table!!

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image119.png)

5.  代理設置需要幾秒鐘才能完成。完成後，Autonomous 代理將打開，並顯示
    **Your agent is ready** 消息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

6.  選擇 **Settings ** 從右上角。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

7.  必須啟用 Generative AI 選項才能繼續為代理創建 Trigger。

8.  從 **Settings** 屏幕左側的選項列表中選擇 **Generative AI** 選項。在
    **Using generative AI in conversations**下，選擇 **Generative**
    式點擊 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

9.  關閉 **Settings** 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

### 任務 2：向代理添加觸發器

1.  返回 自治代理 頁面，向下滾動到 **Triggers (preview) **部分，然後選擇
    **+ Add trigger** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

2.  從 **Add trigger** 屏幕中選擇 **When a row is added， modified or
    deleted** 觸發器。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image125.png)

3.  在 下一個屏幕中單擊 **Continue**。

4.  選擇後， **Trigger name** 和 **Sign in options**
    將加載到下一個屏幕中。這將需要幾分鐘時間才能填充。對於我們選擇的觸發器，將有兩個應用程序，一個是
    **Microsoft Copilot Studio**，另一個是 **Microsoft Dataverse**。

5.  加載後，確保登錄選項的連接狀態為綠色，然後單擊 **Next** 繼續。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image126.png)

6.  在 Add trigger 屏幕中，選擇以下詳細信息，然後單擊 **Create
    trigger**。

    - 更改類型 – **Added or modified**

    - 表名稱 – **Booking Requests**

    - 範圍 – **Organization**

    - 觸發指令 – 保留為 **default**。這會將整個響應返回給代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image127.png)

7.  觸發器創建可能需要 3 到 5 分鐘才能完成。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

8.  完成後，單擊 **Close** in the **Time to test your trigger! **屏幕。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

9.  單擊 **Actions** 選項卡，然後選擇 **+ Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

10. 尋找 !!Send an email!!，然後選擇 **Send an email （V2） action**。

![A screenshot of a email conversation AI-generated content may be
incorrect.](./media/image131.png)

11. 建立連接後，單擊 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

12. 選擇 **Copilot author Authentication** 作為 **End user
    authentication**下拉列表中的選項，然後選擇 **Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

13. 選擇 created Action。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

14. Select the **Inputs** tab.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

15. 在 **Description** 字段中提供郵件需要傳送到的電子郵件 ID，然後單擊
    **Save**。這可以是您可以訪問的任何郵件 ID。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image136.png)

### 任務 3：向代理添加說明

1.  選擇 **Overview** 轉到 Overview 頁面，然後單擊 Overview 頁面中的
    **Edit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

2.  將下面的說明粘貼到 **instructions** 文本區域內，將下面 b
    部分中\<郵件 ID\> 的占位符替換為 需要將詳細信息發送到的郵件
    ID，然後單擊 **Save**。

!!a. Read the details of the row that gets added or modified!! !!b. Mail
the modified information only to \<Mail ID\> with a proper subject and
body added to the email!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

3.  單擊 **Publish** 將代理發佈到它所連接的所有渠道。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

4.  單擊 **Publish this agent** 對話框中的 **Publish**。

![A screen shot of a computer AI-generated content may be
incorrect.](./media/image140.png)

5.  發佈後，您將收到一條成功消息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

### 任務 4：更新 Bookings 表

1.  登錄 ！！<https://make.powerapps.com/>！！，然後從
    左側導航窗格中選擇 **Tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

2.  選擇  **Custom**  ，然後從中選擇 **Booking Request** 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image143.png)

3.  在表中添加或更新值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

### 任務 5：測試代理

1.  在代理頁面中，選擇 Test，然後打開 **Activity Map**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

2.  在代理頁面中，選擇 **Test trigger** 選項。我們在 Bookings
    表中所做的更新將觸發觸發器。我們將使用它從 copilot studio 進行
    **test** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

3.  選擇最新條目，然後單擊 **Start testing**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image147.png)

4.  觸發器被調用。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

5.  郵件將發送到指定的郵件 ID。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

6.  檢查相應的郵箱，查看您是否收到了如下郵件。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

**總結**

在本實驗中，我們學習了

- 從 Copilot Studio 構建代理並在其中創建主題。

- 從 Copilot Studio 測試代理並將其發佈到演示網站。

- 構建自治代理並進行測試

 
