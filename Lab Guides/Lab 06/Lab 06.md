# ラボ6 - Hiring Agentを自律システムにアップグレードする

このラボでは、**イベントトリガー**についてさらに深く掘り下げ、エージェントシステムを**リアクティブ**から**自律的な動作**へと進化させます。エージェントを、人間の入力を待つ状態から、外部イベントにプロアクティブに反応し、監視なしにインテリジェントなアクションを実行する状態へと変革します。

質問に答えるだけのエージェントから、ニーズを予測し、自律的に行​​動するエージェントへとアップグレードすると考えてみてください。イベントトリガーと自動化されたワークフローを通じて、**Hiring
Agent**は履歴書の**メール**を受信し、添付ファイルを**自動的に処理し**、データを**Dataverseに保存し**、Microsoft
Teams経由で**人事採用チームに通知します**。そうして、より価値の高いタスクに集中できます。

**目的**

このラボでは、次の内容を学習します。

1.  イベントトリガーがユーザーの介入なしに、自律的なエージェントの動作を可能にする仕組み

2.  Copilot Studio
    における、インタラクティブエージェントと自律エージェントの違い

3.  メールの添付ファイルを自動的に処理し、ファイルを Dataverse
    にアップロードするイベントトリガーを作成する方法

4.  通知用にアダプティブカードをTeamsチャネルに投稿するエージェントフローを構築する方法

5.  エンド・ツー・エンドの自動化のためにイベントトリガーとエージェントフロー間でデータを渡す方法

**イベントトリガーとは何ですか。**

**イベントトリガー**別のシステムで何かが発生した際に、エージェントが自動でアクションを実行します。ユーザーからのメッセージは必要ありません。「new
SharePoint item」、「new email」、「Planner task
assigned」、あるいは時間ベースの繰り返しなど、設定されたイベントが発生すると、コネクタからエージェントにトリガーペイロードが送信されます。エージェントはユーザーの指示に従い、どのアクションまたはトピックを呼び出すかを決定します。　

**対話型エージェントと自律型エージェントの比較**

イベント トリガーとトピック
トリガーの違いがわかったので、次に、インタラクティブ
エージェントと自律エージェントの違いについて学習しましょう。

Copilot Studio
の用語では、「インタラクティブ」とは、主にチャットやチャンネルの**トピック**を介してやり取りするエージェントを指します。「自律型」とは、**イベントトリガー**も活用してユーザー入力なしで実行するエージェントを指します。

## 演習1: 応募者への応募メールの自動化

次に、**Hiring Agent**にイベント トリガーを追加し、子の**Application
Intake Agent**にエージェント
フローを構築して、自律性のためのさらなる処理を実行します。

**ユースケースシナリオ**

人事採用担当者**として**、履歴書が添付されたメールが受信トレイに届き、それが自動的にDataverseにアップロードされた際に通知を**受け取りたいです**。そうすることで、メールで送られてきた、応募書類が自動的にDataverseにアップロードされたことを常に把握できます。この目的は、2つの手法を用いて実現します。

1.  メールが届いた時のイベントトリガー

    - ファイルの contentType が形式タイプとして PDF
      に等しいことを確認します。

    - ファイルを抽出し、Dataverse コネクタ経由のアクションを使用して
      Dataverse にアップロードします。

    - 次に、Dataverse
      アクションから入力パラメータを渡して、エージェントにプロンプ​​トを送信し、さらに処理を進めます。

&nbsp;

1.  イベントトリガーのプロンプトによって呼び出される、子の**Application
    Intake Agent**にエージェント フローが追加されます。

    - Microsoft Teams
      のチャネルに投稿されたアダプティブカード内のイベントトリガーのプロンプトから渡された入力パラメータを使用して、人事採用チームに通知します。アダプティブカードには、**Hiring
      Agent**で確認できるデータバース行へのリンクが含まれます。

### タスク1: 電子メールで受信した履歴書をDataverseにアップロードする自動化

1.  Hiring
    Agentで、「**Overview**」**タブ**の「**Triggers** 」セクションまで下にスクロールし、「**+
    Add trigger**」を選択します。

> ![](./media/image1.png)

2.  トリガーのリストが表示されます。「**When a new email arrives
    (V3)** 」を選択し、「**Next**」を選択します。

> ![](./media/image2.png)

3.  次の画面で「**Continue**」を選択します。

![](./media/image3.png)

