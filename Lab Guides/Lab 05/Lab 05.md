# ラボ 05 – Safe Travelsエージェントの強化と マルチエージェントオーケストレーションの実装

## 客観的

**「Safe Travels」**というエージェントを作成しました。このラボでは、この
エージェントを特定の顧客のニーズに合わせて拡張する方法を学びます。

その過程で、Copilot Studio でのエージェント フローの作成とマルチ
　　　　　　　　　　　　　エージェント・
オーケストレーションの概念を学習します。

## 演習1 – 既存のSafe Travelsエージェントをテストする

**Safe
Travels**エージェントをテストして、旅行の承認について尋ねられたときにどのように応答するかを確認します。

1.  ブラウザから +++https://copilotstudio.microsoft.com+++
    にある**Copilot 　　Studio**を開きます。Dev **One**環境に移動し、
    **Safe Travels**エージェントを　　　　　　　　開きます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  エージェントをテストするには、**Test**アイコンを選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  Testウィンドウに +++Need travel authorization+++ と入力し、
    **Enter**をクリックします。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image3.png)

4.  エージェントが、旅行の承認を得るために従うべき一般的な指示セットで
    応答していることがわかります。

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image4.png)

## 企業固有の知識資産でエージェントを強化する

Contoso に固有の知識資産「**Travel Policy」**を追加します。

1.  エージェントのOverviewページで下にスクロールし、 **「+ Add
    knowledge」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

2.  **select to browse**オプションをクリックします。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

3.  **C:\Labfiles**フォルダーから**Travel Policy.docx**を選択し、
    **\[Open\]**をクリック します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

4.  **「Add」**をクリックしてファイルを追加します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

    ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image9.png)

5.  ファイルが追加されていることを確認してください。ステータスが**「In
    progress」から「Ready」**に変わるまで待ってから、次のステップに進んで
    ください。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

## 演習3 – Microsoft Teamsでチームとチャネルを作成する

この演習では、出張承認リクエストを送信する MS Teams のチームとチャネルを
作成します。

1.  Microsoft Teams を開き、左側のペインから \[**See all your teams\]**
    オプションを選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

2.  新しいチームを作成するには、 **「Create team」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  チーム名に「+++ **HR Team** +++」、最初のチャネル名に「+++ **Travel
    Approval Channel** +++」と入力し、 **\[Create\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  HR チームにメンバーを追加するダイアログで**\[Skip\]**を選択します。

    ![A screenshot of a email AI-generated content may be
incorrect.](./media/image15.png)

これで、チームとチャネルの作成が完了しました。

## 演習4 – エージェント・フローを作成する

出張リクエストをTeamsチャネルに投稿するための新しいAgentFlowを作成します。

1.  左側のペインから**Flows**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  新しいフローを作成するには、 **\[New agent flow\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

3.  **Add a trigger**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

4.  **AI capabilities**で**When an agent calls the flow**を選択します。

    ![A screenshot of a web page AI-generated content may be
incorrect.](./media/image19.png)

5.  **+ Add an input**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

6.  **「Number」**を選択し、「+++ **Employee ID
    +++」**という名前を付けます。 次に、 **「+ Add an
    input」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

7.  次に、**Text**入力を選択し**、「+++ Purpose
    +++」**という名前を付けます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

8.  Triggerノードの下にある**\[Add an action\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

9.  +++ **Teams** +++ を検索し、 Teams のアクション グループの下にある
    **\[See more\]** をクリックします。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

10. **Post message in a chat or channel**を選択します。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image26.png)

11. **\[Sign in\]**を選択し、資格情報を使用して**ログインします。**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

12. 以下の詳細を選択してください

    Post as–**User**を選択
    
    Post in –**Channel**を選択
    
    Team – **HR Team**を選択
    
    Channel – **Travel Approval Channel**を選択

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image29.png)

13. メッセージ欄に次の内容を入力します

    ```
    Travel Request from 
    Employee ID - <Employee ID>
    Purpose - <Purpose>
    ```

    以下のスクリーンショットのように、 **\<Employee ID\>**と**\<Purpose\>**を動的 コンテンツ変数の**Employee ID**と**Purposeに**置き換えます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

14. Parametersタブは以下のようになります。

    ![](./media/image32.png)

15. Parametersタブを閉じます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

16. Post Message ノードの後に別の**action**を追加します。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image34.png)

