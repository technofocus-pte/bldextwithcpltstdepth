# 實驗室——將招聘代理升級為自主系統

在本實驗中，你將深入研究**事件觸發器**，從而將你的智能體系統從被動響應提升到**自主運行**。你將使你的智能體不再等待人類輸入，而是主動響應外部事件，並在無需監督的情況下採取智能行動。

您可以將其視為從回答問題的客服人員升級為能夠預測需求並獨立行動的客服人員。通過事件觸發和自動化工作流程，您的**招聘代理**將檢測收到的簡歷**郵件**，自動處理附件，將數據存儲在
**Dataverse** 數據庫中，並通過 **Microsoft Teams**
**通知**您的**人力資源招聘團隊**——所有這些都能讓您專注於更有價值的任務。

**目標**

在這個實驗室裡，你會學到東西:

1.  事件觸發器如何實現無需用戶交互即可自主代理行為

2.  Copilot Studio 中交互代理與自主代理的區別

3.  如何創建自動處理郵件附件並將文件上傳到 Dataverse 的事件觸發器

4.  如何構建能夠向Teams頻道發佈自適應卡片以發送通知的代理流程

5.  如何在事件觸發器和代理流程之間傳遞數據，實現端到端自動化

**什麼是事件觸發器？**

*事件觸發*器讓代理在
其他系統發生事件時自動行動——無需用戶消息。當配置事件觸發時——例如“新SharePoint項目”、“新郵件”、“規劃工具任務分配中”，甚至基於時間的重複事件，連接器會向你的代理發送觸發負載。代理人隨後按照你的指示決定調用哪些動作或話題。

**交互代理與自主代理——比較**

既然你已經瞭解了事件觸發器和主題觸發的區別，接下來讓我們瞭解交互代理和自主代理之間的區別。

用Copilot
Studio的術語來說，“互動”映射到主要通過聊天或頻道中話題互動的客服。
“**自主**”映射到那些同樣利用**事件觸發**器在用戶輸入下運行的代理。

## 練習一：自動化候選人申請郵件

接下來我們將為**招聘代理**添加事件觸發器，並在子**應用接收代理**中構建代理流程，以處理後續的自主處理。

**用例場景**

**作為**人力資源招聘人員

**我希望**當簡歷郵件到達我的收件箱並自動上傳到Dataverse時，能收到通知

**這樣我就能**隨時收到通過郵件發送的簡歷，這些簡歷會自動上傳到Dataverse

我們將通過兩種技術實現這一點

1.  郵件到達時觸發事件，

    - 檢查內容，文件的格式類型等於PDF。

    - 通過 Dataverse 連接器的作提取文件並上傳到 Dataverse。

    - 然後通過傳遞Dataverse動作中的輸入參數，向代理發送提示，以便進一步處理。

2.  一個代理流會被添加到子**應用接收代理**中，該流程由事件觸發器中的提示調用。

    - 利用事件觸發提示中傳遞的輸入參數，通過一張自適應卡片發佈到Microsoft
      Teams的頻道，通知人力資源招聘團隊。自適應卡會有一個指向Dataverse行的鏈接，可以在**招聘代理中查看**。

### 任務一：自動將通過電子郵件收到的簡歷上傳到 Dataverse

1.  在招聘代理中，向下滾動到“**Overview**”**選項卡**中的“**Triggers**”部分，然後選擇**+
    Add trigger**。

> ![](./media/image1.png)

2.  此時將顯示觸發器列表。選擇“**When a new email arrives
    (V3)** ”，然後選擇“**Next**”。

> ![](./media/image2.png)

3.  在下一個屏幕中選擇“**Continue**”。

![](./media/image3.png)

4.  現在我們將看到所列應用程序的**觸發器名稱**和**登錄**連接引用。將觸發器名稱重命名為以下內​​容:

+++When a new email arrives from an applicant+++

> **注意：**
> 確保你看到每個應用連接引用旁的綠色標記。如果沒有看到綠色勾選，通過省略號（...）登錄，選擇
> ** + New connection reference** 以創建新的連接引用。
>
> ![](./media/image4.png)

5.  最後一步是設置觸發器的輸入屬性。將以下屬性更新為以下內容，

[TABLE]

6.  選擇 **Create trigger**。

> ![](./media/image5.png)

7.  創建完成後，將顯示一條確認消息，提示觸發器已添加到代理。選擇“**Close**”，觸發器將列在“**Triggers**”部分。

> ![](./media/image6.png)

8.  我們現在將更新事件觸發器，增加更多自動化功能。選擇觸發器旁的**省略號（...）**，然後選擇
    **Edit in Power Automate**。

