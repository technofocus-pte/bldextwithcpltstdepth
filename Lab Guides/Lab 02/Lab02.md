
# 實驗 02 – 構建自治代理來跟蹤在 OneDrive 中創建的新文件

**介紹**

組織的 OneDrive For Business
一直在其中創建多個文件，管理員很難跟蹤它們。

**目的**

構建一個自治代理，將新添加的文件的詳細信息輸入到 File Details
（文件詳細信息） 跟蹤器中。這解決了跟蹤文件添加的問題，並且 File details
（文件詳細信息） 跟蹤器將包含所有新創建文件的詳細信息。

## 練習 1：設置環境

1.  使用 Resources 選項卡中的密碼登錄到 VM。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

### 任務 1：設置 OneDrive

1.  打開瀏覽器並導航到 +++**https://office.com**+++。 使用 **Resources**
    選項卡中的憑證登錄

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  從 左側菜單中選擇 **OneDrive**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

3.  單擊 左上角的 + icon，然後選擇 **Files upload**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

4.  從 **C：\LabFiles** 中選擇文件 **File details** 並選擇 **Open**。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  上傳文件後，窗口中會彈出一條成功消息。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

6.  單擊左側菜單中的 **My files**，您可以看到新文件在那裡可用。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

### 任務 2 ：創建開發環境

1.  使用 Resources 選項卡中的租戶詳細信息[登錄到
    +++](https://admin.powerplatform.microsoft.com/)
    <https://admin.powerplatform.microsoft.com/>+++。

2.  選擇 **Environments** 從左側導航窗格中，然後單擊 **+ Newv。**

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  在打開的 New environment （新建環境）
    窗口中，填寫以下詳細信息，然後單擊 **Next**。

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image9.png)

![A screenshot of a computer Description automatically
generated](./media/image10.png)

4.  在 **Add Dataverse** 窗口中，接受默認值，然後單擊 **Save** 。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

5.  新創建的環境將在管理中心列出，其狀態在 Environments 窗格中。

6.  **Status** 為 **ready**
    後，環境即可使用。我們將在即將到來的練習中使用此環境。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

### 任務 3：啟用 Copilot Studio 試用版

1.  在新選項卡中，打開 +++**https://copilotstudio.microsoft.com/**+++。

2.  使用 實驗室 VM 的 **Resources** 選項卡下提供的 **Credentials**
    登錄。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  登錄後，**Welcome to Microsoft Copilot Studio**
    頁面，將國家/地區保留為 **United States** ，然後單擊 **Get Started**
    。

![A person sitting at a computer Description automatically
generated](./media/image14.png)

4.  在 **Welcome** 屏幕中選擇 **Skip** 。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

## 練習 2：構建和測試自治代理

### 任務 1：從 Copilot Studio 創建代理

1.  單擊打開的 Agent creation 頁面中的 Skip to configure 選項。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

2.  在代理創建窗格中，輸入以下詳細信息，然後單擊 **Create**。

- **Name** - +++New file tracker agent+++

&nbsp;

- **Description** - +++每次在 OneDrive
  中創建新文件時，此代理都會更新放置在 OneDrive 中的 File details
  tracker

![A screenshot of a computer Description automatically
generated](./media/image17.png)

### 任務 2：向代理添加觸發器

1.  創建代理後，向下滾動以找到 **Trigger** 部分。選擇 **+ Add
    trigger。**

![A screenshot of a computer Description automatically
generated](./media/image18.png)

2.  在 **Turn on generative orchestration to continue** 對話框中，選擇
    **Turn it on**。我們需要將此選項設置為 on 才能添加觸發器。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

3.  從 Add trigger 菜單中，選擇 **When a file is created** 觸發器。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  在 **Add trigger** 屏幕中，選擇 Continue 。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  在下一個屏幕中，請注意 **Trigger name** 已填充。等待 與 **Microsoft
    Copilot Studio** 和 **OneDrive for Business**
    建立連接（每個連接器都有一個綠色勾號）。然後，單擊 **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  選擇以下詳細信息。

- **Folder** – Root

- **Include subfolders** – Yes

> 將其他字段保留為默認字段，然後選擇 **Create trigger**。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  創建觸發器後，將顯示 **Time to test your trigger** 消息。 **Close**
    它。我們將稍微調整觸發器的基本流程以實現功能，然後對其進行測試。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

### 任務 3：向觸發器添加邏輯

1.  在 **New file track agent** 頁面中，向下滾動到觸發器部分。

2.  單擊觸發器 **When a file is created**上的 3 個點，然後選擇 **Edit in
    Power Automate**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  選擇 **+** icon **When the file is created** 和 **Sends a prompt
    action** ，然後選擇 **Add an action**。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  搜索 +++add a row+++，然後選擇 **Add a row into the table**。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

5.  為每行選擇以下值，然後單擊 **Save** 。

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image30.png)

![A screenshot of a computer Description automatically
generated](./media/image31.png)

6.  該流現在將類似於以下屏幕截圖中的流。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  保存流程並 **publish** 它。

### 任務 4：發佈觸發器

1.  返回 Copilot Studio，選擇 **Settings**。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

2.  選擇 **Security** -\> **Authentication** -\> **No authentication**
    ，然後單擊 **Save**。

![A screenshot of a computer Description automatically
generated](./media/image34.png)

3.  在 確認對話框中選擇 **Save**。

![A screenshot of a computer error Description automatically
generated](./media/image35.png)

4.  現在，選擇 **Publish** 以發佈代理。

![](./media/image36.png)

5.  在 確認對話框中選擇 **Publish**。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

### 任務 5：測試觸發器

1.  在瀏覽器中導航回 **OneDrive** 。點擊 **+** 並選擇 **Word
    document。**

![A screenshot of a computer Description automatically
generated](./media/image38.png)

2.  為文檔 **name** ，然後選擇 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

3.  單擊 **Close** 關閉隱私選項。

![A screenshot of a computer screen Description automatically
generated](./media/image40.png)

4.  以類似方式添加更多文件。

5.  現在，從 OneDrive 打開 File details.xlsx
    並觀察所創建文件的詳細信息是否已添加到跟蹤器中。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

6.  在 OneDrive 中創建文件時，將調用觸發器，該觸發器反過來會在 **When a
    file is added** 執行流並更新跟蹤器。

7.  您還可以在 Copilot Studio 的 Activity
    選項卡中查看自治代理的詳細信息。

**總結**

在本實驗中，我們學習了如何從 Copilot Studio 創建、發佈和測試自主代理。
