# ラボ 7 - Computer-Using Agents (CUA) を使用して、自律的な金融データ検索エージェントを構築する 

**紹介**

APIのないレガシーシステムは、自動化の大きな障害となります。従来のRPAは、脆弱なスクリーンスクレイピングや手作業による回避策に頼ることが多く、意思決定の遅延、エラーの増加、生産性の低下を招きます。このラボでは、よりスマートなソリューションとして、Microsoft
Copilot StudioとComputer Using Agents
(CUA)を紹介します。CUAは、人間と内部システムのインタラクションをシミュレートすることで、API統合を必要とせずに、安全にデータにアクセスし、処理することができます。より迅速な応答を提供し、手作業の負荷を軽減し、リアル・タイムで情報に基づいた意思決定を可能にする、自律型エージェントの構築方法を学びます。

目的

このラボでは、Microsoft Copilot Studio
を使用して、自律エージェントを構築する方法を学びます。このエージェントは、レガシー内部システムとの人間のやり取りをシミュレートし、直接
API アクセスを必要とせずに、金融ポートフォリオデータを取得します。

## タスク1: 自律エージェントの作成と構成

このタスクでは、Microsoft Copilot Studio
で新しい自律エージェントを作成し、その ID を構成し、Microsoft 365
Outlook コネクタを使用して電子メール トリガーを設定します。

ポートフォリオの検索を自動化するには、エージェントが受信メール要求を検出し、件名のフィルタリングに基づいて適切な自動化フローを開始できる必要があります。

1.  ログイン資格情報を使用して、+++https://copilotstudio.microsoft.com+++
    で Copilot Studio にログインします。

2.  右上から Dev One 環境を選択します。

![](./media/image1.png)

3.  **Create an agent**を選択します。

![](./media/image2.png)

4.  エージェントが作成されたら、**Details**に対して**Edit**を選択します。　

![](./media/image3.png)

5.  Nameに +++Portfolio Lookup Agent+++ と入力し、\[Save\]
    を選択して、エージェントのデフォルト名を変更します。

![](./media/image4.png)

6.  トリガーセクションまで下にスクロールし、「**+Add
    trigger**」をクリックします。

![](./media/image5.png)