> ![](./media/image7.png)

9.  觸發器隨後將作為流程加載到 Power Automate
    創建門戶中。它將打開流程設計器，我們可以在其中添加更多邏輯和操作以實現更高級的自動化。觸發器將顯示在頂部，其後的是“**Sends
    a prompt to the specified copilot for
    processing** ”作為流程中的最後一個操作。

> ![](./media/image8.png)

10. 默認情況下，如果同時收到多封電子郵件，Power Automate 中的“**When a
    new email
    arrives** ”觸發器可能會同時處理多封電子郵件，並且只會為該批次運行一次流程。

> 為了確保每封郵件的流程單獨運行，請選擇“When a new email
> arrives”節點，選擇 **Settings**。
>
> 在**觸發器的設置**中啟用“**Split On**”設置，並在下**拉數組字段**中選擇
> **@triggerOutputs()?\['body/value'\]** 。
>
> 開**Split
> On**模式，且數組字段設置為@triggerOutputs（）？\['body/value'\]，即使同時收到多個消息，流程也會單獨運行。
>
> ![](./media/image9.png)

11. 接下來，我們添加一些邏輯來檢查附件的文件類型。我們只想上傳 .PDF
    文件附件，而不是圖片附件（圖片可能來自電子郵件簽名）。選擇觸發器下方的“**+**”圖標，然後在“**Built
    in tools**”部分下選擇“**Control** ”。 

> ![](./media/image10.png)

12. 選擇 **Condition** 動作。

> ![](./media/image11.png)

13. 現在我們將配置條件，檢查文件附件的類型是否為 .PDF。在左側的“**Choose
    a value**”字段中，選擇**閃電圖標**。

> ![](./media/image12.png)

14. 在**搜索**字段中輸入+++content
    type+++，然後從觸發器中選擇“**Attachments Content-Type** ”參數。

> ![](./media/image13.png)

15. 我們先暫停一下，你可能注意到 **For each** 動作會自動出現。

> ![](./media/image14.png)
>
> 此操作表示遍歷電子郵件中的每個附件，因為 **Attachments
> Content-Type** 參數與每個附件相關聯。 
>
> 從底層來看，它是一個數組，這就是為什麼當我們在
> **Condition** 操作中選擇**Attachments
> Content-Type** 參數時，會自動添加“**For each**”操作的原因。

16. 接下來，在“**Condition** ”塊右側的另一個“**Choose a
    value** ”字段中，輸入+++application/pdf+++

這樣可以確保每個文件附件都會檢查擴展名格式是否.PDF。

> ![](./media/image15.png)

17. 現在我們將配置 **True** 路徑，從電子郵件中提取文件並將其上傳到
    **Resume** Dataverse 表中。

> 在**True**路徑下方添加一個新操作，並搜索“html to text”。搜索並選擇
> +++**Html to text**+++ 操作。 
>
> **注意：**Power Automate 中的“**HTML to text**”操作用於將 HTML
> 格式的內容轉換為純文本。當您收到包含 HTML
> 標簽的數據（例如電子郵件、網頁內容或 API
> 響應）並且只想提取可讀文本而不包含任何格式或代碼時，此功能尤其有用**。** 
>
> ![](./media/image16.png)

18. 接下來，我們需要通過選擇“**Create new**”來為 **Html to
    text** 操作創建一個新的連接引用。

> ![](./media/image17.png)

19. 現在可以配置操作了。讓我們從觸發器中添加“**Body**”參數。在“**Content** ”字段中，選擇右側的**閃電圖標**或
    **fx 圖標**。 

> ![](./media/image18.png)

20. 在“**Dynamic
    content** ”選項卡中，搜索“+++body+++”，然後選擇“**Body** ”參數，再選擇“**Add**”。

> ![](./media/image19.png)

21. 我們已經完成了這個動作的配置，現在選擇兩個指向左邊的角括號（«）來折疊面板，從而退出動作。

> ![](./media/image20.png)

22. 我們將通過選擇“**Html to
    text** ”操作下方的**“+”圖標**來添加新操作，這將加載添加操作面板。搜索“**Dataverse
    add**”，然後選擇“**Add a new row** ”操作。

> ![](./media/image21.png)

23. 在屬性面板的左上角粘貼 +++Add a new Resume row+++
    作為名稱，重命名該操作,

對於“**Table name**”參數，搜索 res 並選擇“**Resumes**”表。

> ![](./media/image22.png)

24. 接下來選擇“**Resume Title**”字段，然後選擇右側的 **fx 圖標**。 

