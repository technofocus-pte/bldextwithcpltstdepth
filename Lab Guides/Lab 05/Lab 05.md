# 實驗室——將招聘代理轉變為可擴展的多代理架構

在之前的實驗室裡，你構建了主招聘代理，為管理招聘流程打下了堅實基礎。但一個代理人能做的有限。

如果你接受這項任務，那就是 **Operation Symphony** -
將你手下的單個特工轉型為**多特工系統**：一支由各領域專家組成的協同作戰團隊，共同應對複雜的招聘挑戰。你可以把它理解為從單打獨鬥的特工升級為指揮一支特種部隊。

就像交響樂團中每位音樂家完美和聲地演奏自己的部分一樣，你將為現有的招聘代理增加兩位關鍵專家：一位自動處理簡歷的申請接待員，以及一位負責製作全面面試材料的面試準備員。這些代理將在你的主編排器下無縫協作。

創建多智能體後，您將將智能體從等待人類輸入轉變為主動響應外部事件，並在無監督下採取智能行動。

可以把它看作是從回答*問題的代理*升級為能夠*預見需求*並*獨立行動*的代理。通過事件觸發器和自動化工作流程，您的招聘代理將檢測收到的簡歷郵件，自動處理附件，將數據存儲在Dataverse中，並通過Microsoft
Teams通知人力資源招聘團隊——而您則專注于更高價值的任務。

## 目標

在這次任務中，你將學到東西:

1.  何時使用**子代理**與**連接代理**

2.  如何設計 可擴展的**多智能體架構**

3.  為聚焦任務創建**子代理**

4.  建立 代理之間的**通信模式**

5.  構建申請接待代理和麵試準備代理

6.  事件觸發器如何實現無需用戶交互即可自主代理行為

7.  Copilot Studio 中交互代理與自主代理的區別

8.  如何創建自動處理郵件附件並將文件上傳到 Dataverse 的事件觸發器

9.  如何構建能夠向Teams頻道發佈自適應卡片以發送通知的代理流程

10. 如何在事件觸發器和代理流程之間傳遞數據，實現端到端自動化

## 子代理：申請接收代理

讓我們開始構建我們的多代理人招聘系統。我們的首位專家將是**申請接納代理**——一位負責處理新簡歷和候選人信息的兒童代理。

![](./media/image1.png)

**應用接收代理的職責**

- **解析**通過互動聊天提供的PDF**簡歷內容**（在未來的任務中，你將學會如何自主處理簡歷）。

- **提取結構化數據**（姓名、技能、經驗、教育背景）

- 根據資歷和求職信**匹配候選人與空缺職位**

- 將候選信息**存儲在Dataverse中以便後續處理**

- **減少申請重疊**，避免重複創建同一候選人，並利用簡歷中提取的電子郵件地址與現有記錄匹配。

**為什麼這應該是兒童代理人**

申請接收代理作為子代理非常合適，因為:

- 它專門用於文檔處理和數據提取

- 它不需要單獨出版

- 這是我們整體招聘解決方案的一部分，由同一團隊管理

- 它聚焦於特定觸發條件（收到新簡歷），由招聘代理調用。

## 關聯代理：面試準備代理

我們的第二位專家是**面試準備代理**——一個互聯的代理，幫助製作全面的面試材料並評估候選人回答。

**面試準備代理職責**

- **製作**包含公司信息、職位要求和評估標準的**面試包**

- 針對特定職位和候選人背景**生成針對面試問題**

- **回答**關於職位崗位和申請的**常見問題**，以便與利益相關者溝通

**為什麼這應該是一個連接的代理**

面試準備代理作為聯絡代理工作效果更好，因為:

- 人才招聘團隊可能希望在多個招聘流程中獨立使用它

- 它需要自己的面試最佳實踐和評估標準知識庫

- 不同的招聘經理可能希望為他們的團隊定制其行為

- 它可以被用於內部職位，而不僅僅是外部招聘

## 練習1 - 添加應用接收代理

