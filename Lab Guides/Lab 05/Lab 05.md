# 實驗室 05 – 增強 Safe Travels 代理並實施多代理編排

## 目的

您在上一個實驗中使用 Copilot Studio 中提供的模板創建了一個名為 **Safe
Travels**
的代理。在本實驗中，您將瞭解如何增強該代理以滿足特定客戶的需求。

在此過程中，您將學習 Copilot Studio 中的代理流創建和多代理編排的概念。

## 練習 1 – 測試現有的 Safe Travels 代理

在本練習中，我們將測試 **Safe Travels**
代理，以瞭解當被問及差旅批准時，代理如何回答。

1.  從瀏覽器以 +++https://copilotstudio.microsoft.com+++ 打開 **Copilot
    Studio**。導航到 **Dev One** 環境並打開 **Safe Travels** 代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  選擇 **Test** 圖標以測試代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  在 Test 窗口中輸入 +++Need travel approval +++，然後單擊 **Enter**。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image3.png)

4.  您可以看到，代理使用通用指令集進行響應，以便獲得旅行批准。

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image4.png)

## 練習 2 – 使用公司特定的知識資產增強代理

在本練習中，我們將添加特定於 Contoso 的知識資產 - **Travel Policy** 。

1.  在代理的 概述 頁面中，向下滾動並選擇 **+ Add knowledge**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

2.  單擊 **select to browse** 選項。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

3.  從 **C：\Labfiles** 文件夾中，選擇 **Travel Policy.docx** 然後單擊
    **Open**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

4.  單擊 **Add** 以添加文件。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

    ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image9.png)

5.  確保已添加文件。請等待狀態從 **In progress** 更改為 **Ready**
    ，然後再繼續下一步。

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image10.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image11.png)

## 練習 3 – 在 Microsoft Teams 中創建團隊和頻道

在本練習中，我們將在 MS Teams
中創建一個團隊和一個頻道，差旅審批請求將發送到該團隊和頻道。

1.  打開 Microsoft Teams 並從左側窗格中選擇“**See all your
    teams**”選項。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

2.  選擇 **Create team** 以創建新團隊。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  將 團隊名稱 輸入為 +++**HR Team**+++，將 第一個渠道名稱 輸入為
    +++**Travel Approval Channel**+++，然後選擇 **Create**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  在 Add members to HR Team 對話框中選擇 **Skip**。

    ![A screenshot of a email AI-generated content may be
incorrect.](./media/image15.png)

現在，團隊和渠道創建已完成。

## 練習 4 – 創建代理流

在本練習中，我們將創建一個新的 AgentFlow 來將差旅請求發佈到 Teams 渠道

1.  從 左側窗格中選擇 **Flows**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  選擇 **New agent flow** 以創建新流程。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

3.  選擇 **Add a trigger**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

4.  在 **AI capabilities**下選擇 **When an agent calls the flow**。

    ![A screenshot of a web page AI-generated content may be
incorrect.](./media/image19.png)

5.  選擇 **+ Add an input**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

6.  選擇 **Number** 並將其命名為 +++**Employee ID**+++。然後選擇 **+ Add
    an input**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

7.  現在，選擇一個 **Text** input 並將其命名為 +++**Purpose**+++。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

8.  選擇 **Add an action** 在觸發器節點下方。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

9.  搜索 +++**Teams**+++，然後單擊 Teams作組下的 **See more**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

10. 選擇 **Post message in a chat or channel** 。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image26.png)

11. 選擇 **Sign in** 並使用 您的憑證 login。

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image27.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image28.png)

12. 選擇以下詳細信息

    發佈為 – 選擇 **User**

    Post in – 選擇 **Channel**

    團隊 – 選擇 **HR Team**

    Channel – 選擇 **Travel Approval Channel**

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image29.png)

13. 在 Message 字段中，輸入以下內容

    ```
    Travel Request from 
    Employee ID - <Employee ID>
    Purpose - <Purpose>
    ```

    將 **\<Employee ID\>** 和 **\<Purpose\>** 替換為動態內容變量 **Employee ID** 和 **Purpose**，如下面的屏幕截圖所示。

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image30.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image31.png)