4.  **トリガー名**と、リストされているアプリの**Sign
    in** 接続参照が表示されます。トリガー名を以下のように変更します。

+++When a new email arrives from an applicant+++

> **注記：**リストされているアプリの各接続参照に緑色のチェックマークが付いていることを確認してください。緑色のチェックマークが表示されていない場合は、省略記号
> (...) からサインインし、「**+ New connection
> reference** 」を選択して新しい接続参照を作成してください。
>
> ![](./media/image4.png)

5.  最後のステップは、トリガーの入力プロパティを設定することです。以下のプロパティを以下のように更新します。

[TABLE]

6.  トリガーの作成を選択します。

> ![](./media/image5.png)

7.  作成が完了すると、トリガーがエージェントに追加されたことを示す確認メッセージが表示されます。「**Close** 」を選択すると、トリガーが「**Triggers** 」セクションに表示されます。

> ![](./media/image6.png)

8.  イベントトリガーを更新して、自動化機能をさらに追加します。トリガーの横にある**省略記号（...）**を選択し、「**Edit
    in Power Automate**」を選択してください。

> ![](./media/image7.png)

9.  トリガーはPower
    Automateのメーカーポータルにフローとして読み込まれます。フローデザイナーが開き、そこでロジックやアクションを追加して自動化を強化できます。トリガーはフローの一番上に表示され、フローの最後のアクションとして「**Sends
    a prompt to the specified copilot for
    processing** 」が表示されます。

> ![](./media/image8.png)

10. 既定では、Power Automate の「**When a new email
    arrives** 」トリガーは、複数の電子メールが一度に到着した場合、複数の電子メールをまとめて処理し、バッチに対してフローを
    1 回だけ実行することがあります。

> フローがメールごとに個別に実行されるようにするには、\[When a new email
> arrives\] ノードを選択し、\[**Settings**\] を選択します。
>
> **トリガーの設定**で **Split On**
> 設定を有効にし、**Arrayドロップダウン**フィールドで
> **@triggerOutputs()?\['body/value'\]** を選択します。
>
> Split On をオンにして、配列フィールドを
> @triggerOutputs()?\['body/value'\]
> に設定すると、多くのメッセージが同時に到着した場合でも、フローはメッセージごとに個別に実行されます。
>
> ![](./media/image9.png)

11. 次に、添付ファイルのファイルタイプを確認するロジックを追加しましょう。.PDFファイルのみをアップロードし、画像はアップロードしません（メール署名などから取得される可能性があります）。トリガーの下にある+アイコンを選択し、「**Built
    in tools** 」セクションの「**Control** 」を選択します。

> ![](./media/image10.png)

12. **Condition** アクションを選択します。

> ![](./media/image11.png)

13. 次に、添付ファイルの種類が.PDFであるかどうかを確認する条件を設定します。左側の「**Choose
    a value** 」フィールドで、**稲妻アイコン**を選択します。

> ![](./media/image12.png)

14. **Search** フィールドに「+++content
    type+++」と入力し、トリガーから**Attachments
    Content-Type** パラメータを選択します。

> ![](./media/image13.png)

15. ここで少し立ち止まって考えてみましょう。おそらく、「**For
    each**」アクションが自動的に表示されたことに気づいたでしょう。

> ![](./media/image14.png)
>
> このアクションは、**Attachments
> Content-Type**パラメータが各添付ファイルに関連付けられているため、電子メール内の各添付ファイルをループすることを表します。
>
> 内部的には配列であるため、**Condition** アクションで **Attachments
> Content-Type** パラメータを選択すると、**For each**
> アクションが自動的に追加されます。

16. 次に、**Condition** ブロックの右側にあるもう1つの**Choose a
    value** フィールドに、+++application/pdf+++と入力します。　

これにより、各添付ファイルのファイル拡張子形式が .PDF
であることが確認されます。

> ![](./media/image15.png)

17. ここで、電子メールからファイルを抽出し、それを **Resume** Dataverse
    テーブルにアップロードするための True パスを構成します。

> **True**パスの下に新しいアクションを追加し、「html to
> text」を検索します。「**+++Html to
> text+++**」アクションを検索して選択します。
>
> **注記：**Power Automate の html to textアクションは、HTML
> 形式のコンテンツをプレーンテキストに変換するために使用されます。これは、HTML
> タグを含むデータ（メール、Web コンテンツ、API
> レスポンスなど）を受信し、書式設定やコードなしで読み取り可能なテキストのみを抽出したい場合に特に便利です。
>
> ![](./media/image16.png)