讓我們把我們的第一位子代理添加到你現有的招聘代理中。

### 任務1 - 解決方案設置

1.  在 Copilot Studio 中，選擇左側導航工具下方的省略號（...）。

2.  選擇 **Solutions**。

> ![](./media/image2.png)

3.  找到您的**Operative**解決方案，點擊其旁邊的**省略號
    (...)**，然後選擇“**Set preferred
    solution**”。在彈出的對話框中點擊“**Apply**”。這將確保您的所有工作都添加到此解決方案中。

> ![](./media/image3.png)

4.  在“Set your preferred solution”對話框中選擇應用。

![](./media/image4.png)

### 任務2 - 配置你的招聘代理指示

1.  **導航**到Copilot Studio。確保你的環境在右上角的 **Environment
    Picker** 中被選中**。**

2.  打開 **Hiring Agent**。

3.  在代理的“**Overview** ”選項卡的“**Instructions**”部分中選擇“**Edit** ”。

![](./media/image5.png)

4.  複製粘貼以下指令到指令輸入中。

**你是招聘流程的核心協調者。你協調活動，提供摘要，並將工作委派給專業代理人。**

5.  選擇**Save**。

> ![](./media/image6.png)

6.  選擇屏幕右上角的 **Settings** 按鈕。

> ![](./media/image7.png)

7.  檢查頁面，確保以下設置已應用，然後選擇 **Save**。

[TABLE]

> ![](./media/image8.png)
>
> ![](./media/image9.png)
>
> ![](./media/image10.png)
>
> ![](./media/image11.png)

8.  點擊 右上角的**X**鍵可以關閉設置菜單

> ![](./media/image12.png)

### 任務3 - 添加應用接收子代理

在此任務中，你將向招聘代理添加一個子代理。

1.  在您的招聘代理中**導航**到“**Agents**”選項卡（您可以在這裡添加專業代理），然後選擇“**Add**”。

![](./media/image13.png)

2.  選擇 **New child agent**。

![](./media/image14.png)

3.  填寫您的代理人**姓名** +++Application Intake Agent+++

4.  選擇“**The agent chooses**  - **When will this be
    used?** ’下拉菜單中的描述”。這些選項類似於可以為主題配置的觸發器。

5.  將**描述**設置為 - +++Processes incoming resumes and stores
    candidates in the system+++

![](./media/image15.png)

6.  展開**Advanced**，並將優先級設置為10000。這樣可以確保面試代理在本次採訪前會被用來回答一般性問題。這裡也可以設定一個條件，比如確保至少有一個附件。

![](./media/image16.png)

7.  確保“**Web
    Search**”開關設置為“**Disabled**”。這是因為我們只想使用父代理提供的信息。選擇“**Save**”。

![](./media/image17.png)

### 任務4 - 配置恢復上傳代理流程

代理在沒有工具或主題的情況下無法執行任何作。

我們使用**代理流程工具**而非主題來完成*上傳簡歷*步驟，因為這個多步後臺流程需要確定性執行並與外部系統集成。雖然主題是引導對話對話的最佳選擇，但代理流程提供了結構化自動化，能夠可靠地處理文件處理、數據驗證和數據庫更新（插入新內容或更新現有內容），而無需依賴用戶交互。

1.  在申請接收代理頁面中找到“**Tools**”部分。 

> **重要提示：**這不是父代理的工具標簽，但如果你在子代理指示下方向下滾動可以找到。

2.  選擇 **+ Add**。

> ![](./media/image18.png)

3.  選擇 **+ New tool**。

> ![](./media/image19.png)

4.  選擇 **Agent
    flow**。代理流程設計器會打開，這裡我們會添加上傳簡易邏輯。  
    ![](./media/image20.png)

5.  選擇“**When an agent calls the flow**”，然後選擇“ **+ Add an
    input**” 

> ![](./media/image21.png)

6.  為 下表中列出的每個參數添加
    **inputs**。選擇表格中顯示的正確輸入類型，並確保同時添加名稱和描述。包含描述很重要，因為這能幫助代理知道該填寫哪些內容。