7.  「**When a new email arrives (V3) (Office 365
    Outlook**」を検索して選択し、「**Next**」をクリックします。

![](./media/image6.png)

8.  トリガーの名前を +++ When a portfolio lookup email arrives +++
    に変更し、Copilot Studio と Outlook
    の接続が確立されていることを確認してから、\[**Next**\]
    をクリックします。

![](./media/image7.png)

9.  \[**Subject Filter (Optional)**\]
    フィールドで、件名に「+++Portfolio+++」と入力します。

![](./media/image8.png)

10. トリガーが作成されたら、「Time to test your
    trigger」ダイアログを**閉じる**ことができます。

![](./media/image9.png)

## タスク2: Computer Useツールを追加する

このタスクでは、コンピューターにログインし、ウェブサイトを閲覧し、金融ポートフォリオデータを検索・取得するComputer
Useツールを構成します。その後、Office 365 Outlook
コネクタを使用して、要求されたデータを返信します。　

1.  最上位メニューの「**Tools**」に移動します。　

![](./media/image10.png)

2.  **+ Add a tool**を選択します。

![](./media/image11.png)

3.  **+ New tool**を選択します。

![](./media/image12.png)

4.  「**Computer use (preview)**」を選択します。

![](./media/image13.png)

5.  以下の手順を追加し、「**Add and configure**」を選択します。

&nbsp;

1.  Go to
    <https://computerusedemos.blob.core.windows.net/web/Portfolio/index.html>.

2.  Enter the Portfolio ID in the "Enter Portfolio ID" search field and
    click on the "Search" button.

3.  Retrieve the "Client Name", "Portfolio Value" and "Manager" values
    exactly as shown.

4.  Return those three values as the final output. If no portfolio data
    is found, reply that you couldn't find a portfolio with the
    specified ID.

![](./media/image14.png)

6.  Computer useツールの**Name**を +++ Look up portfolio data +++
    に更新します。

7.  **Description**を「+++ Search and retrieve financial portfolio data
    +++」に更新します。

![](./media/image15.png)

8.  Inputsセクションで **+ Add input**を選択します。

![](./media/image16.png)

9.  Nameに「+++ Portfolio ID +++」、Descriptionに「+++ The ID of the
    portfolio +++」と入力し、「**Done**」を選択します。

![](./media/image17.png)

10. \[**Save**\]を選択します。

![](./media/image18.png)

## タスク3: Computer useツールをテストする

1.  「**Instructions**」セクションで、右側の「**Test**」ボタンを選択します。

![](./media/image19.png)

2.  Sample value +++44123BCD+++ を追加し、\[**Test now**\]
    を選択します。

![](./media/image20.png)

3.  Computer
    useツールがコンピュータにログインし、要求されたアクションを実行する様子を観察します。

    - 左側のパネルには、指示と、ツールの推論およびアクションのステップごとのログが表示されます。

    - 右側のパネルには、コンピューター使用用に設定した、マシン上のアクションのプレビューが表示されます。

![](./media/image21.png)

> ![](./media/image22.png)

![](./media/image23.png)

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

4.  \[**Finish testing**\]を選択します。

![](./media/image27.png)

## タスク4: 電子メール応答機能の設定

このタスクでは、電子メール機能を設定します。

1.  **Tools**タブに戻り、**+ Add a tool**を選択します。

![](./media/image28.png)

2.  +++ **Send an email (V2) (Office 365 Outlook)**+++
    を検索して選択します。

![](./media/image29.png)

3.  \[**Add and configure**\]を選択します。

![](./media/image30.png)

4.  **Name**を +++ Reply to email +++ に更新し、**Description**を +++
    Use this operation to reply to the email received +++
    に更新して、\[**Additional details**\] を選択します。

![](./media/image31.png)

5.  \[**Additional details**\] で、**Credentials to
    use**を**Maker-provided credentials**に設定します。

![](./media/image32.png)

6.  **Inputs**セクションで、**To**入力の**customize**をクリックし、**Description**を
    +++ Use the "from" email of the triggering received email +++
    に設定します。

![](./media/image33.png)

![](./media/image34.png)

7.  **Subject**入力欄を**カスタマイズし**、**Description**を「+++ Write
    the email subject +++」に設定します。

![](./media/image35.png)

8.  **Body**の入力をカスタマイズし、その**Description**を +++ Write the
    email body using HTML and highlight the requested data +++
    に設定します。

![](./media/image36.png)

9.  \[**Save**\] をクリックして、ツールの設定を完了します。

![](./media/image37.png)

10. 「**Overview**」タブに移動し、Instructionsを**編集**します。

![](./media/image38.png)

11. 次の指示を貼り付けます。

When a financial portfolio related request is received, identify the
Portfolio ID and search for the requested data using \< Look up
portfolio data \>. Once you have gathered the financial portfolio
information, use the \< Reply to email \> tool to reply to the original
email you received. Do not respond with data beyond what was requested.

![](./media/image39.png)

12. \< Look up portfolio data \> を選択し、/ を入力して、Look up
    portfolio dataツールを選択します。

![](./media/image40.png)

![](./media/image41.png)

13. 同様に、\< Reply to email \> を **Reply to
    email**ツールに置き換えます。

14. 置換が完了したら、下のスクリーンショットのように「**Save**」を選択します。

![](./media/image42.png)

15. 右上から「**Settings**」を選択します。

![](./media/image43.png)

16. **「Knowledge」**セクションにある**「Use general
    knowledge」オプションを無効にし、「Save」**を選択します。　

![](./media/image44.png)

17. **Settings**ペインを閉じます。

![](./media/image45.png)

## タスク5: 完成したエージェントのテスト

このエージェントでは、作成したエージェントの完全な動作をテストします。

1.  希望するメールアドレスからトレーニングユーザーのメールアカウントにテストメールを送信します。

件名: +++ Portfolio data request +++

体：

Hi!

I hope you're doing well!

I'm looking for the portfolio manager and value of portfolio \#44123BCD.
Much appreciated.

Thanks!

![](./media/image46.png)

2.  トレーニング
    ユーザーの受信トレイにメールが届いていることを確認してください。

3.  \[**Overview**\] タブで、\[**Triggers**\]
    セクションに移動し、\[**Test trigger**\] を選択します。

![](./media/image47.png)

4.  **トリガー インスタンス**を選択し、**Start testing**を選択します。

![](./media/image48.png)

5.  実行が行われた上、Testペインで更新とフローを確認できます。

![](./media/image49.png)

![](./media/image50.png)

6.  実行が完了したら、エージェントの返信をメールで確認してください。

![](./media/image51.png)

## まとめ

この演習では、Microsoft Copilot StudioとComputer-Using
Agents（CUA）を使用して、自律型の財務データ取得エージェントを構築しました。イベント駆動型のエージェントを構成し、メールによるリクエストに自動的に応答し、レガシーシステムとの人間による操作をシミュレートしてポートフォリオデータを取得し、APIに依存することなく正確な結果を返すようにしました。

以下のことを学びました:

- 直接的なユーザー操作なしで動作する自律エージェントを設計すること。

- メールベースのトリガーを使用して、自動化されたワークフローを開始すること。

- Computer-Using Agentsを構成して、レガシー
  ウェブアプリケーションを安全に移動して、  
  データを抽出すること。　

- 結果をメールで送信するための、アクションツールを統合すること。

- AI駆動型コンピュータインタラクションを使用して、脆弱なRPAパターンへの依存を軽減こと。

このラボでは、CUA を備えた自律エージェントが、レガシー
システムアクセスを最新化し、運用ワークフローを合理化し、API
が利用できない環境でより迅速で信頼性の高い意思決定を可能にする方法を示します。