17. **\[Skills\]**の下の**\[Respond to the agent\]**を選択します。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image35.png)

18. 「Add an
    output」を選択します。名前を「+++Output+++」とし、値を「+++Request
    submitted+++」と入力します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

19. フローを保存するには、 **「Save draft」**をクリックします。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

20. フローを保存したら、 **\[Publish\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

21. フローが公開されていることを確認します。

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image39.png)エージェント
    フローの**Overview**タブをクリックします。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

23. **「Edit」**を選択し、**Details**ペインでフローに「+++ Request
    Travel Approval Flow +++」という名前を付けます。
    **「Save」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

## 演習5 – エージェント・フローをツールとしてエージェントに 追加する

フロー機能を活用するために、エージェント Safe Travels
にエージェント作成　　　　フローを追加します。

1.  左側のペインから、 **\[Agents\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

2.  **Safe Travels**エージェントを選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

3.  Overviewページを下にスクロールし、**Add tool**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

4.  作成した**Request Travel Approval Flow**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

5.  **Add to agent**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

6.  追加されたフローは、**agent**の**OverviewページのTools**セクションに表示
    されます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

## 演習6 – トピックの作成

この演習では、作成した出張承認フローを使用するためのトピックを作成します。

1.  トップメニューから**「Topics」**を選択します。Copilot**で「+ Add a
    topic** -\> **Add from description with Copilot**」を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

2.  以下の詳細を入力し、 **「Create」**を選択します。

    **Name**- +++ Travel Approval +++
    
    **Create a topic to** - +++ This topic should get the Employee ID
    (Number) and Purpose of travel (Text) details from the user and invoke
    the Tool "Request Travel Approval Flow"+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

3.  **Topic**は以下のように作成されます。

    ![](./media/image50.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image51.png)

4.  フローが実際に呼び出されたかどうかを確認してください。この場合、
    フローが呼び出されたことを示すMessageノードのみが追加されます。その場合は、そのMessageノードを削除し、ユーザーに目的を尋ねたノードの
    後の「Add a node」アイコンをクリックしてください。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

5.  **Add a tool** -\> **Request Travel Approval Flow**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  フロー変数 **Employee ID** に変数**EmployeeID**を追加します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  同様に、Travel inputのPurposeの入力を追加します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  **Send a message**ノードを追加し、それに出力変数を追加します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  **「Save」**を選択し、
    **「Publish」**を選択してエージェントを公開します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image60.png)

10. 確認ダイアログボックスで**「Publish」**を選択します。

    ![A close-up of a white background AI-generated content may be
incorrect.](./media/image61.png)

11. Test アイコンを選択し、+++ Travel Approval
    +++と入力して、Testペインから送信します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

12. エージェントに以下の詳細を伝えて会話してください

    Employee ID – +++1234+++
    
    Purpose of travel - +++Client meeting for finalizing proposal of XYZ project+++

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image63.png)

13. エージェントから**Request submitted**メッセージが届きます。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image64.png)

14. Teams チャネルを開くと、出張承認についてそこに投稿された詳細が表示
    されます。

    ![](./media/image65.png)

## 演習7 – 休暇管理エージェントの作成

この演習では、休暇や従業員の休暇残高などを把握するために使用できる休暇管理エージェントを構築します。

1.  Copilot Studio のホームページから、 **\[Agents** -\> **+ New
    agent\]**を選択 します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

2.  **Skip to configure**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  設定ページで以下の詳細を入力し、 **「Create」**を選択します。

    - Name - +++Leave Manager Agent+++

    - Description - +++This agent is to track the leaves of all the
      employees, their leave balance and leave history to approve or
      reject any new leave requests.+++

    - Instructions - +++Track the leaves of employees. Track their leave
      balance. Apply/Reject leaves based on their balance.+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  エージェントが作成されたら、「Overview」ページを下にスクロールし、
    「**Knowledge**」セクション**「Add knowledge」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  **select to browse**をクリックします。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  C:\Labfiles から**Leave balance Tracker**ファイルを選択し、
    **\[Open\]**を クリックします。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  トラッカーをエージェントに追加するには、 **\[Add\]**を選択します。

    ![](./media/image72.png)

