# 實驗1：打造智能招聘人才招聘代理

在這個實驗室中，你將為招聘自動化系統奠定基礎。您將首先導入一個預配置的解決方案，其中包含管理候選人、職位和招聘工作流程所需的所有Dataverse表和數據結構。接下來，你將用樣本數據填充這些表格，支持本模塊的學習，並為測試提供真實情景。最後，你將在Copilot
Studio中創建招聘代理，建立基礎的對話界面，這將成為未來任務中所有其他功能的基石。

## 練習1：導入解法

在這個練習中，你將導入一個已有的解決方案。

1.  訪問 Copilot Studio 的 +++https://copilotstudio.microsoft.com+++

2.  選擇...... 在左側導航中選擇**Solutions。**

![](./media/image1.png)

3.  選擇“**Import
    solution**”。單擊“**Browse**”，選擇以“**Operative**”開頭的
    **C:\LabFiles** 壓縮文件，然後選擇“**Open**”。

![](./media/image2.png)

![](./media/image3.png)

![](./media/image4.png)

4.  選擇後，選擇“**Next**”，然後選擇“**Import**”。

![](./media/image5.png)

![](./media/image6.png)

5.  這大約需要 3 到 5
    分鐘。成功後，您將看到一個綠色通知欄，其中包含以下消息："Solution
    "Operative"已成功導入。”

![](./media/image7.png)

6.  看到"imported
    successfully"消息後，通過在解決方案列表中選擇解決方案的顯示名稱(**Operative**)來查看您導入的內容。

![](./media/image8.png)

7.  請審查解決方案，並確保以下組件已導入。

![](./media/image9.png)

8.  點擊頁面頂部的“Publish all customizations”按鈕。

![](./media/image10.png)

## 練習2 - 導入樣本數據

在這個練習中，你將向上一個練習中導入的一些表格添加樣本數據。

1.  從你在上一個練習中導入的解決方案中，選擇“**Hiring
    Hub** 模型驅動應用程序”，方法是選中該行前面的勾選標記，然後選擇頂部的“**Play**”按鈕。

> ![](./media/image11.png)

2.  在左側導航中選擇 **Job
    Roles** 。在命令欄中選擇“**More**”圖標（上下三個點），然後選擇“**Import
    from Excel**”旁邊的**右箭頭**。

![](./media/image12.png)

3.  選擇 **Import from CSV**。

![](./media/image13.png)

4.  選擇“**Choose File**”按鈕，從 **C:\LabFiles**
    中選擇**job-roles.csv**文件，然後選擇**Open**。

![](./media/image14.png)

5.  選擇“**Next**”。下一步保持默認設置，然後選擇“**Review Mapping**”。

![](./media/image15.png)

![](./media/image16.png)

6.  確保映射正確，然後選擇**“Finish Import**”。

![](./media/image17.png)

7.  選擇 **Done**。這可能需要一些時間，但你可以點擊
    **Refresh** 按鈕查看導入是否成功。

![](./media/image18.png)

![](./media/image19.png)

8.  現在，你將導入 **評估標準樣本數據**

9.  在左側導航中選擇**Evaluation Criteria**。

10. 像之前一樣選擇“**Import from CSV**”。選擇“**Choose File** ”按鈕，從
    **C:\LabFiles** 中選擇 **evaluation-criteria.csv** 文件。

![](./media/image20.png)

11. 選擇 **Next**。保持下一步不變，選擇“**Review Mapping**”。

![](./media/image21.png)

![](./media/image22.png)

12. 現在我們需要對映射關係進行一些補充工作。選擇“**Job
    Role**”字段旁邊的**放大鏡圖標。**

![](./media/image23.png)

13. 確保這裡選中了**Job Title**，如果沒有，添加並選擇**OK**。

![](./media/image24.png)

14. 確保其餘映射也正確，然後選擇“**Finish Import**”，再選擇“**Done**”。

![](./media/image25.png)

15. 這可能需要一些時間，但你可以點擊 **Refresh **按鈕查看導入是否成功。

![](./media/image26.png)

## 練習 3 - 創建招聘代理

既然你已經完成了先修課程的設置，就該開始真正的工作了！我們先加入招聘代理吧！

1.  在Copilot Studio中，從左側面板選擇特工。選擇 + Create blank
    agent旁邊的下拉菜單，選擇高級創建。

![](./media/image27.png)

2.  在代理設置中，選擇 Solution 作為**Operative**，然後選擇 **Confirm
    and create**。

![](./media/image28.png)

3.  在已創建代理的詳細信息中選擇“**Edit**”。

![](./media/image29.png)

4.  輸入名稱 +++**Hiring Agent**+++和描述 +++**Central orchestrator for
    all hiring activities**+++並選擇**Save**。

> ![](./media/image30.png)

## 摘要

> 在這個實驗室裡，你現在需要完成以下任務。

- **情景理解**: 全面瞭解招聘自動化挑戰及您將構建的解決方案。

- **解決方案部署**: 成功導入並配置了招聘管理系統的構建模塊。

- **代理創建**:
  構建了一個招聘代理，作為你作為特工學院特工將要構建的場景的起點