[TABLE]

> ![](./media/image22.png)

7.  選擇代理調用流程節點下方的 **+ 圖標**，搜索 +++Dataverse
    add+++，然後在 **Microsoft Dataverse** 部分選擇“**Add a new
    row** ”操作。

> ![](./media/image23.png)
>
> ![](./media/image24.png)

**注意**

添加動作後，可能會提示你創建新的Dataverse連接。輸入連接的任意名稱，點擊添加即可創建該連接。

8.  將節點命名為 +++Create Resume+++，方法是選擇 3 點並選擇 **Rename**。
     

> ![](./media/image25.png)

9.  將 **Table name**  設置為“**Resumes**”，然後選擇“**Show
    all**”，以顯示所有參數。

> ![](./media/image26.png)

10. 設置以下**屬性**:

[TABLE]

> ![](./media/image27.png)
>
> ![](./media/image28.png)
>
> ![](./media/image29.png)

11. 選擇“Create Resume”節點下方的**“+”圖標**，搜索 +++Dataverse
    upload+++ ，然後選擇“**Upload a file or an image** ”操作。

![](./media/image30.png)

12. 將節點命名為 +++**Upload Resume File**+++。

> ![](./media/image31.png)

13. 設置以下**屬性**:

[TABLE]

> ![](./media/image32.png)

14. 選擇“**Respond to the agent**”**節點**，然後選擇“ **+ Add an
    output**”。創建一個具有下表中定義的屬性的輸出。

> ![](./media/image33.png)

[TABLE]

> ![](./media/image34.png)

15. 在右上角選擇“**Save draft** ”

> ![](./media/image35.png)

16. 選擇“**Overview** ”選項卡，在“**Details** ”面板中選擇“**Edit** ”。按照如下所示填寫名稱和描述，然後選擇“**Save**”

    1.  **流程名稱**:+++Resume Upload+++

    2.  **描述**:+++Uploads a Resume when instructed+++

> ![](./media/image36.png)

17. 再次選擇“**Designer**”選項卡，然後選擇“**Publish**”。

> ![](./media/image37.png)

### 任務5 - 將流程連接到你的代理

現在你將發佈的流程連接到你的申請接收代理。

1.  返回 **Hiring Agent**，選擇“代理”選項卡。打開**Application Intake
    Agents**代理，找到“**Tools**”面板，然後選擇“**+Add**”。  
    ![](./media/image38.png)

2.  選擇“**Flow**”篩選器，然後選擇“**Resume Upload**”流程。 

> ![](./media/image39.png)

3.  選擇 **Add and configure**。

> ![](./media/image40.png)

4.  設置以下參數，用於**描述工具以及何時使用該工具**。

[TABLE]

> ![](./media/image41.png)
>
> **注意：**此描述告訴代理何時調用此工具。請注意描述中使用了“strict
> rule”。這為何時使用此工具提供了額外的限制，在本例中，僅當存在附件且對話上下文為簡歷上傳時才使用此工具。選擇何時可以使用此工具也很重要。由於我們正在構建一個多代理系統，並且有一個子代理，因此我們希望確保此工具僅在子代理中調用，而不是在主代理中調用。將該值設置為“only
> when referenced by topics or agents”即可確保這一點**。**

5.  向下滾動到輸入部分，選擇** Add Input **以添加以下輸入:

[TABLE]

> ![](./media/image42.png)

6.  現在我們需要設置輸入框的屬性。首先是 **contentBytes**
    輸入框，它將存儲實際的簡歷文件。在 **contentBytes**
    輸入框旁邊的“**Fill using** ”下拉菜單中選擇“**Custom
    value** ”。在“**Value**”屬性中，選擇**三個點 (...)**。

> ![](./media/image43.png)

7.  選擇“**Formula** ”選項卡。粘貼以下從聊天記錄中提取文件的公式，然後單擊“**Insert**”按鈕。

+++First(System.Activity.Attachments).Content+++

