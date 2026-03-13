# 實驗室 - 構建具備知識接地和實時連接器的智能代理架構

**介紹**

現代用戶期望的回答是智能的、符合上下文的，超越簡單的關鍵詞匹配。本實驗室將引導您創建一個智能代理，能夠跨多個知識源推理並執行實時作，以提供全面、準確的答案。

**目標**

在這個實驗室裡，你將打造一個智能助手，超越簡單的問答，提供基於上下文的多部分回答。實驗結束時，你會明白的

利用對話創建體驗創建一個智能代理。配置座席語氣、行為和指令以體現你的品牌形象。加入像維基百科這樣的公共網站作為事實基礎的知識來源。關閉常識以減少幻覺並確保準確性。

## 任務1：創建一個新的代理並添加知識

利用 Copilot Studio
的對話式設置體驗，創建帶有自定義說明和維基百科知識集成的 Nova AI。

1.  打開瀏覽器，進入 +++copilotstudio.microsoft.com+++
    並用你的憑證登錄。

2.  選擇 **Dev One** 環境。

3.  在主頁中，選擇 **Create agent**。

![](./media/image1.png)

4.  創建代理後，選擇“**Detail**”旁邊的“**Edit**”。

![](./media/image2.png)

5.  輸入以下信息並選擇 **Save**。

    - 名稱 - +++Researcher agent+++.

    - 描述 - +++Answers multi-part questions by combining historical
      facts, biographical data, and real-time information like weather.
      Ideal for deep research, exploration, and knowledge synthesis+++

> ![](./media/image3.png)

6.  在“**Instructions**”下輸入以下內容，然後選擇“**Save**”。

你應該利用經過驗證的公開信息和實時查詢（如天氣或換算）來回答複雜的問題。你應該給出清晰簡潔的回答，並一次處理多個問題。您不得進行猜測、分享未經核實或敏感信息，或比較產品或公司。你應清晰且專業地溝通，適當時使用友好的語氣和輕微的表情符號。

![](./media/image4.png)

7.  向下滾動，選擇 **+ Add knowledge**以添加知識來源。

![](./media/image5.png)

8.  從列表中選擇**“Public Website**”選項。

![](./media/image6.png)

9.  在下一個屏幕中選擇“**Add**”，然後選擇“**Add to agent**”。

![](./media/image7.png)

![](./media/image8.png)

10. 接下來，你需要關閉常識以減少幻覺。從右上角選擇 **Settings** 。

![](./media/image9.png)

11. 將“Knowledge”部分下的“**Use general knowledge**”選項切換為 **off**
    狀態。

![](./media/image10.png)

12. 在測試面板輸入以下消息，點擊 **Send** ，觀察輸出。

> 寫一封草稿郵件，向一台壞掉的烤麵包機申請退款（麵包總是燒焦）

![](./media/image11.png)

![](./media/image12.png)

## 任務2：添加天氣連接器

在此任務中，您將添加一個天氣連接器，以實現實時數據檢索和生成式編排測試。確保代理只提供基於事實、受控的響應，同時能夠執行實時作，如天氣查詢，以獲得全面、多步驟的答案。

1.  從頂部菜單選擇**“Tools**”標簽。

![](./media/image13.png)

2.  在搜索框中輸入 +++MSN Weather+++，並選擇 **Get current weather**。

![](./media/image14.png)

3.  選擇“**Not connected**”消息旁邊的下拉菜單，然後選擇“**Create new
    connection**”。接著，在下一個屏幕中選擇“**Create**”。

![](./media/image15.png)

![](./media/image16.png)

4.  選擇 **Add and configure** ，將工具添加到代理中，並按需配置。

![](./media/image17.png)

5.  添加後，選擇 **“Additional details**”。

![](./media/image18.png)

6.  在“Credentials to use”中，選擇 **Maker-provided credentials**。

**注意：**
使用Maker提供的憑據時，代理的終端用戶不會被提示使用自身上下文和連接來連接服務。而是利用配置代理者的上下文和連接。-
僅在不需要用戶特定數據的作中使用作者認證，因為使用他人憑證可能會暴露數據外泄風險。-
在基於角色的訪問場景中使用用戶認證- 始終審查認證選擇的安全影響

![](./media/image19.png)

7.  在輸入、**Inputs**, **Units**, -\> **Fill using** -\>，選擇 **Custom
    value**，然後選擇**Metric**。

![](./media/image20.png)

8.  在“**Inputs**”下，對於“**Location**”，將“**Fill using to Dynamically
    fill with AI**”，然後選擇“**Customize**”來設置描述。

![](./media/image21.png)

9.  設置描述如下，然後選擇 **Save**。