18. 次に、「**Create new**」を選択して、**Html to
    text** アクションの新しい接続参照を作成する必要があります。

> ![](./media/image17.png)

19. アクションの設定が完了しました。トリガーから**Body**パラメータを追加しましょう。「**Content** 」フィールドで、右側の**稲妻アイコン**または**fxアイコン**を選択します。

> ![](./media/image18.png)

20. \[**Dynamic content** \] タブで、 +++body+++ を検索し、**Body**
    パラメータを選択して、\[**Add**\] を選択します。

> ![](./media/image19.png)

21. このアクションの構成が完了したので、左向きの 2 つの山括弧 («)
    を選択してパネルを折りたたみ、アクションを終了しましょう。

> ![](./media/image20.png)

22. 「**Html to
    text** 」アクションの下にある「**+**」アイコンを選択して、アクションを追加するためのパネルを開き、新しいアクションを追加します。「**Dataverse
    add**」を検索し、「**Add a new row** 」アクションを選択します。

> ![](./media/image21.png)

23. プロパティパネルの左上隅に「+++ Add a new Resume row
    +++」という名前を貼り付けて、  
    アクションの名前を変更します。

**Table name** パラメータで、res を検索し、**Resumes**
テーブルを選択します。

> ![](./media/image22.png)

24. 次に**Resume Title** フィールドを選択し、右側の **fx
    アイコン**を選択します。

> ![](./media/image23.png)

25. \[**Function tab**\] タブで、item()
    関数を使用する次の式を入力します。

+++item()?\['name'\]+++

> 「**Add** 」を選択して、**Resume Title** パラメータに式を追加します。
>
> ![](./media/image24.png)

**item() 関数に関する注意:**

- 「**Apply to each** 」アクションを使用すると、Power Automate
  はコレクション (配列) 内の各要素を調べます。

- これは、**Apply to each**  (または **For each**)、**Select**、**Filter
  array**などのアクション内で最もよく使用されます。

26. さらに、いくつかのパラメータを設定する必要があるので、「**Show
    all**」を選択します。

> ![](./media/image25.png)

27. 「**Cover Letter** 」フィールドで、右側の
    **fxアイコン**を選択します。

> **Functionタブ**で次の式を入力します。
>
> +++if(greater(length(body('Html_to_text')), 2000),
> substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))+++
>
> この式は、HTML からテキストへのアクションからのテキストが 2000
> 文字より長いかどうかを確認し、長い場合は最初の 2000
> 文字のみを返し、そうでない場合は完全なテキストを返します。
>
> ![](./media/image26.png)

28. 式が**Cover Letter** フィールドに追加されます。

> ![](./media/image27.png)

29. \[**Source Email Address** \]
    フィールドでは、**稲妻アイコン**を選択し、メール
    アドレスの値が含まれるトリガーから \[**From** \]
    パラメータを選択します。

> ![](./media/image28.png)

30. 「**Upload
    Date** 」フィールドでは、右側の**fxアイコン**を選択します。「**Function**」タブで「+++utcNow()+++」と入力し、「**Add**」を選択します。

**注記： utcNow() 関数とは何ですか。**

- Power Automate の utcnow() 関数は、現在の日付と時刻をCoordinated
  Universal Time (UTC) で ISO 8601 形式で返します (例:
  2025-09-23T04:32:14Z)。

> ![](./media/image29.png)

31. これで、**Add a new Resume
    row** アクションの構成が完了したので、パネルを折りたたんで終了しましょう。

> ![](./media/image30.png)

32. 「**Add a new Resume
    row** 」アクションの下にある**+**アイコンを選択して、新しいアクションを追加します。すると、アクションを追加するためのパネルが開きます。+++
    **Dataverse Upload** +++を検索し、「**Upload a file or an
    image** 」アクションを選択します。　

> ![](./media/image31.png)

33. 名前として +++Upload Resume File+++
    を貼り付けて、アクションの名前を変更します。

> ![](./media/image32.png)

34. 次に、**Content name** フィールドを選択し
    (すでに「無題」メッセージがある場合は削除します)、右側の **fx
    アイコン**を選択します。

> 「**Function**」タブで、item()関数を使用する次の式を入力します。これにより、現在のアイテム（添付ファイル）のnameプロパティが取得されます。
>
> +++item()?\['name'\]+++
>
> ![](./media/image33.png)