> ![](./media/image23.png)

25. 在**Function**選項卡中，輸入使用 item() 函數的以下表達式。.

+++item()?\['name'\]+++

> 選擇“**Add**”將該表達式添加到“**Resume Title** ”參數中。 
>
> ![](./media/image24.png)

**關於 item（） 函數的說明:**

- 當您使用“**Apply to each** ”操作時，Power Automate
  會遍歷集合（數組）中的每個元素。

- 它最常用於“**Apply to each** （或 **For each**）、**選擇** 或 **Filter
  array**”等操作中。

26. 我們還需要配置更多參數，選擇**“Show all**”。

> ![](./media/image25.png)

27.  在 **Cover Letter** 欄中，選擇右側的 **fx 圖標**。

> 在**“Function”**標簽頁中，輸入以下表達式。
>
> +++if(greater(length(body('Html_to_text')), 2000),
> substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))+++
>
> 此表達式檢查從 **Html to text** 操作返回的文本是否超過 2000
> 個字符，如果超過，則僅返回前 2000 個字符；否則，返回全文。
>
> ![](./media/image26.png)

28. 該表達式現在將被添加到 **Cover Letter** 字段中。

> ![](./media/image27.png)

29. 對於“**Source Email
    Address** ”字段，選擇**閃電圖標**，並從觸發器中選擇“**From**”參數，因為其中包含電子郵件地址值。

> ![](./media/image28.png)

30. 在“**Upload Date**”字段中，選擇右側的 **fx
    圖標**。在“**Function**”**選項卡**中，輸入 +++utcNow()+++
    並選擇“**Add**”。 

**注意：什麼是utcNow（）函數？**

- Power Automate中的utcnow（）函數以ISO
  8601格式返回當前協調世界時（UTC）的日期和時間，類似：2025-09-23T04：32：14Z

> ![](./media/image29.png)

31. 我們現在已經完成了“**Add a new Resume
    row** ”作，所以讓我們通過折疊面板退出。

> ![](./media/image30.png)

32. 我們將通過點擊“**Add a new Resume
    row** ”操作下方的**“+”圖標**來添加新操作，這將打開添加操作的面板。搜索+++**Dataverse
    Upload**+++。選擇“**Upload a file or an image** ”操作。

> ![](./media/image31.png)

33. 通過將 +++Upload Resume File+++ 作為名稱來重命名動作。

> ![](./media/image32.png)

34. 接下來選擇“**Content
    name** ”字段（如果已有“未命名”消息，請將其刪除），然後選擇右側的
    **fx 圖標**。

> 在**Function
> 標簽頁**中，輸入以下使用項項（）函數的表達式。這會獲得當前項目（附件文件）的名稱屬性。
>
> +++item()?\['name'\]+++
>
> ![](./media/image33.png)

35. 對於“**Table
    name** ”參數，搜索“+++resumes+++”，然後選擇“**Resumes**”表。

> ![](./media/image34.png)

36. 接下來選擇 **Row ID** 字段，然後選擇右側的**閃電圖標**。

> 搜索 +++ID+++，然後從 Dataverse 的“**Add a new
> row** ”操作中選擇“**Resume**”參數，因為其中包含要上傳 PDF 文件的行的
> ID 值。
>
> ![](./media/image35.png)

37. 選擇“**Column name**”字段，然後選擇“**Resume PDF** ”選項。

> ![](./media/image36.png)

38. 選擇 **Content** 字段，然後選擇右側的 **fx 圖標**。 f

> 在**Function
> 標簽頁**中，輸入以下使用項項（）函數的表達式。這會獲得當前項目（附件文件）的contentBytes屬性。contentBytes
> 指的是文件或附件的原始二進制數據，編碼為 Base64 字符串。
>
> +++item()?\['contentBytes'\]+++
>
> ![](./media/image37.png)

39. 我們已經完成了這個動作的配置，現在選擇兩個指向左邊的角括號（«）來折疊面板，從而退出動作。

> ![](./media/image38.png)

40. 接下來，選擇“**Sends a prompt to the specified copilot for
    processing**”，然後將此操作拖放到條件“**True**”路徑中的“**Upload
    Resume File** ”操作下方。.

> ![](./media/image39.png)

41. 選擇“**Sends a prompt to the specified copilot for
    processing**”以進行配置。

![](./media/image40.png)

42. 在 **Body/message** 字段中，選擇所有字段內容並清除/刪除。

> ![](./media/image41.png)

43. 將以下文本複製並粘貼到 **Body/message** 字段中，選中“**RESUME ID
    PLACEHOLDER**”，然後選擇**閃電**圖標。

