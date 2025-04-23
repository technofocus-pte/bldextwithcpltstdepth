# **實驗 12\_ 將消息從 Copilot（經典）發送到 Teams 頻道**

**實驗室持續時間** – 30 分鐘

**目的：**

在本實驗中，我們將通過調用流將消息從 Copilot 發送到 Teams 頻道。

## **練習 1：在 Microsoft Teams 中添加頻道和團隊**

1.  從 VM 打開 **Microsoft
    Teams**，並使用租戶憑據登錄（如果已關閉）。選擇 **Teams** 選項。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  從 Teams 中，選擇 **More options** ，然後選擇 **+ -\> Create team**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  將團隊命名為 +++**HR Team**+++，將頻道命名為 +++**HR
    Experts**+++，然後選擇 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  在“Add members to HR Team”窗口中選擇 **Skip**。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  在“Add members to the HR Experts channel”窗口中選擇 **Skip**。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

## **練習 2：通過升級到 HR 專家來增強主題以處理複雜查詢**

1.  在 Teams 應用中，選擇 Copilot Studio 應用（Power Virtual
    Agents），選擇 **Copilots** 選項卡並打開 **HR Support Copilot**。

> ![](./media/image6.png)
>
> **注意：**如果未找到 Copilot Studio 快捷方式，請在“應用程序”下搜索
> **Copilot Studio/Power Virtual Agents**，然後選擇 **Open**）
>
> ![](./media/image7.png)

2.  從左側窗格中選擇 **Topics** ，然後返回到您之前創建的主題 **(Employee
    time off)** 並轉到創作區域。

> ![A screenshot of a chat Description automatically
> generated](./media/image8.png)

3.  在 **Ask a question** 節點中，添加名為 **Extended leave** 的選項。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  在 Extended leave 的 Condition
    節點下，添加一個問題節點，要求提供問題的描述，並添加文本 +++**How
    would you would describe the issue？***+++*

> ![](./media/image10.png)

5.  在 Identity 下選擇 **User's entire response，**並將描述保存在名為
    +++**Description**+++ 的變量中。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image11.png)

6.  選擇 **Save**。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  在問題下添加一個節點，然後選擇 **Call an action**。 選擇 **Create a
    flow**，以便在 Teams 的 Copilot Studio 中啟動 Power Automate。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

8.  選擇 **Power Virtual Agents Flow Template** 選項。

![](./media/image14.png)

![A screenshot of a computer Description automatically
generated](./media/image15.png)

9.  通過單擊第一步中的 **+ Add an input** 來添加 **Text** 輸入字段。將
    Input by **Description** 替換為 Input。

![A computer screen shot of a computer error Description automatically
generated](./media/image16.png)

10. 插入 **new step** ，然後選擇 **Add an action**。

![](./media/image17.png)

11. 在 **Choose an operation**下選擇 **Microsoft Teams**。

![](./media/image18.png)

12. 選擇 **Post message in a chat or channel**。

![](./media/image19.png)

13. 提供以下詳細信息:

- Post as – **User**

- Post in – **Channel**

- Team – **HR Team**

- Channel – **HR Experts**

- Message **– Description** from **Dynamic Content**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

14. 將流重命名為 +++**Send a message to HR team**+++，然後單擊
    **Save**。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

15. 單擊 **Close** 關閉 Power Automate 並返回到 Authoring （創作）
    畫布。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

16. 從 Authoring 畫布中，添加一個節點 – **call an action** \> **Send a
    message to HR team**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

17. 將輸入添加為 **Description**。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

18. 添加消息節點，其中包含消息 +++**We notify the expert。They’ll reach
    out shortly**+++。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

19. 結束對話 \> 結束調查。

![A screenshot of a chat Description automatically
generated](./media/image26.png)

20. 單擊 **Save** 以保存主題。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

21. 獲取 **Topic saved** 的成功消息。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

## **練習 3：測試您的 chatbot**

1.  從左側窗格中選擇 Test your chatbot。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

2.  發送消息 +++ **I need help with time off** +++，然後選擇 延長休假
    chatbot。

![A screenshot of a chat Description automatically
generated](./media/image30.png)

3.  描述您延長休假的原因。在這裡，我們給出了 +++ **I need extended leave
    of one month for travelling** +++。

![A screenshot of a chat Description automatically
generated](./media/image31.png)

4.  Bot 回復“We notified an expert.....”消息。

![A screenshot of a chatbot Description automatically
generated](./media/image32.png)

> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)

## **練習 4：在 Teams 中檢查消息。**

1.  單擊 MS Teams app 左側菜單中的 Teams。

![](./media/image34.png)

2.  選擇 **HR Team** 團隊下的 **HR Experts** 頻道
    。請注意，從用戶到機器人的消息已在此處發送。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

## **練習 5：發佈 Copilot – Teams**

1.  返回 Microsoft Copilot Studio 應用程序。選擇聊天機器人 **HR Support
    Copilot**。

2.  從左側窗格中選擇 Publish。

![A screenshot of a chat Description automatically
generated](./media/image36.png)

3.  單擊 **Publish**。

![](./media/image37.png)

4.  在 **Publish latest content？**中選擇發佈

![A close-up of a computer screen Description automatically
generated](./media/image38.png)

5.  獲得成功消息，如下面的屏幕截圖所示。單擊 **Availability options**。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  **Add to** **Contoso** 選項將機器人添加到特定團隊。

7.  **Show to my team mates and shared users** 使 bot 顯示在 Built by
    colleagues 部分下。

8.  **Show to everyone in the organization** 向管理員提交請求，以獲取
    **Built by org** 部分下列出的機器人。

![A screenshot of a computer Description automatically
generated](./media/image40.png)

**總結:**

在本實驗中，我們學習了從機器人向 Teams 渠道發佈消息。