35. **Table name** パラメータで、 +++resumes+++ を検索し、**Resumes**
    テーブルを選択します。

> ![](./media/image34.png)

36. 次に**Row ID**
    フィールドを選択し、右側の**稲妻アイコン**を選択します。

> +++ID+++ を検索し、**Add a new row**  Dataverse アクションから
> **Resume** パラメータを選択します。これには、PDF
> ファイルをアップロードする行の ID 値が含まれています。　
>
> ![](./media/image35.png)

37. **Column name** フィールドを選択し、**Resume
    PDF** オプションを選択します。

> ![](./media/image36.png)

38. \[**Content** \] フィールドを選択し、右側の **fx
    アイコン**を選択します。

> 「**Function**」タブで、item()
> 関数を使用する次の式を入力します。この式は、現在のアイテム（添付ファイル）の
> contentBytes プロパティを取得します。contentBytes
> は、ファイルまたは添付ファイルの生のバイナリデータ（Base64
> 文字列としてエンコードされたもの）を参照します。
>
> +++item()?\['contentBytes'\]+++
>
> ![](./media/image37.png)

39. このアクションの構成が完了したので、左向きの 2 つの山括弧 («)
    を選択してパネルを折りたたみ、アクションを終了しましょう。

> ![](./media/image38.png)

40. 次に、「**Sends a prompt to the specified copilot for
    processing**」を選択し、このアクションを条件の
    **True** パスの「**Upload Resume File** 」アクションの下にドラッグ
    アンド ドロップします。

> ![](./media/image39.png)

41. **Sends a prompt to the specified copilot for
    processing** を選択して設定します。

![](./media/image40.png)

42. **Body/message** フィールドで、フィールドの内容をすべて選択し、クリア/削除します。

> ![](./media/image41.png)

43. 次のテキストをコピーして**本文/メッセージ**
    フィールドに貼り付け、**RESUME ID PLACEHOLDER**
    を強調表示して、**稲妻**アイコンを選択します。

> Send \[ResumeId (text)\] = "RESUME ID PLACEHOLDER" and \[ResumeTitle
> (text_1)\] = "RESUME TITLE PLACEHOLDER" and \[ResumeNumber (text_2)\]=
> "RESUME NUMBER PLACEHOLDER" to the Tool "Notify Teams Applicant
> channel" in the child agent "Application Intake Agent"
>
> ![](./media/image42.png)

44. +++resume+++
    を検索し、作成された**Resume** 行のID値が含まれるため、**Add a new
    row** *Dataverse* アクションから **Resume**
    パラメーターを選択します。

> ![](./media/image43.png)

45. 「RESUME TITLE
    PLACEHOLDER」をハイライトします。右側の**稲妻アイコン**を選択します。

> +++title+++ を検索し、**Add a new row
> Dataverse**アクションから**Resume Title** 
> パラメーターを選択します。これには、作成されたResume行の履歴書のタイトル値が含まれます。
>
> ![](./media/image44.png)

46. 「RESUME NUMBER
    PLACEHOLDER」をハイライトします。右側の**稲妻アイコン**を選択します。

> +++resume number+++ を検索し、**Add a new row
> Dataverse** アクションから Resume Number
> パラメーターを選択します。これには、作成されたResume 行の Resume
> Number 値が含まれます。
>
> ![](./media/image45.png)

47. このアクションとエージェントフローの設定が完了しました。「**Save**」を選択してイベントトリガーフローを保存しましょう。

> ![](./media/image46.png)

48. ここで、エージェント
    フローの詳細を編集する必要があります。保存したら、\[**Back**る\]
    を選択します。

> ![](./media/image47.png)

49. **Details** セクションで「**Edit** 」を選択し、「**Plan** 」を「**Copilot
    Studio**」オプションに更新します。「**Save**」を選択します。

> ![](./media/image48.png)

50. Copilot
    Studioプランへの切り替えを確認するモーダルが表示されます。「**Confirm**」を選択してください。

> ![](./media/image49.png)

51. プランが**Copilot
    Studio**に更新されました。エージェントのイベントトリガーフローを公開する必要があるため、「**Edit** 」を選択してください。

> ![](./media/image50.png)

52. \[**Publish**\]を選択します。

> ![](./media/image51.png)
>
> イベント トリガー フローが公開されました。

![](./media/image52.png)