8.  ファイルが追加されました。ステータスが「準備完了」になるまで待って
    から、次のステップに進んでください。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

9.  「Topics」タブから、 **「+ Add a topic** -\> **Add from description
    with Copilot」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

10. 以下の詳細を入力し、 **「Create」**をクリックします。

    - Name - +++Leave Balance Checker+++
    
    - Create a topic to - +++Get the Employee ID from the user and check and
      reply with the leave balance based on the tracker added as knowledge
      source+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

11. トピックにEmployee
    IDを取得するためのノードがあるかどうかを確認し、**「Save」**をクリックします。ここでは、従業員IDを取得するためのノードと、残高が取得されていることを示すMessageノードがあります。

    トピックを一度確認し、上記のノード以外に作成された他のノードを削除 します。

    次にトピックを保存します。

![](./media/image76.png)

12. Test ペインから、メッセージを送信します +++ Check Leave balance +++
    。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image77.png)

13. Employee IDに「+++1234+++」と入力します。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image78.png)

14. エージェントからの応答を確認します。これは、エージェントに追加されたナレッジ・アセットから取得されます。

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image79.png)

15. 「Publish」を選択し、エージェントが公開されるまで待ちます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 演習8 - Copilot Studioでマルチエージェント・　　　　　　　オーケストレーションを実装する

単一のエージェントにすべてを依存したり、サイロ化されたエージェントを管理　したりするのではなく、Copilot
Studio（プレビュー）でマルチエージェント・　　　システムを構築し、エージェントが互いにタスクを委任できるようになりました。これには、Microsoft
365 エージェントビルダー、Microsoft Azure AI Agents
　　　　　　サービス、Microsoft Fabric
で構築されたシステムも含まれます。これらの　　　　　　　　　　　エージェントはすべて連携して、システム、チーム、ワークフローにまたがる複雑でビジネスクリティカルなタスクを完了するという共通の目標を達成できるようになります。

この演習では、旅行の計画時に休暇について学習するために使用できる休暇管理　エージェントを
Safe Travels エージェントに追加します。

1.  Copilot Studio から**Safe Travels**エージェントを選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  休暇に関してどのような情報を提供できるかをテストします。Testペインで「+++
    Check Leave balance +++」と入力し、Enterキーを押します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

3.  一般的な情報を提供していることがわかります。また、その際に出張
    ポリシー文書も参照しています。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image83.png)

4.  上部のメニューから**「Agents」**タブを選択し、 **「+
    Add」**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

5.  **\[Choose how do you want to extend your agent\]**の下で、
    **\[Copilot Studio\]**を 選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

6.  リストから**「Leave Manager
    Agent」**を選択してください。公開済みの場合のみ追加できます。公開中の場合はお待ちください。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

7.  このエージェントを**Safe Travels**に追加するには、 **\[Add
    agent\]**を選択 します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

8.  エージェントが追加された後、数分間待ってから**「Publish」**をクリック
    します。

    ![](./media/image89.png)

9.  エージェントが公開されてからさらに数分間待ってから、**Safe Travels
    agentのTest ペインに +++Check Leave balance+++** と入力します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

10. **Leave
    Manager**エージェントが自動的にアクセスされ、エージェントが**Leave
    Manager**エージェントのトピックから**Enter Employee
    ID**を入力という質問に返信していることがわかります。

11. Employee ID を +++1234+++ として入力すると、エージェントが Leave
    Manager エージェントのナレッジ アセットに基づいて返信していることが
    わかります。

    ![](./media/image91.png)

## まとめ

このラボでは、テンプレートから作成したエージェントを個々のニーズに
合わせて拡張する方法を学びました。また、Copilot
Studioでマルチエージェント
オーケストレーションを実装する方法も学びました。