> Send \[ResumeId (text)\] = "RESUME ID PLACEHOLDER" and \[ResumeTitle
> (text_1)\] = "RESUME TITLE PLACEHOLDER" and \[ResumeNumber (text_2)\]=
> "RESUME NUMBER PLACEHOLDER" to the Tool "Notify Teams Applicant
> channel" in the child agent "Application Intake Agent"
>
> ![](./media/image42.png)

44. 搜索 +++resume+++，然後從 *Dataverse* 操作中 **Add a new
    row**，選擇“**Resume** ”參數，因為其中包含已創建的“簡歷”行的 ID 值。

> ![](./media/image43.png)

45. 請高亮 RESUME TITLE PLACEHOLDER。選擇右側的**閃電圖標**。

> 搜索 +++title+++，然後從 **Add a new row
> Dataverse** 操作中選擇“**Resume
> Title** ”參數，因為其中包含已創建的簡歷行的簡歷標題值。
>
> ![](./media/image44.png)

46. 選中“RESUME NUMBER PLACEHOLDER”。選擇右側的**閃電圖標**。

> 搜索+++resume number+++，然後從“**Add a new row
> Dataverse** ”操作中選擇“**Resume
> Number** ”參數，因為其中包含已創建的簡歷行的“簡歷編號”值。 
>
> ![](./media/image45.png)

47. 我們已經完成了此操作和代理流程的配置。現在，讓我們通過選擇“**Save**”來保存事件觸發流程。

> ![](./media/image46.png)

48. 現在我們需要編輯代理流程的細節，保存後選擇 **Back**。

> ![](./media/image47.png)

49. 在“**Details**”部分選擇“**Edit**”，並將“**Plan**”更新為“**Copilot
    Studio**”選項。選擇“**Save**”。

> ![](./media/image48.png)

50. 會顯示一個模態，要求你確認是否切換到Copilot Studio套餐。選擇
    **Confirm**。

> ![](./media/image49.png)

51. 該計劃現已更新為**Copilot Studio**。選擇
    **Edit **，因為我們需要為代理發佈事件觸發流程。

> ![](./media/image50.png)

52. 選擇 **Publish**。

> ![](./media/image51.png)
>
> 事件觸發流程現已發佈。

![](./media/image52.png)

讓我們繼續創建一個新的代理流，該流程將由子**Intake Application Agent**。

### 任務2 - 使用自適應卡通知Teams頻道

我們現在將為子 **Intake Application Agent** 創建一個新的代理流程
，使用事件觸發器傳遞的值，將自適應卡發佈到Teams頻道。這張自適應卡片會提醒人力資源招聘團隊自動上傳的PDF，以便他們進行審核。

#### 任務2.1：在Teams中創建頻道

在這個任務中，你將在MS
Teams中創建一個團隊和一個頻道，這些將在後續的實驗室中使用。

1.  登錄 +++https://teams.microsoft.com+++

2.  選擇“**New items**”**下拉菜單**，然後選擇“**New team**”。

![](./media/image53.png)

3.  請提供以下信息並選擇創建。

    - 團隊名稱- +++HR Team+++

    - 第一個頻道名稱- +++Applicants +++

> ![](./media/image54.png)

4.  在下一界面選擇跳過。

![](./media/image55.png)

5.  你現在創建了新的團隊和頻道。

![](./media/image56.png)

#### 任務2.2：創建代理流程

1.  返回 Copilot Studio，在 **Hiring
    Agent** 中選擇“**Agents**”選項卡，然後選擇“**Application Intake
    Agent**”。

![](./media/image57.png)

2.  向下滾動到 **Tools** ，選擇 **+ Add**。

> ![](./media/image58.png)

3.  此時將出現“**Add tool**”對話框。選擇 **+ New tool**。

> ![](./media/image59.png)

4.  選擇 **Agent flow**。

> ![](./media/image60.png)

5.  接下來將加載**代理流程設計器**。在“**When an agent calls the flow”**
    觸發器中，選擇**+ Add an input**。

> ![](./media/image61.png)

6.  選擇**Text** 作為用戶輸入類型。

> ![](./media/image62.png)

7.  在輸入文本字段中，輸入參數名稱為 +++ResumeId+++。

> ![](./media/image63.png)

8.  對以下參數重複同樣步驟。

文本- +++ResumeTitle+++

文本- +++ResumeNumber+++

![](./media/image64.png)

![](./media/image65.png)

9.  現在，你要在代理流程中添加一張自適應卡。我們現在會在代理流程中添加另一個動作，將自適應卡片發佈到Teams頻道。