子の **Intake Application Agent** によって呼び出される新しいエージェント
フローの作成を進めましょう。

### タスク 2 - アダプティブ カードを使用して Teams チャネルに通知する

次に、子の**Intake Application
Agent**用の新しいエージェントフローを作成します。このフローは、イベントトリガーから渡された値を使用して、Teamsチャネルにアダプティブカードを投稿します。このアダプティブカードは、自動アップロードされたPDFについて人事採用チームに通知し、確認できるようにします。

#### タスク 2.1: Teams でチャネルを作成する

このタスクでは、このラボの後半で使用するTeamとChannelを MS Teams
に作成します。

1.  +++https://teams.microsoft.com+++ にログインしてください。

2.  \[**New items** \] ドロップダウンを選択し、\[**New team**\]
    を選択します。

![](./media/image53.png)

3.  以下の詳細を入力し、「Create」を選択します。

    - Team name - +++HR Team+++

    - First channel name - +++Applicants +++

> ![](./media/image54.png)

4.  次の画面で「Skip」を選択します。

![](./media/image55.png)

5.  これで、新しいTeamとChannelが作成されました。

![](./media/image56.png)

#### タスク2.2: エージェントフローを作成する

1.  Copilot Studioに戻り、**Hiring
    Agent**で**Agents** タブを選択し、**Application Intake
    Agent**を選択します。

![](./media/image57.png)

2.  \[**Tools** \] まで下にスクロールし、\[**+ Add**\] を選択します。

> ![](./media/image58.png)

3.  **Add tool** モーダルが表示されます。「**+ New
    tool**」を選択します。

> ![](./media/image59.png)

4.  **Agent flow**を選択します。

> ![](./media/image60.png)

5.  次に**agent flow designer**が読み込まれます。「**When an agent calls
    the flow** 」トリガーで、「+ **Add an input**」を選択します。

> ![](./media/image61.png)

6.  ユーザー入力の種類として**Text** を選択します。

> ![](./media/image62.png)

7.  入力テキスト フィールドに、入力パラメータ名として +++ResumeId+++
    と入力します。

> ![](./media/image63.png)

8.  以下のパラメータに対して同じ手順を繰り返します。

Text - +++ResumeTitle+++

Text - +++ResumeNumber+++

![](./media/image64.png)

![](./media/image65.png)

9.  次に、エージェントフローにアダプティブカードを追加します。次に、アダプティブカードをTeamsチャネルに投稿するアクションをエージェントフローに追加します。

トリガーの下の **+ アイコン**を選択します。

> ![](./media/image66.png)

10. +++**Microsoft Teams** **post** +++ を検索し、**Post card in a chat
    or channel**アクション を選択します。

> ![](./media/image67.png)

11. サインインしたユーザーアカウントでMicrosoft
    Teamsへの接続参照を作成する必要があります。「**Sign
    in**」を選択してください。

> ![](./media/image68.png)

12. ユーザー アカウントを選択し、\[**Allow access**\] を選択します。

> ![](./media/image69.png)

13. 次の入力パラメータに従って構成します。

[TABLE]

> ![](./media/image70.png)

14. 次に、**Adaptive Card**フィールドを設定します。**Adaptive
    Card**フィールドを選択してください。

> ![](./media/image71.png)

15. 以下のコードをコピーして、**Adaptive
    Card**フィールドに貼り付けます。

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

16. ここで、JSON
    ペイロード内の既存の値を、実際の値または動的コンテンツに置き換えます。

> まず、**selectAction**プロパティ内の**urlプロパティ**の**URL**を更新しましょう。このURLは、**Hiring
> Hub**モデル駆動型アプリの**Resumes**システムビューのURLに置き換えられます。これにより、採用担当者はアクションを選択し、モデル駆動型アプリのResumesシステムビューにリダイレクトされるようになります。
>
> **current URL**値を強調表示して削除します。　

![](./media/image73.png)

17. **Hiring
    Hub**モデル駆動型アプリで、左側のメニューから**Resumes** システムビューに移動し、URLをコピーします。その後、**エージェントフロー**に戻り、**コピーしたURL**をselectActionプロパティ内の**url**プロパティに貼り付けます。

> ![](./media/image74.png)

18. 次のように、黄色で強調表示されている部分が **Hiring Hub**
    モデル駆動型アプリの環境の詳細になります。

[TABLE]

> ![](./media/image75.png)

