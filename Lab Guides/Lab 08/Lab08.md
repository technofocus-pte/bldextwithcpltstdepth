**實驗 08 - 為 Microsoft Copilot 創建對話actions**

**實驗室持續時間** – 20 分鐘

**目的**

Microsoft Copilot
提供開箱即用的體驗，以與整個組織的內容和資源互動。在某些情況下，需要回答並與外部系統交互。使用
Microsoft Copilot Studio，您可以創作可作為 Copilot
插件發佈的對話主題。在您的租戶管理員批准插件後，可以將其添加到您組織的
M365 聊天體驗中。

如果組織擁有相同的有效許可證，則這些作將在生產中的 Microsoft Copilot
中可用。

在本實驗中，我們將學習如何創建對話作。

## **練習 1：創建對話作**

1.  使用您的租戶憑據登錄到
    +++**https://copilotstudio.microsoft.com/**+++（如果尚未登錄）。

2.  從右上角選擇 **Dev one** 作為環境。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  從 左側窗格中選擇 **Agents**。

4.  選擇 **Copilot for Microsoft 365**。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

5.  選擇 **Actions**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

6.  選擇 **Add an action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

7.  在 **New action pane** 中選擇 **Conversational**。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

8.  將作的名稱設置為 !!**Conversational action**!!.選擇 **Create**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  準備就緒後，創建的作將在 Authoring canvas 中打開。選擇 **Topics**。

10. 如果它沒有打開，請刷新頁面並查看它是否列在 **Library** -\>
    **Conversation** 下。

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image7.png)

11. 打開 **Conversational action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

12. 將主題命名為 !!Holidaylist!!

![A screenshot of a computer Description automatically
generated](./media/image9.png)

13. 在 Trigger
    節點的描述中，明確描述對話插件如何幫助用戶以及它可以做什麼。讓本主題幫助用戶找到
    2025 年的假期列表。

鍵入 +++ **This plugin helps to retrieve the list of holidays for the
year 2025.**+++ 在 Trigger 節點的描述中。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

此描述具有功能用途，Microsoft Copilot 使用它來確定是否調用您的插件。

14. 添加包含假日列表的 message 節點。

2025 年國定假日:

- New Year’s Day: Jan 1

- Martin Luther King Jr. Day: Jan 20

- Washington’s Birthday (Presidents’ Day): Feb 17

- Memorial Day: May 26

- Juneteenth National Independence Day: June 19

- Independence Day: July 4

- Labor Day: Sep 1

- Columbus Day / Indigenous Peoples’ Day: Oct 13

- Veterans Day: Nov 11

- Thanksgiving Day: Nov 27

- Christmas Day: Dec 25

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

15. 單擊 **Save** 以保存插件。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

![A screenshot of a chat box Description automatically
generated](./media/image13.png)

## **練習 2：將聊天作發佈到 Microsoft Copilot**

1.  發佈對話插件會在 Dataverse
    註冊表中為您的租戶創建一個新插件。在那裡可用後，租戶管理員需要批准您的插件可供
    Microsoft Copilot 插件目錄中的用戶使用。

2.  單擊 **Publish**。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

3.  選擇 **Publish。**

![A screenshot of a computer program Description automatically
generated](./media/image15.png)

4.  在 **Publish latest content** 對話框中選擇 **Publish** 。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

5.  發佈狀態顯示在屏幕上。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

注意： 發佈應該會很快完成。Microsoft Admin Center
中的實際可用性最多可能需要 4 小時。

**重要提示： ：** 要讓管理員在管理中心列出它，公司必須持有有效的 Copilot
許可證。

6.  您的管理員可以 在 **Microsoft Admin Center** 的 設置 下找到
    **Dataverse and Microsoft Copilot Studio** 集成應用，然後選擇
    **Integrations to be reviewed and approved**。

7.  租戶管理員批准 Dataverse 和 Microsoft Copilot Studio
    集成應用後，它應顯示在其 Microsoft Copilot UI 的用戶插件列表中。

**總結：**

在本實驗中，我們學習了如何創建對話作並發佈它。