選擇觸發器下方的**+圖標**。

> ![](./media/image66.png)

10. 搜索 +++**Microsoft Teams post+++** ，然後選擇在**Post card in a
    chat or channel** 操作。

> ![](./media/image67.png)

11. 需要用你登錄的用戶賬戶創建一個指向 Microsoft Teams 的連接引用。選擇
    **Sign in**。

> ![](./media/image68.png)

12. 選擇你的用戶賬戶，然後選擇**Allow access**。

> ![](./media/image69.png)

13. 根據以下輸入參數進行配置:

[TABLE]

> ![](./media/image70.png)

14. 接下來，我們將配置 **Adaptive Car d**片字段。選擇 **Adaptive
    Card** 片字段。 

> ![](./media/image71.png)

15. 複製下面的代碼並粘貼到自適應卡字段。

> {
>
> "type": "AdaptiveCard",
>
> "speak": "New Resume Uploaded",
>
> "body": \[
>
> {
>
> "inlines": \[
>
> {
>
> "type": "TextRun",
>
> "size": "Small",
>
> "text": "Resume table updated",
>
> "selectAction": {
>
> "url": "https://adaptivecards.io",
>
> "type": "Action.OpenUrl"
>
> }
>
> }
>
> \],
>
> "type": "RichTextBlock"
>
> },
>
> {
>
> "columns": \[
>
> {
>
> "width": "auto",
>
> "items": \[
>
> {
>
> "type": "Icon",
>
> "name": "DocumentArrowUp",
>
> "color": "Accent"
>
> }
>
> \],
>
> "type": "Column"
>
> },
>
> {
>
> "width": "stretch",
>
> "items": \[
>
> {
>
> "size": "Large",
>
> "text": "New Resume Uploaded",
>
> "weight": "Bolder",
>
> "wrap": true,
>
> "type": "TextBlock"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center",
>
> "spacing": "Small",
>
> "type": "Column"
>
> }
>
> \],
>
> "spacing": "Small",
>
> "type": "ColumnSet"
>
> },
>
> {
>
> "type": "Table",
>
> "targetWidth": "AtLeast:Narrow",
>
> "columns": \[
>
> {
>
> "width": 1
>
> },
>
> {
>
> "width": 2
>
> }
>
> \],
>
> "rows": \[
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Resume Number",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "RESUME NUMBER PLACEHOLDER",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Name",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "RESUME NAME PLACEHOLDER",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Status",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Waiting for Review",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Due Date",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "May 21, 2023",
>
> "wrap": true
>
> }
>
> \]
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Priority",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "ColumnSet",
>
> "columns": \[
>
> {
>
> "type": "Column",
>
> "width": "auto",
>
> "items": \[
>
> {
>
> "type": "Icon",
>
> "name": "Flag",
>
> "color": "Attention",
>
> "size": "xSmall",
>
> "horizontalAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "Column",
>
> "width": "stretch",
>
> "items": \[
>
> {
>
> "color": "Attention",
>
> "text": "Important",
>
> "wrap": true,
>
> "spacing": "Small",
>
> "type": "TextBlock"
>
> }
>
> \],
>
> "spacing": "Small"
>
> }
>
> \],
>
> "spacing": "Small"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> }
>
> \],
>
> "firstRowAsHeaders": false,
>
> "showGridLines": false
>
> },
>
> {
>
> "actions": \[
>
> {
>
> "title": "View Resume",
>
> "type": "Action.OpenUrl",
>
> "url": "https://adaptivecards.io/"
>
> }
>
> \],
>
> "type": "ActionSet",
>
> "targetWidth": "AtLeast:Narrow",
>
> "spacing": "ExtraLarge"
>
> }
>
> \],
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
>
> "version": "1.5"
>
> }

![](./media/image72.png)

16. 我們現在將用實際值或動態內容替換 JSON 負載中的現有值。

> 首先，我們需要更新 **selectAction** 屬性中 **url 屬性**的 URL。該
> **URL** 將被替換為**Hiring
> Hub** 模型驅動應用程序中“**Resumes**”系統視圖的
> URL。這樣，招聘人員就可以選擇該操作並跳轉到模型驅動應用程序中的“簡歷”系統視圖。
>
> 高亮**當前的 URL** 值並刪除它。

![](./media/image73.png)

17. 在 **Hiring
    Hub** 模型驅動應用程序中，使用左側菜單導航至“**Resumes**”系統視圖並複製
    URL。然後**返回代理流程**，並將**複製的** **URL** **粘貼**到
    selectAction 屬性中的 url 屬性中。

> ![](./media/image74.png)

18. 你應該會看到以下黃色高亮顯示的是**Hiring
    Hub**模型驅動應用的環境細節。

[TABLE]

> ![](./media/image75.png)

19. 接下來，我們將為多個屬性添加動態內容值。我們先從文本開始，它將顯示由事件觸發自動創建的行的
    Resume Number 引用。

選擇**面板**圖標加載動作面板。

![](./media/image76.png)

20. 向下滾動到你看到“RESUME NUMBER
    PLACEHOLDER”文本屬性的那一行。高亮占位值並刪除它。

![Delete placeholder](./media/image77.png)

21. 點擊雙引號之間，選擇右側的**閃電圖標**。

![](./media/image78.png)

22. 在“**Dynamic Content**”選項卡中，選擇“**ResumeNumber**”參數。 

> ![](./media/image79.png)

23. **ResumeNumber** 參數現在將作為動態內容添加到文本屬性中。

> ![](./media/image80.png)

24. 我們會重複同樣的步驟，針對簡歷名稱占位符。向下滾動到你看到“RESUME
    NAME
    PLACEHOLDER”文本屬性的那一行。高亮占位值並刪除它。點擊雙引號之間，從右側選擇**閃電圖標**。

> ![](./media/image81.png)

25. 在“**Dynamic Content** ”選項卡中，選擇“**ResumeTitle**”參數。

> ![](./media/image82.png)

26. **ResumeTitle** 參數現在將作為動態內容添加到文本屬性中。

> ![](./media/image83.png)

27. 我們將重複同樣的步驟，確定截**止日期值**，代表招聘人員應在何時審閱簡歷。向下滾動到你看到2023年5月21日文本屬性的那一行。

![Select Allow access](./media/image84.png)

28. 刪除這個日期占位符，點擊雙引號之間，選擇右側的 **fx圖標**。

> ![](./media/image85.png)

29. 在 **Function** 標簽頁中，輸入以下表達式並選擇 **Add**。

> +++addDays(utcNow(), 3, 'MMM dd, yyyy')+++

該表達式利用兩個函數。

[TABLE]

對於UTC現在的值，我們將日期格式化為月份和日期，後面是年份。

> ![](./media/image86.png)

30. The expression will now be added to the text property.

![](./media/image87.png)

31. 最後，我們將更新 JSON 有效負載底部 **actions** 數組屬性中 **url
    屬性**的 **URL**。當前占位符 URL 將被替換為 **Hiring Hub**
    模型驅動應用程序中“**簡歷”行**的
    URL。這樣，招聘人員就可以選擇自適應卡片的 **Action.OpenURL**
    操作，並跳轉到模型驅動應用程序中的“**Resume**”頁面。

> ![](./media/image88.png)

32. 在 **Hiring
    Hub** 模型驅動應用中，使用左側菜單打開“**Resumes**”系統視圖中的一行。該簡歷行將以表單的形式加載到模型驅動應用中。

複製簡歷行的URL。

![](./media/image89.png)

> ![](./media/image90.png)

33. 然後返回代理流程，選中當前占位URL值並 **刪除** 它。

> ![](./media/image91.png)

34. 然後將**複製的 URL 粘貼**到 **url** 屬性中的 url 屬性中。

> ![](./media/image92.png)

35. 你應該看到以下內容。刪除結尾的GUID
    ID值。我們將替換這個動態內容——**ResumeId**參數。

![](./media/image93.png)

36. 從右側選擇閃電圖標。

在 **Dynamic Content **標簽中，選擇 **ResumeId** 參數。

> ![](./media/image94.png)

37. **ResumeId**將作為動態內容添加。黃色標示的以下內容是**Hiring
    Hub**模型驅動應用的環境詳情。

[TABLE]

> ![](./media/image95.png)

38. 我們已經完成了在 **Post card in a chat or channel** 中配置帖子卡片
    👏🏻 選擇 **x** 圖標退出操作配置面板。

> ![](./media/image96.png)

39. 最後，我們將配置最後一個動作，通過**Respond to the
    agent** 發送文本來響應，以結束處理。

在“**Respond to the agent** ”動作中，選擇 **+Add a output**。

> ![](./media/image97.png)

40. 選擇**Text**作為輸出類型。

> ![](./media/image98.png)

41. 請輸入以下細節

    - 名稱 - +++EndConversation+++

    - 價值 - +++ Finished+++

> ![](./media/image99.png)

42. 我們現在已經完成了代理流程的配置。選擇 **Save
    draft** 以保存代理流程。保存後會出現確認消息。

> ![](./media/image100.png)

43. 發佈代理流程之前，我們需要更新代理流程的詳細信息。選擇“**Overview**”選項卡，然後選擇“**Edit**”。

> ![](./media/image101.png)

44. 輸入名稱 +++Notify Teams Applicant
    channel+++，然後選擇描述下的刷新圖標，使用 AI 更新它。

![](./media/image102.png)

45. 描述填充後，選擇 **Save** 以保存代理流程的更新細節。

> ![](./media/image103.png)

46. 返回 **Designer** 選項卡，選擇“**Publish**”以發佈代理流程。 

> ![](./media/image104.png)

47. 發佈後將顯示確認信息。

> ![](./media/image105.png)

48. 現在需要將代理流程作為工具添加到 **Application Intake Agent**
    中。返回**Hiring Agent**，選擇“**Agents**”選項卡，然後選擇
    **Application Intake Agent**。

![](./media/image106.png)

49. 在代理人的“**Details**”部分，我們將更新“**Description**”字段。複製以下內容並粘貼到描述文本的末尾。 

+++and also notifies the Teams Applicant channel+++

選擇 **Save**。

> ![](./media/image107.png)

50. 接下來，我們將把代理流程添加為一個工具。向下滾動到
    **tools** 部分，然後選擇 **+ Add**。 

> ![](./media/image108.png)

51. 選擇“**Flow**”選項卡，然後選擇之前創建的代理流程“**Notify Teams
    Applicant Channel**”。

> ![](./media/image109.png)

52. 選擇 **Add and configure**下一步。

> ![](./media/image110.png)

53. 在“**Inputs**”部分，可以看到我們之前在代理流程中配置的三個輸入。默認情況下，“**Fill
    using** ”配置設置為“**Dynamically fill with
    AI**”。我們將保持此設置不變，因為事件觸發器的提示將包含 AI
    將提取的參數值。

> ![](./media/image111.png)

54. 現在該工具已添加到 **Application Intake Agent**
    程序中，需要更新代理程序的指令。選擇**後退箭頭**。

![](./media/image112.png)

55. 在 **Hiring Agent** 的 **Agents** 選項卡中選擇 **Application Intake
    Agent**。

![](./media/image113.png)

56. 在“**Instructions**”欄中，在“**2.上傳後說明**”之後另起一行。複製並粘貼以下說明。

> Process for Resume Upload via Email
>
> 1. When you receive a message, \*\*Send \[ResumeId (text)\] =
> "1680265f-5793-f011-b41b-7c1e525be9f7" and \[ResumeTitle (text_1)\] =
> "TAYLOR TESTPERSON (FICTITIOUS).pdf" and \[ResumeNumber (text_2)\]=
> "R01026" to the Tool "Notify Teams Applicant channel"\*\* in the child
> agent "Application Intake Agent", call \[AGENT FLOW PLACEHOLDER\]
>
> ![](./media/image114.png)

57. 高亮\[AGENT FLOW PLACEHOLDER\] 文本。

> ![](./media/image115.png)

58. 輸入正斜杠字符 /，然後選擇“**Notify Teams Applicant
    Channel** ”工具。

> ![](./media/image116.png)

59. 現在，應用 **Application Intake
    Agent** 將按照指示調用代理流程，在事件觸發器中的最後一個操作（**向指定的
    copilot 發送提示進行處理**）之後，將包含參數值的提示發送回代理。

選擇“**Save**”以保存更新後的 **Application Intake Agent** 指令。

> ![](./media/image117.png)

60. 一旦代理被保存，說明將會更新。

> ![](./media/image118.png)

61. 現在我們需要**發佈** **Hiring Agent**
    信息。選擇右上角的“**Publish**”，然後在出現的“**Publish this agent
    modal **”對話框中選擇“**Publish**”。![](./media/image119.png)

> ![](./media/image120.png)

62. 發佈後，會出現確認提示，表示代理已被發佈。

> ![](./media/image121.png)

我們現在可以測試該藥劑了！

## 練習 3：測試事件觸發

在這個練習中，你將測試實驗室中創建的事件觸發器。

1.  要執行事件觸發器，需要發送一封帶有簡歷PDF文件的電子郵件。在Outlook中，撰寫一封新的電子郵件。

[TABLE]

> Dear Hiring Manager,
>
> I am writing to express my interest in the Senior Power Platform
> Engineer position at your organization. With over nine years of
> experience delivering secure and scalable solutions on Microsoft cloud
> platforms, I am confident in my ability to contribute effectively to
> your team.
>
> In my most recent role as Lead Power Platform Engineer, I developed an
> automated resume-intake pipeline, reducing manual triage and improving
> searchability. I have delivered HR case management applications,
> introduced solution-aware flows, and implemented PR checks to enhance
> deployment lead times. My expertise includes Power Apps, Power
> Automate, Power Pages, Dataverse, and a range of Microsoft 365
> services, as well as integration with Graph/REST APIs and Azure
> Functions.
>
> Previously, I developed Teams approvals with adaptive cards, cutting
> approval times to the same day, and created robust error-handling
> frameworks. My background also includes migrating legacy workflows to
> Power Automate and building self-service portals adopted by hundreds
> of employees.
>
> I hold a B.Sc. in Computer Science and am certified as a Power
> Platform Developer (PL-400) and Solution Architect (PL-600). I am also
> passionate about mentoring and have volunteered with local maker
> groups.
>
> Please find my CV attached for your consideration. I would welcome the
> opportunity to discuss how my skills and experience align with your
> needs.
>
> Thank you for your time and consideration.
>
> Kind regards,
>
> Taylor Testperson

2.  郵件從郵箱**發送**。

> ![](./media/image122.png)

3.  在事件觸發流程的 +++https://make.powerautomate.com/+++
    中，選擇刷新圖標以查看發送郵件成功運行的流程。你可以看到這股流動已經成功了。

> ![](./media/image123.png)

4.  返回 Copilot
    Studio，在招聘代理中選擇“**Activity**”選項卡。“**Activity**”選項卡將加載，其中顯示**Hiring
    Agent**的所有活動。其中會有一個名為“**Automated**”且狀態為“**Complete**”的活動。此活動代表觸發的事件以及調用的代理流程。

> ![](./media/image124.png)

5.  選擇活動，然後在活動地圖中選擇事件觸發器。在右側面板中，請注意提示中的輸入參數包含從已創建的
    **Dataverse** 行中獲取的“簡歷
    ID”、“簡歷標題”和“簡歷編號”參數值。這些值來自之前在“**Automate
    uploading resumes to Dataverse received by
    email**”中配置的動態內容值。

> ![](./media/image125.png)

6.  返回 **Hiring Hub** 模型驅動應用，在 **Resumes system view**
    中，選擇“**Refresh**”以刷新視圖。現在，通過電子郵件發送的簡歷的新創建行將顯示出來，因為它是通過事件觸發器創建的。

> ![](./media/image126.png)

7.  返回 Copilot Studio，在活動地圖的“**Application Intake
    Agent**”中選擇“**Notify Teams Applicant
    Channel** ”代理流程。在右側面板中，請注意輸入值來自 Dataverse
    行。這是由事件觸發器中最後一個操作（**Sends a prompt to the
    specified copilot for
    processing**）發送的提示信息，該事件觸發器包含來自新創建的 Dataverse
    行的參數值。這就是我們如何將參數值從事件觸發器傳遞到代理流程的方法。

> ![](./media/image127.png)

8.  最後，我們來看一下發佈到 **Microsoft Teams**
    頻道中的自適應卡片。在頻道中，我們會看到一張自適應卡片，它顯示了
    Dataverse
    中新創建的簡歷行的信息。將鼠標懸停在自適應卡片開頭的超鏈接上，你會發現該
    URL 是我們之前在自適應卡片的 JSON 有效負載中配置的簡歷系統視圖 URL。

> ![](./media/image128.png)

9.  選擇超鏈接後，您將被引導到瀏覽器中**Hiring
    Hub**模型驅動應用中的簡歷系統視圖。

> ![](./media/image129.png)

10. 返回Microsoft
    Teams中該頻道發佈的自適應卡片。這次，將鼠標懸停在**“View
    Resume**”上，即自適應卡的
    Action.OpenURL作。注意URL是我們之前在自適應卡JSON負載中配置的Resumes行。

> ![](./media/image130.png)

11. 選擇作後，你會被引導到瀏覽器中 Hiring Hub
    模型驅動應用中的“簡歷”行表單。

> ![](./media/image131.png)

## 摘要

在這個實驗室裡，

1.  你創建了一個事件觸發器，將Dataverse參數值傳遞給代理流程。

2.  構建了代理流程：消耗Dataverse參數值，將自適應卡片發佈到Microsoft
    Teams的某個渠道，以通知人力資源招聘團隊。

3.  更新的子代理指令：事件觸發完成後調用流程。

4.  這使得 **Hiring Agent**
    能夠在收到簡歷時自主工作，並通知人力資源招聘團隊進行人工審核。