19. 次に、いくつかのプロパティに動的なコンテンツ値を追加します。まずは、イベントトリガーによって、自動的に作成された行のResume
    Number参照を表示するテキストから始めましょう。

**パネル** アイコンを選択してアクション パネルを読み込みます。

![](./media/image76.png)

20. 「RESUME NUMBER
    PLACEHOLDER」というテキストプロパティがある行までスクロールダウンします。プレースホルダー値をハイライト表示して削除します。

![Delete placeholder](./media/image77.png)

21. 二重引用符の間をクリックし、右側の**稲妻アイコン**を選択します。

![](./media/image78.png)

22. **Dynamic Content** タブで、**ResumeNumber**
    パラメータを選択します。

> ![](./media/image79.png)

23. **ResumeNumber**
    パラメータが動的コンテンツとしてテキストプロパティに追加されます。

> ![](./media/image80.png)

24. 「RESUME NAME
    PLACEHOLDER」についても同じ手順を繰り返します。「RESUME NAME
    PLACEHOLDER」のテキストプロパティがある行までスクロールダウンします。プレースホルダーの値をハイライト表示して削除します。二重引用符の間をクリックし、右側にある**稲妻アイコン**を選択します。

> ![](./media/image81.png)

25. **Dynamic Content** タブで、**ResumeTitle** パラメータを選択します。

> ![](./media/image82.png)

26. **ResumeTitle** パラメータが動的コンテンツとしてテキスト
    プロパティに追加されます。

> ![](./media/image83.png)

27. 採用担当者が履歴書を確認する期限を表す「**Due
    Date** 」の値についても、同じ手順を繰り返します。2023年5月21日のテキストプロパティが表示されている行までスクロールします。　

![Select Allow access](./media/image84.png)

28. この日付プレースホルダー値を削除し、二重引用符の間をクリックして、右側から
    **fx アイコン**を選択します。

> ![](./media/image85.png)

29. \[**Function** \] タブで次の式を入力し、\[**Add**\] を選択します。

> +++addDays(utcNow(), 3, 'MMM dd, yyyy')+++

この式は 2 つの関数を利用します。

[TABLE]

utcNow
値の場合、日付を月と日、その後に年が続くようにフォーマットします。

> ![](./media/image86.png)

30. 式がテキストプロパティに追加されます。

![](./media/image87.png)

31. 最後に、JSONペイロードの下部にある**actions**配列プロパティ内の**urlプロパティ**の**URL**を更新します。この現在のプレースホルダーURLは、**Hiring
    Hub**モデル駆動型アプリの**Resume**行のURLに置き換えられます。これにより、採用担当者はアダプティブカードの**Action.OpenURL**アクションを選択し、モデル駆動型アプリの**Resume**にアクセスできるようになります。

> ![](./media/image88.png)

32. **Hiring
    Hub**モデル駆動型アプリの左側メニューを使用して、「**Resumes** 」システムビューの行を開きます。履歴書の行は、モデル駆動型アプリにフォームとして読み込まれます。　

Resume行の URL をコピーします。

![](./media/image89.png)

> ![](./media/image90.png)

33. 次に、エージェントフローに戻り、現在のプレースホルダー URL
    値を強調表示して削除します。

> ![](./media/image91.png)

34. 次に、**コピーした URL** を の **url**
    プロパティ内に**貼り付けます**。

> ![](./media/image92.png)

35. 以下のように表示されるはずです。末尾のGUID
    id値を削除してください。この動的なコンテンツ、つまり**ResumeId**パラメータを置き換えます。

![](./media/image93.png)

36. 右側から**稲妻アイコン**を選択します。

**Dynamic Content** タブで、**ResumeId** パラメータを選択します。

> ![](./media/image94.png)

37. **ResumeId**は動的コンテンツとして追加されます。黄色でハイライトされている部分は、**Hiring
    Hub**モデル駆動型アプリの環境詳細です。

[TABLE]

> ![](./media/image95.png)

38. **Post card in a chat or
    channel** アクションでのポストの構成が完了しました 👏🏻 **x**
    アイコンを選択して、アクション構成パネルを終了します。

> ![](./media/image96.png)

39. 最後に、処理を終了するためにエージェントに、テキストを返信して**エージェントに応答する**最後のアクションを設定します。

**Respond to the agent** アクションで、**+Add an output**を選択します。

> ![](./media/image97.png)

40. 出力の種類として**Text** を選択します。