14. Parameters 選項卡現在如下所示。

    ![](./media/image32.png)

15. 關閉 Parameters 選項卡。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

16. 在 Post message 節點後添加另一個action。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image34.png)

17. 在 **Skills** 下選擇 **Respond to the agent**。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image35.png)

18. 選擇 Add an output。將其命名為 +++**Output**+++，並將值輸入為
    +++**Request submitted**+++。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

19. 單擊 **Save draft** 以保存流。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

20. 保存流程後，選擇 **Publish**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

21. 確保流程已發佈。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

22. 單擊 代理流程的 **Overview** 選項卡。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

23. 選擇 **Edit，**然後在 **Details** 窗格中將流命名為 +++Request Travel
    Approval Flow+++。選擇 **Save** 。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

## 練習 5 – 將代理流程作為工具添加到代理

在本練習中，我們將創建代理流程添加到代理 Safe Travels
中，以便利用流程功能。

1.  從左側窗格中，選擇 **Agents**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

2.  選擇 **Safe Travels** 代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

3.  在 Overview 頁面中向下滾動，然後選擇 **Add tool**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

4.  選擇已創建的 **Request Travel Approval Flow**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

5.  選擇 **Add to agent**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

6.  添加後，該流將列在代理的 **Overview** 頁面的 **Tools** 部分下。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

## 練習 6 – 創建主題

在本練習中，我們將創建一個 Topic 以使用創建的差旅審批流程。

1.  從 頂部菜單中選擇 Topics。選擇 **+ Add a topic -\> Add from
    description with Copilot**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

2.  輸入以下詳細信息，然後選擇 **Create**。

    **Name** - +++Travel Approval+++

    **Create a topic to** - +++This topic should get the Employee ID
    (Number) and Purpose of travel (Text) details from the user and invoke
    the Tool "Request Travel Approval Flow"+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image49.png)

3.  **主題**將按如下方式創建。

    ![](./media/image50.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image51.png)

4.  查看是否實際調用了 Flow。在這種情況下，僅添加一個 Message
    節點，說明已調用流。在這種情況下，請刪除此類 Message
    節點，然後單擊向用戶請求 Purpose 的節點後的 Add a node 圖標。

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image52.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image53.png)

5.  選擇 **Add a tool** -\> **Request Travel Approval Flow**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  為流變量 **Employee ID** 添加變量 **EmployeeID。**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  同樣，添加 Purpose of travel 輸入。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  添加 **Send a message** 節點，並向其添加 Output
    Variable，如下面的屏幕截圖所示。

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image57.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image58.png)

9.  選擇 **Save**，然後選擇 **Publish** 以發佈代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image60.png)

10. 在 確認對話框中選擇 **Publish**。

    ![A close-up of a white background AI-generated content may be
incorrect.](./media/image61.png)

11. 選擇 測試 圖標，輸入 +++Travel Approval +++ 並從測試窗格發送。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

12. 通過向代理提供以下詳細信息進行交談

    員工 ID – +++1234+++

    旅行目的 - +++Client meeting for finalizing proposal of XYZ project+++

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image63.png)

13. 您將從代理處收到 **Request submitted** 消息。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image64.png)

14. 打開 Teams 頻道，您將看到那裡發佈的旅行批准的詳細信息。

    ![](./media/image65.png)

## 練習 7 – 創建 Leave Management 代理 

在本練習中，我們將構建一個休假管理代理，該代理可用於瞭解休假、員工的休假餘額等。

1.  在 Copilot Studio 主頁上，選擇 **Agents -\> + New agent**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