> ![](./media/image44.png)

8.  現在我們將配置**名稱**輸入框，它將存儲簡歷文件的名稱。該名稱也將是硬編碼的，因此請在“**Fill
    using** ”列中選擇“**Custom value** ”選項。

9.  選擇“**Value**”列中的**三個點（...），**粘貼以下公式，該公式可從聊天記錄中提取文件名，然後單擊“**Insert** ”按鈕。

+++First(System.Activity.Attachments).Name+++

> ![](./media/image45.png)

10. 現在我們來配置“**Message** ”輸入框。我們希望使用人工智能動態填充此輸入框，因此我們將保持默認設置。選擇“**Value**”列中的“**Customize** ”按鈕，以便填寫更多詳細信息，說明如何填充此輸入框。

![](./media/image46.png)

11. 請在 **Description** 字段輸入以下內容。然後選擇 **Advanced**。

**根據上下文提取求職信格式的信息。務必不要提示用戶，並根據現有上下文創建至少一份簡潔的求職信。嚴格規定：信息長度必須少於
2000 個字符。**

**注意**

填寫動態輸入的描述是確保代理正確填寫輸入的關鍵步驟。

> ![](./media/image47.png)

12. 展開“**Advanced**”部分，配置此輸入的其他屬性。在“**How many
    reprompts**”部分，選擇“**Don't repeat**”。

> ![](./media/image48.png)

**注意**

這個設置幫助你定制用戶體驗，避免客服在無法識別所需數據時重複問同一個問題。

13. 向下滾動至“**No valid entity found** ”部分。在“**Action if no entity
    found**”下拉菜單中選擇“**Set variable to value** ”選項。在“**Default
    entity value** ”輸入框中輸入+++Resume upload+++ 。

> ![](./media/image49.png)
>
> **注意**
>
> 如果代理無法動態填充該消息輸入，該設置允許我們硬編碼備份值。

14. 我們將通過在“**Fill using**”列中選擇“**Custom
    value**”選項，並在“**Value**”列中選擇**三個點（...）**來填充
    **UserEmail** 輸入。

> ![](./media/image50.png)

15. 選擇“**System**”選項卡並搜索“**User**”。選擇“**User.Email** ”變量以獲取使用該代理的人員的電子郵件地址。

> ![](./media/image51.png)

16. 選擇 **Save**

> ![](./media/image52.png)

### 任務6 - 定義代理指令

在此任務中，您將定義應用接收代理的代理指令。

1.  選擇“**Agents**”選項卡，然後選擇“**Application Intake
    Agent**”，返回到“**Application Intake Agent**”界面。 

> ![](./media/image53.png)

2.  在**“Instructions**”欄中，粘貼以下清晰的指導，供您的子代理使用。