> ![](./media/image98.png)

41. 以下の詳細を入力してください

    - Name - +++EndConversation+++

    - Value - +++ Finished+++

> ![](./media/image99.png)

42. エージェントフローの設定が完了しました。「**Save
    draft** 」を選択してエージェントフローを保存してください。保存すると確認メッセージが表示されます。

> ![](./media/image100.png)

43. エージェントフローを公開する前に、エージェントフローの詳細を更新する必要があります。「**Overview** 」タブを選択し、「**Edit**」を選択してください。

> ![](./media/image101.png)

44. Nameに+++Notify Teams Applicant
    channel+++と入力し、Descriptionの下の更新アイコンを選択して AI
    を使用して更新します。

![](./media/image102.png)

45. Descriptionが入力されたら、\[**Save** \] を選択して、エージェント
    フローの更新された詳細を保存します。

> ![](./media/image103.png)

46. 「**Designer** 」タブに戻り、「**Publish** 」を選択して、エージェント
    フローを公開します。

> ![](./media/image104.png)

47. 公開されると確認メッセージが表示されます。

> ![](./media/image105.png)

48. エージェントフローを**Application Intake
    Agent**のツールとして追加する必要があります。**Hiring**
    **Agent**に戻り、「**Agents** 」タブを選択して、**Application Intake
    Agent**を選択してください。　

![](./media/image106.png)

49. エージェントの**Details** セクションで、「**Description** 」フィールドを更新します。以下のテキストをコピーして、説明テキストの末尾に貼り付けます。

+++and also notifies the Teams Applicant channel+++

\[**Save**\]を選択します。

> ![](./media/image107.png)

50. 次に、エージェントフローをツールとして追加します。ツールセクションまで下にスクロールし、「**+
    Add**」を選択します。

> ![](./media/image108.png)

51. \[**Flow** \] タブを選択し、先ほど作成したエージェント
    フロー「**Notify Teams Applicant Channel**」を選択します。

> ![](./media/image109.png)

52. 次に「**Add and configure**」を選択します。

> ![](./media/image110.png)

53. 「**Inputs** 」セクションには、エージェントフローで先ほど設定した3つの入力が表示されています。デフォルトでは、「**Fill
    using** 」は「**Dynamically fill with
    AI**.」に設定されています。イベントトリガーからのプロンプトにはAIが抽出するパラメータ値が含まれるため、この設定はそのままにしておきます。

> ![](./media/image111.png)

54. ツールがApplication Intake
    Agentに追加されたので、エージェントの指示を更新する必要があります。**戻る矢印**を選択してください。

![](./media/image112.png)

55. **Hiring Agent**の**Agents** タブで、**Application Intake
    Agent**を選択します。

![](./media/image113.png)

56. 「**Instructions** 」フィールドの「**2.Post-Upload** 」の後に新しい行を入力します。以下の手順をコピーして貼り付けます。　

> Process for Resume Upload via Email
>
> 1. When you receive a message, \*\*Send \[ResumeId (text)\] =
> "1680265f-5793-f011-b41b-7c1e525be9f7" and \[ResumeTitle (text_1)\] =
> "TAYLOR TESTPERSON (FICTITIOUS).pdf" and \[ResumeNumber (text_2)\]=
> "R01026" to the Tool "Notify Teams Applicant channel"\*\* in the child
> agent "Application Intake Agent", call \[AGENT FLOW PLACEHOLDER\]
>
> ![](./media/image114.png)

57. \[AGENT FLOW PLACEHOLDER\] テキストを強調表示します。　

> ![](./media/image115.png)

58. スラッシュ文字 (/) を入力し、**Notify Teams Applicant
    Channel** を選択します。

> ![](./media/image116.png)

59. イベント トリガーの最後のアクション (**Sends a prompt to the
    specified copilot for processing**)
    によって、パラメータ値を含むプロンプトがエージェントに返された後、指示に従って**Application
    Intake Agent** によってエージェント
    フローが呼び出されるようになります。

**Application Intake
Agent** の更新された手順を保存するには、\[**Save** \] を選択します。

> ![](./media/image117.png)

60. エージェントが保存されると、手順が更新されます。

> ![](./media/image118.png)

61. 次に、Hiring
    Agentを**公開**する必要があります。右上の「**Publish** 」を選択し、表示される「**Publish
    this agent modal **」モーダルで「**Publish**」を選択します。