天氣查詢地點。有效的輸入是城市、州、國家。在適當地點（例如美國）時，請始終包含城市和國家，州名應保留。

![](./media/image22.png)

![](./media/image23.png)

10. 用這個複雜的問題來測試你的增強型特工:

> GitHub
> 的母公司現任首席執行官是誰？他們是在哪裡獲得MBA學位的？那個校園附近一居室公寓的平均租金是多少？該地區今天的空氣質量指數是多少？

![](./media/image24.png)

11. 注意生成式編排如何執行多次搜索並觸發天氣連接器，從而提供全面的答案

![](./media/image25.png)

## 任務3：微調你的AI助手，使對話更順暢

定制系統主題以提升交互性，提供更流暢的用戶體驗。

在本部分，您將自定義內置系統主題，以改善用戶互動，打造超越知識源的更無縫體驗。

定制助理的歡迎信息使其更具吸引力，添加建議啟動提示以有效引導用戶，並完善如Escalate等系統主題，確保其符合組織需求。

1.  從頂部菜單中選擇 **“Topics**”。

![](./media/image26.png)

2.  在“**System**”下選擇“**Conversation Start**”主題。

![](./media/image27.png)

3.  在主題的 **消息** 節點中，輸入以下消息。

> 嘿，你好！我是研究員特工，你們的深度研究與發現智能助手。我能拆解複雜的問題，結合歷史事實、傳記和實時數據（如天氣）的見解。你今天好奇什麼？
>
> ![](./media/image28.png)

4.  仍在同一節點中，選擇 **+ Add** -\> **Quick reply**。

![](./media/image29.png)

5.  請補充以下問題。

+++What caused the fall of the Roman Empire?+++

![](./media/image30.png)

6.  同樣地，再加兩個。

> +++Who is the current CEO of the company that owns GitHub? Where did
> they earn their MBA? What's the average rent for a one-bedroom
> apartment near that campus? What's the air quality index in that area
> today?+++
>
> +++What's the temperature in the city that hosted the last Olympic
> Games?+++

![](./media/image31.png)

7.  添加後，選擇 **Save** 以保存主題。

![](./media/image32.png)

8.  定制升級體驗。選擇 **Topics** -\> **System** -\> **Escalate**。

![](./media/image33.png)

9.  將文字更新為以下內容，這樣更有意義地解除最終用戶的屏蔽，並選擇
    **Save**。

> 很抱歉，我似乎幫不上忙。我建議聯繫我們的\[Microsoft Copilot
> Studio社區\]（https://aka.ms/CopilotStudioCommunity
> 年）或提交\[支持請求\]
> (<https://learn.microsoft.com/en-us/power-platform/admin/get-help-support>).

![](./media/image34.png)

## 任務4：讓你的經紀人公開並發佈到演示網站

在本部分，你將移除認證，使代理對公眾開放，然後發佈到演示網站進行測試和共享。由於Researcher代理只提供一般信息，不處理私人數據，你需要關閉身份驗證以實現無縫的用戶體驗，並將認證發佈到演示網站收集反饋，然後再部署到真實網站。

1.  進入 **Settings** 。

![](./media/image35.png)

2.  選擇“**Security** -\> **Authentication**”。選擇“**No
    authentication**”，然後選擇“**Save**”。

![](./media/image36.png)

3.  在確認提示中**Save**保存。

![](./media/image37.png)

4.  你現在可以關閉設置面板了。

![](./media/image38.png)

5.  選擇 **Publish** 以使你的更改上線。

![](./media/image39.png)

6.  在確認對話框中選擇**Publish**。

![](./media/image40.png)

7.  發佈完成後，你會收到成功通知。

![](./media/image41.png)

8.  現在，從 頂部菜單選擇“**Channels**”。

![](./media/image42.png)

9.  從可用頻道列表中選擇**Demo website**。

![](./media/image43.png)

10. 輸入歡迎信息為 +++Welcome to your demo website+++，然後選擇
    **Save**。

![](./media/image44.png)

11. 點擊 **“Open demo website** ”即可打開您的網站。

![](./media/image45.png)

12. 你現在可以與你的代理人互動了。

![](./media/image46.png)

## 摘要

在這個實驗室裡，你們成功交付了一個面向公眾的智能代理，:

- 解答複雜且多部分的研究問題

- 使用經過驗證的公開知識和實時連接器

- 通過受控知識源減少幻覺

- 提供精緻且用戶友好的對話體驗

- 已部署並通過在線演示網站訪問

本實驗室演示如何設計、增強並發佈一款生產**準備的智能代理**，超越簡單的問答，提供可信、實時且具上下文感知的洞察。