2.  選擇 **Skip to configure**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  在配置頁面中，輸入以下詳細信息，然後選擇 **Create**。

    - 名字 - +++Leave Manager Agent+++

    - 描述 - +++This agent is to track the leaves of all the employees,
      their leave balance and leave history to approve or reject any new
      leave requests.+++

    - 指示 - +++Track the leaves of employees. Track their leave
      balance. Apply/Reject leaves based on their balance.+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  創建代理後，在 概述 頁面中向下滾動，然後選擇 **Knowledge** 部分下的
    **Add knowledge**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  點擊 **select to browse**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  從 C：\Labfiles 中選擇文件 **Leave balance Tracker**，然後單擊
    **Open**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  選擇 **Add** 將跟蹤鏈接添加到代理。

    ![](./media/image72.png)

8.  文件已添加。請等待狀態為 Ready，然後再繼續下一步。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

9.  從主題選項卡中選擇 **+ Add a topic -\> Add from description with
    Copilot**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

10. 輸入以下詳細信息，然後單擊 **Create**。

    - 名字 - +++Leave Balance Checker+++

    - 創建主題以 - +++Get the Employee ID from the user and check and reply
    with the leave balance based on the tracker added as knowledge
    source+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image75.png)

11. 檢查主題是否具有用於獲取員工 ID 的節點，然後單擊
    **Save**。在這裡，我們有一個用於獲取 Employee ID 的節點和一個
    Message 節點，用於聲明正在檢索餘額。

    檢查主題一次，然後刪除除上述節點之外已創建的其他節點。

    然後 **Save** 主題。

    ![](./media/image76.png)

12. 發送消息 +++ Check Leave balance+++ 從 Test 窗格中。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image77.png)

13. 輸入 +++1234+++ 作為員工 ID。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image78.png)

14. 檢查代理的響應。這是從添加到代理的知識資產中檢索的。

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image79.png)

15. 選擇 Publish 並等待代理發佈。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 練習 8 - 在 Copilot Studio 中實施多代理編排

組織現在可以在 Copilot
Studio（預覽版）中構建多代理系統，而不是依賴單個代理來完成所有工作，或在孤島中管理斷開連接的代理，代理可以在其中相互委派任務。這包括使用
Microsoft 365 代理生成器、Microsoft Azure AI 代理服務和 Microsoft Fabric
構建的設備。這些代理現在可以協同工作以實現一個共同的目標：完成跨系統、團隊和工作流的複雜關鍵業務任務。

在本練習中，我們將把 Leave management 代理添加到 Safe Travels
代理中，該代理可用於在計劃旅行時瞭解休假。

1.  從 Copilot Studio 中選擇 **Safe Travels** 代理。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  我們將首先測試這個代理，看看它可以在 leaves 上提供什麼信息。在 Test
    窗格中，輸入 +++Check Leave balance+++ 並按 Enter。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

3.  您可以看到，代理會提供有關如何檢查休假餘額的一般信息。在執行此作時，它還引用了
    Travel Policy 文檔。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image83.png)

4.  從 頂部菜單中選擇 **Agents** 選項卡，然後選擇 **+ Add**。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

5.  在 **“Choose how do you want to extend your agent”** 下，選擇
    **“Copilot Studio**”。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

6.  從列表中，選擇 **Leave Manager
    Agent**。只有在發佈後才能添加它。如果它正在發佈過程中，請稍候。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

7.  選擇 **Add agent** 將此代理添加到 **Safe Travels**。

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image87.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image88.png)

8.  添加代理後等待幾分鐘，然後單擊 **Publish**。

    ![](./media/image89.png)

9.  發佈代理後再等待幾分鐘，然後在 **Safe Travels** 代理的 Test
    窗格中輸入 +++Check Leave balance+++。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

10. 您可以看到 **Leave Manager** 代理是自動訪問的，並且代理回答了
    **Leave Manager** 代理主題中的 **Enter Employee ID** 問題。

11. 將員工 ID 輸入為
    +++1234+++，您可以看到座席根據休假管理器座席的知識資產進行回復。

    ![](./media/image91.png)

## 總結

在本實驗中，我們學習了如何增強從模板創建的代理以滿足個人需求。我們還學習了在
Copilot Studio 中實施多代理編排