> ![](./media/image119.png)
>
> ![](./media/image120.png)

62. 公開されると、エージェントが公開されたことを示す確認メッセージが表示されます。

> ![](./media/image121.png)

これでエージェントをテストできます。

## 演習3: イベントトリガーのテスト

この演習では、このラボで作成されたイベント トリガーをテストします。

1.  イベントトリガーを実行するには、履歴書のPDFファイルを添付したメールを送信する必要があります。Outlookで新しいメールメッセージを作成してください。

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

2.  作成されたメールを、メールボックスから**送信します。**

> ![](./media/image122.png)

3.  イベントトリガーフローの +++https://make.powerautomate.com/+++
    で「更新」アイコンを選択すると、送信されたメールのフロー実行が成功していることがわかります。フローが成功したことを確認できます。

> ![](./media/image123.png)

4.  Copilot Studioに戻り、Hiring
    Agentの「**Activity**」タブを選択します。「**Activity**」タブが開き、**Hiring
    Agent**のすべてのアクティビティが表示されます。「名前」が「**Automated** 」で、ステータスが「**Complete**」のアクティビティがあります。このアクティビティは、イベントトリガーと呼び出されたエージェントフローを表しています。

> ![](./media/image124.png)

5.  アクティビティを選択し、アクティビティマップでイベントトリガーを選択します。右側のパネルで、プロンプトの入力パラメータに、作成された**Dataverse** 行のResume
    ID、Resume Title とResume
    Number のパラメータ値が含まれていることに注目してください。これは、**メールで受信した履歴書をデータバースに自動アップロードする**手順で設定した動的コンテンツの値です。

> ![](./media/image125.png)

6.  **Hiring Hub** モデル駆動型アプリに戻り、**Resumes system**
    ビューで「**Refresh** 」を選択してビューを更新します。メールで送信された履歴書に対応する新しく作成された行が、イベントトリガーによって作成されたものとして表示されます。

> ![](./media/image126.png)

7.  Copilot Studioに戻り、アクティビティマップの「**Application Intake
    Agent**」から「**Notify Teams Applicant
    Channel**」エージェントフローを選択します。右側のパネルで、入力にDataverse行の値が含まれていることに注目してください。これは、イベントトリガーの最後のアクション（**指定されたCopilotに処理のためにプロンプ​​トを送信する**）によって送信されたプロンプトからのもので、新しく作成されたDataverse行のパラメーター値が含まれています。このようにして、イベントトリガーからエージェントフローにパラメーター値を渡すことができます。

> ![](./media/image127.png)

8.  最後に、**Microsoft Teams**
    のチャネルに投稿されたアダプティブカードを見てみましょう。チャネルには、Dataverse
    に新しく作成されたResume行の情報を表示するアダプティブカードが表示されます。アダプティブカードの先頭にあるハイパーリンクにマウスポインターを合わせると、その
    URL が、先ほどアダプティブカードの JSON ペイロードで設定したResumes
    systemビューの URL であることがわかります。

> ![](./media/image128.png)

9.  ハイパーリンクを選択すると、ブラウザの **Hiring Hub**
    モデル駆動型アプリの**Hiring Hub** ビューに移動します。

> ![](./media/image129.png)

10. Microsoft Teams
    のチャネルに投稿されたアダプティブカードに戻ります。今度は、アダプティブカードの
    Action.OpenURL アクションである「**View
    Resume**」にマウスポインターを合わせます。URL
    が、先ほどアダプティブカードの JSON ペイロードで設定した Resumes
    行になっていることに注目してください。

> ![](./media/image130.png)

11. アクションを選択すると、ブラウザ上の **Hiring Hub**
    モデル駆動型アプリのResume行フォームに移動します。

> ![](./media/image131.png)

## まとめ

この研究室では、

1.  イベントトリガーを作成し、Dataverseのパラメーター値を、エージェントフローに渡すように設定しました。

2.  エージェントフローを構築しました。このフローは、Dataverseのパラメーター値を受け取り、Microsoft
    Teamsのチャネルにアダプティブカードを投稿して、人事採用チームに通知します。

3.  子エージェントの指示を更新し、イベントトリガーが完了したら、フローを呼び出すようにしました。

4.  これにより、**Hiring
    Agent** は、履歴書がメールの添付ファイルとして受信されるたびに自律的に動作し、人事採用チームに手動レビューを依頼する通知を送信できるようになります。
