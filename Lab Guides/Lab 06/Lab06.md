# **實驗室06_Creating和從 Teams 部署 Microsoft Copilot Studio Copilot**

**實驗室持續時間** – 30 分鐘

**目的:**

在本實驗中，您將在 Microsoft Teams 中安裝 Copilot Studio
應用程序，在團隊中創建新的 Copilot 並對其進行測試。

## **練習 1： 在 Microsoft Teams 中安裝 Copilot Studio 應用程序**

1.  從 VM 中選擇 **Start** 菜單，搜索 +++teams+++，然後選擇 **Microsoft
    Teams apps** 。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  從 **Resources** 選項卡中使用您的憑證登錄。

![A screenshot of a sign in Description automatically
generated](./media/image2.png)

3.  點擊 **Apps**。搜索 +++**Copilot Studio**+++ 並選擇 **Microsoft
    Copilot Studio** ，然後單擊 **Add**。

**注意：** 如果您找不到 Copilot Studio，則必須搜索並選擇 **Power Virtual
agent** 並添加它。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![](./media/image4.png)

4.  點擊 **Open**。

![A screenshot of a phone Description automatically
generated](./media/image5.png)

5.  單擊 **Start now** 。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

## **練習 2：在團隊中創建新的 Copilot**

1.  使用 **Office 365 tenant credentials 登錄到** **Teams**。

> ![A screenshot of a sign in Description automatically
> generated](./media/image7.png)

2.  點擊 **Apps**。搜索 +++**Copilot Studio**+++ 並選擇 **Microsoft
    Copilot Studio** ，然後單擊 **Add**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![A screenshot of a phone Description automatically
generated](./media/image4.png)

**重要提示：** 如果您找不到 Copilot Studio，則必須搜索並選擇 +++**Power
Virtual agent**+++ 並添加它。

![A screenshot of a search engine Description automatically
generated](./media/image8.png)

![A screenshot of a computer Description automatically
generated](./media/image9.png)

3.  單擊 **Start now**。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  選擇 **Contoso** 並單擊 **Continue**。

![A screenshot of a chatbot Description automatically
generated](./media/image10.png)

![A screenshot of a chatbot Description automatically
generated](./media/image11.png)

**重要提示：** 此步驟可能需要大約 10
分鐘。如果花費的時間太長，請關閉它，從左側窗格中的應用程序中選擇 Copilot
Studio 或 Power Virtual Agents，然後重做步驟 4。

5.  在 Create a copilot 窗格中，將 Copilot 的名稱配置為 +++**HR Support
    Copilot**+++，然後單擊 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

6.  獲取一條成功消息，指出 **Your chatbot is provisioned**。

![](./media/image13.png)

## **練習 3：為常見的休假查詢構建員工休假主題**

1.  單擊 左側窗格中的 **Topics**。單擊 **+ New topic -\> From blank。**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  暫時 **Close** Trigger phrases 窗格。

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

3.  單擊 **Details** 圖標。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

4.  在 Details 窗格中，為常見的休假查詢提供 +++**Employee time off**+++
    （名稱） 和 +++**Employee time off topic for common time-off
    queries**+++（Description）。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

5.  **關閉** Details 窗格。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

6.  點擊 **Save**。

![A screenshot of a chat Description automatically
generated](./media/image19.png)

7.  單擊 **Trigger phases。**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

8.  添加觸發短語 +++ **I need help with time off** +++，然後單擊 **+。**

![](./media/image21.png)

9.  添加以下rigger phrases。

- +++**Need information on time off**+++

- +++**How many days of paid vacation do I have**+++

- +++**What are the national holidays**+++

- +++**I need extended leave**+++

![A screenshot of a computer Description automatically
generated](./media/image22.png)

關閉 Trigger phrases 窗格。

10. 添加 Message 節點並輸入文本 +++I can help with questions related to
    time-off+++.

> ![A screenshot of a chat Description automatically
> generated](./media/image23.png)

11. 作為 HR 員工，您知道最常見的休假問題是關於 **paid vacation** 時間和
    **national holidays**
    的。當添加具有用戶響應選項的問題節點時，主題會自動為每個響應獲取一個分叉分支。

12. 選擇消息節點下方的 （**+**） 圖標，然後選擇 **Ask a question**
    以將問題節點添加到主題。輸入 *What information are you looking
    for? *在 **Ask a question** 文本框中。

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)

13. 在 **Options for user** 下，添加 +++ Paid vacation+++ 和 +++
    National Holidays+++ 作為兩個選項。

> ![A screenshot of a questionnaire Description automatically
> generated](./media/image25.png)

14. 用戶選擇存儲在變量中，主題根據用戶選擇的選項進行分支。您可以重命名變量，以便在主題中更好地跟蹤它。

15. 在變量上，在 **Save response as** 下，選擇鉛筆圖標以編輯變量屬性。

16. **Variable** **properties** 窗格隨即打開。將變量重命名為
    +++TimeoffType+++。關閉 **Variable properties**
    窗格，您會看到創作區域中反映的更改。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

17. 為帶薪休假分支添加消息節點，並向用戶發送此消息: +++**For paid
    vacation time-off, go to www.contoso.com/HR/PaidTimeOff**+++ to
    submit time-off requests.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

18. 在 **National Holidays** 路徑中，添加包含以下文本的消息節點:

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

![](./media/image28.png)

19. 點擊 **Save**。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

![A screenshot of a chat window Description automatically
generated](./media/image30.png)

## **練習 4：測試 Copilot 的預期行為**

1.  選擇屏幕頂部的 **Copilot/Power Virtual Agent** 圖標以啟動測試
    Copilot 畫布。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

2.  在 copilot 聊天中鍵入 **I need time off information**。

3.  選擇 **Paid vacation**。

4.  您將根據我們的配置收到響應。

> ![A screenshot of a chat Description automatically
> generated](./media/image32.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)
>
> **總結：**
>
> 在此實驗室中，我們學習了將 Copilot Studio 應用程序添加到 Teams 並在
> Teams 中創建經典機器人。
