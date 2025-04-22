# **ラボ 12\_ Copilot(classic) から Teams チャネルに　メッセージの送信**

**ラボ期間**– 30分

**目的:**

このラボでは、フローを呼び出してコパイロットからTeamsチャネルにメッセージを送信します。

## **手順 1: Microsoft Teams にチャネルとチームを追加する**

1.  VMからMicrosoft
    Teamsを開き、既に閉じている場合はテナントの資格情報を使用してログインします。Teamsオプションを選択します。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  Teamsから**More optionsを選択し、+ -\>** **Create
    team**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  チームを +++**HR Team**+++で チャネルを+++**HR
    Experts**+++として名前を付けて、**Create**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  ‘Add members to HR Team’ ウィンドウに**Skip**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  ‘Add members to the HR Experts
    channel’ウィンドウに**Skip**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

## **手順 2: HR エキスパートにエスカレーションして複雑なクエリを処理するトピックを強化する**

1.  From the Teams app, select the Teams アプリからCopilot Studio
    app(Power Virtual Agents)を選択して、**Copilots**タブを選択し**、HR
    Support Copilot**を開く。

> ![](./media/image6.png)
>
> **注:** Copilot Studio
> のショートカットが見つからない場合は、\[アプリ\] で **Copilot
> Studio/Power Virtual Agents** を検索し、**\[Open\]**
> を選択します**。**
>
> ![](./media/image7.png)

1.  左側のウィンドウから トピック を選択し、前に作成したトピック
    (**Employee time off**) に戻り、作成キャンバスに移動します。

> ![A screenshot of a chat Description automatically
> generated](./media/image8.png)

2.  \[**Ask a question**\] ノード**で、\[Extended leave\]
    という名前のオプションを追加します。**

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

3.  長期休暇の条件ノードの下に、問題の説明を求める質問ノードを追加し、「**+++How
    would you describe the issue?+++**」というテキストを追加します。

> ![](./media/image10.png)

4.  「Identify」の下で「**User's entire response**」を選択し、説明を
    +++**Description**+++ という名前の変数に保存します。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image11.png)

5.  **Save**を選択する

![A screenshot of a computer Description automatically
generated](./media/image12.png)

6.  質問の下にノードを追加し、「**Call an action**」を選択する。Teams の
    Copilot Studio 内で Power Automate を起動する「**Create a
    flow**」を選択する。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

7.  **Power Virtual Agents Flow** Templateオプションを選択する。

![](./media/image14.png)

![A screenshot of a computer Description automatically
generated](./media/image15.png)

8.  最初のステップでの「+Add an
    input」をクリックしてテキスト入力フィールドを追加する。入力をDescriptionに置き換える。

![A computer screen shot of a computer error Description automatically
generated](./media/image16.png)

9.  新しいステップを挿入し、**Add an action**を選択する。

![](./media/image17.png)

10. **Microsoft Teams** under **Choose an operation**の下に**Microsoft
    Teams**を選択する**。**

![](./media/image18.png)

11. **Post message in a chat or channel**を選択する。

![](./media/image19.png)

12. 以下の詳細を入力する:

- Post as – **User**

- Post in – **Channel**

- Team – **HR Team**

- Channel – **HR Experts**

- Message **– Description** from **Dynamic Content**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

13. フローを +++**Send a message to HR team**+++
    として改名し、**Save**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

14. \[Close\] をクリックして Power Automate
    を閉じてから、作成キャンバスに戻ります。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

15. 作成キャンバスからノードを追加する – **call an action** -\> **Send a
    message to HR team**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

16. 入力を**Description**として追加する

![A screenshot of a computer Description automatically
generated](./media/image24.png)

17. +++**We notified the expert. They’ll reach out
    shortly**+++とのメセッジがあるメセッジノードを追加する

![A screenshot of a computer Description automatically
generated](./media/image25.png)

18. 会話を終了する \> アンケートを終了する.

![A screenshot of a chat Description automatically
generated](./media/image26.png)

19. **Save**をクリックしてトピックを保存する。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

20. **Topic saved**の成功のメセッジが表示する。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

## **手順 3: チャットボットをテストする**

1.  左側ウィンドウからTest your chatbot を選択する![A screenshot of a
    computer Description automatically generated](./media/image29.png)

2.  Send a message +++**I need help with time
    off**+++のメセッジを送付し、Extended
    leaveを選択してチャットボットに回答する。![A screenshot of a chat
    Description automatically generated](./media/image30.png)

3.  休暇延長の理由を記入する。ここでは「+++I need extended leave of one
    month for travelling+++」と入力しました。

![A screenshot of a chat Description automatically
generated](./media/image31.png)

4.  ボットは「専門家に通知しました…」というメッセージで返信します。

![A screenshot of a chatbot Description automatically
generated](./media/image32.png)

> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)

## **手順 4: Teams でメッセージを確認します。**

1.  MS Teamアプリの左側メニューからTeamsをクリックする。

![](./media/image34.png)

2.  Teamsの**HR Teamの下にあるHR Experts** チャネルを選択する。team.
    ここで、ユーザーからボットへのメッセージが送信されていることに注意する。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

## **手順 5: Copilot – Teamsを公開する**

1.  Microsoft Copilot Studio アプリに戻り、チャットボット「**HR Support
    Copilot**」を選択します。

2.  左側ウィンドウからPublishを選択する。

![A screenshot of a chat Description automatically
generated](./media/image36.png)

3.  **Publish**をクリックする。

![](./media/image37.png)

4.  **Publish latest content?で**Publishを選択する。

![A close-up of a computer screen Description automatically
generated](./media/image38.png)

5.  以下のスクリーンショットのよう成功メセッジを受け取る。**Availability
    options**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  **Add to Contosoオプションによりボットを特定チームに追加します。**

7.  **Show to my team mates and shared usersによりボットが**Built by
    colleaguesセクションの下に表示される。

8.  **Show to everyone in the orgによりアドミンにボットをBuilt by
    orgセクションのしたにリストされる要求を提出します。**

![A screenshot of a computer Description automatically
generated](./media/image40.png)

**要約:**

このラボでは、ボットから Teams
チャネルにメッセージを投稿する方法を学習しました。