> You are tasked with managing incoming Resumes, Candidate information,
> and creating Job Applications.
>
> Only use tools if the step exactly matches the defined process.
> Otherwise, indicate you cannot help.
>
> Process for Resume Upload via Chat
>
> 1. Upload Resume
>
> - Trigger only if /System.Activity.Attachments contains exactly one
> new resume.
>
> - If more than one file, instruct the user to upload one at a time and
> stop.
>
> - Call /Upload Resume once. Never upload more than once for the same
> message.
>
> 2. Post-Upload
>
> - Always output the \[ResumeNumber\] (R#####).
>
> ![](./media/image54.png)

3.  如果指令中包含斜杠（/），選擇緊隨/後的文本並選擇已解析的名稱。為了，

    - System.Activity.Attachments（變量）

    - 上傳簡歷（工具）

> 注意：如果你點擊說明中的System.Acticvity.Attachements，會看到已解析的名稱。你可以選擇它。選擇後，如果已有文本的任何部分可用，請刪除。
>
> ![](./media/image55.png)
>
> ![](./media/image56.png)

4.  說明書現在應該是這樣的。

> ![](./media/image57.png)

5.  選擇 **Save。**

> ![](./media/image58.png)

### 任務7 - 測試你的應用接收代理

現在讓我們通過打電話給子代理並按照我們的指示確認代理是否正常工作。

1.  通過選擇**“Test**”來切換打開測試面板。

> ![](./media/image59.png)

2.  選擇附件圖標，選擇簡歷—— AVERY EXAMPLE pdf，點擊 **Open**。

> ![](./media/image60.png)

3.  輸入消息+++Process these resumes+++，然後點擊 **send**。

> ![](./media/image61.png)

4.  代理人隨後應發送類似如下的消息：**The resume for Avery Example has
    been successfully uploaded. The resume number is R1001**。

> ![](./media/image62.png)

5.  在 **Activity map** 中，您應該可以看到 **Application Intake Agent** 
    正在處理簡歷上傳。

> ![](./media/image63.png)

6.  如果應用尚未打開，請訪問
    +++make.powerapps.com+++。確保右上角的“環境選擇器”中已選擇 Dev One
    環境。選擇 **Apps** → Hiring Hub → 省略號（...）菜單 → **Play**。   
    ![](./media/image64.png)

**注意：**如果播放按鈕呈灰色，則表示您尚未發佈解決方案。請選擇“**Solutions** → **Publish
all customizations**”**。**

7.  在 Power Apps – Hiring Hub
    應用中，導航至“**Resumes**”，並檢查簡歷文件是否已上傳，以及求職信是否已正確設置。

> ![](./media/image65.png)

## 練習2：添加面試準備相關代理

現在，讓我們創建一個聯網代理用於面試準備，並將其添加到您現有的招聘代理中。

### 任務1：創建聯網面試代理

1.  在 Copilot Studio
    中，選擇左側導航欄中的“**Agents**”選項卡，然後選擇**+ Create blank
    agent**”旁邊的**下拉菜單**，並選擇“**Advanced create**”。

> ![](./media/image66.png)

2.  選擇 **Solution** 為“**Operative**”，然後選擇“**Confirm and
    create**”。

> ![](./media/image67.png)

3.  選擇 **Edit**，而不是細節。

> ![](./media/image68.png)

4.  請提供以下信息並選擇 **Save**。

    - **名稱**: +++Interview Agent+++

    - **描述**: +++Assists with the interview process.+++

> ![](./media/image69.png)

5.  選擇“說明”旁邊的“**Edit**”，輸入以下**說明**，然後選擇“**Save**”。

> You are the Interview Agent. You help interviewers and hiring managers
> prepare for interviews. You never contact candidates.
>
> Use Knowledge to help with interview preparation.
>
> The only valid identifiers are:
>
> - ResumeNumber (ppa_resumenumber)→ format R#####
>
> - CandidateNumber (ppa_candidatenumber)→ format C#####
>
> - ApplicationNumber (ppa_applicationnumber)→ format A#####
>
> - JobRoleNumber (ppa_jobrolenumber)→ format J#####
>
> Examples you handle
>
> - Give me a summary of ...
>
> - Help me prepare to interview candidates for the Power Platform
> Developer role
>
> - Create interview assistance for the candidates for Power Platform
> Developer
>
> - Give targeted questions for Candidate Alex Johnson focusing on the
> criteria for the Job Application
>
> How to work:
>
> You are expected to ask clarification questions if required
> information for queries is not provided
>
> - If asked for interview help without providing a job role, ask for it
>
> - If asking for interview questions, ask for the candidate and job
> role if not provided.
>
> General behavior
>
> - Do not invent or guess facts
>
> - Be concise, professional, and evidence-based
>
> - Map strengths and risks to the highest-weight criteria
>
> - If data is missing (e.g., no resume), state what is missing and ask
> for clarification
>
> - Never address or message a candidate
>
> ![](./media/image70.png)

6.  確保**關閉** **Web Search**。 

> ![](./media/image71.png)

### 任務2：配置數據訪問並發佈

在這個任務中，你需要配置數據訪問，然後發佈代理。

1.  1\. 在 **Knowledge** 部分，選擇 **+ Add knowledge**。

> ![](./media/image72.png)

2.  選擇 **Dataverse**  
    ![](./media/image73.png)

3.  在**搜索框**中，輸入+++ppa\_+++。這是你之前在實驗中導入的表格的前綴。

4.  **選擇**全部 5
    個表格（候選人、評估標準、職位申請、職位角色、簡歷）。選擇“**Add to
    agent**”**。**

> ![](./media/image74.png)

5.  選擇右上角的 **Settings** 按鈕

> ![](./media/image75.png)

6.  確保以下設置已配置。

    - **允許其他代理連接並使用此代理：**開啟

    - **運用常識：**關閉

    - **文件上傳：**關閉

    - **內容審核級別：**中等

> ![](./media/image76.png)
>
> ![](./media/image77.png)
>
> ![](./media/image78.png)

7.  選擇“**Save**”，然後選擇右上角的 **X** 關閉設置菜單。 

> ![](./media/image79.png)

8.  選擇 **Publish**。

> ![](./media/image80.png)

9.  在確認對話框中選擇 **Publish**，等待發佈完成。

![](./media/image81.png)

### 任務3：將面試準備代理與你的招聘代理連接起來

在此任務中，您將將面試準備代理與招聘代理連接，實現多代理協調。

1.  返回您的 **Hiring Agent** 頁面。選擇“**Agents** ”選項卡，然後選擇
    **+Add an agent**。

> ![](./media/image82.png)

2.  選擇 **Interview Agent**。

> ![](./media/image83.png)
>
> **注意**
>
> 如果面試代理顯示為灰色且無法選擇，那說明它沒有發佈。先回面試代理那裡發佈。

3.  將 **Description** 設置為，

> Assists with the interview process and provides information about
> Resumes, Candidates, Job Roles, and Evaluation Criteria.
>
> 請注意，已檢查與該代理的“Pass”對話記錄。這使得父代理能夠為連接的代理提供完整的上下文。
>
> 選擇 **Add and configure**。

![](./media/image84.png)

4.  請確保您同時看到 **Application Intake Agent** 和 **Interview
    Agent**。請注意，一位是子專員，另一位是關聯專員。

> ![](./media/image85.png)
>
> ![](./media/image86.png)

### 任務4：測試多智能體協作

1.  通過選擇“**Test**”來**切換**打開測試面板。

2.  **上傳**其中一個測試恢復，輸入以下描述，告訴父代理可以委派給連接代理的內容:

> 上傳這份簡歷，然後給我展示一些空缺職位，每個職位都描述了評估標準，然後用這些來匹配至少一個合適的職位，即使不是完全匹配。
>
> ![](./media/image87.png)

3.  注意招聘代理將上傳工作委託給兒童代理，然後讓面試代理根據其知識提供摘要和職位匹配。

> ![](./media/image88.png)

4.  嘗試用不同的方式詢問有關簡歷、職位描述和評估標準的問題。**例如:**

> +++Give me a summary of active resumes+++
>
> +++Summarize resume R1006+++
>
> +++Which active resumes are suitable for the Power Platform Developer
> role?+++

## 摘要

你成功地將單一的招聘代理轉變為一個複雜、多代理協同、具備專業能力的代理。

這是你在這個實驗室取得的成就。

**多智能體架構掌握**  
你現在明白了何時使用子代理，何時使用連接代理，以及如何設計可擴展的系統。

**應用接收子代理**  
你已經在招聘代理中添加了一個專門的子代理，負責處理簡歷、提取候選人數據並在Dataverse中存儲信息。

**面試準備相關代理**  
你已經為面試準備搭建了一個可重複使用的聯網代理，並成功將其連接到了你的招聘代理。

**代理通信**  
你已經見識過主客服如何與專業客服協調、共享上下文並協調複雜的工作流程。

**自治基礎**  
你們的增強版招聘系統現在已經準備好支持我們將在未來任務中添加的高級功能：自主觸發、內容審核和深度推理。
