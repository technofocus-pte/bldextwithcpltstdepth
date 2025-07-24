# Lab 07 – パーソナライズされたショッピング・　　　アシスタントを作成する

## 客観的

このラボの目的は、Contoso Electronics
向けにパーソナライズされたショッピング・エージェントを作成することです。エージェントのナレッジソースとして
Dataverse
テーブルを使用します。エージェントは、顧客の最新のショッピング履歴に基づいて　Product
Categoryを提案し、ショッピング体験全体を通してサポートします。

## 演習1 – Dataverseテーブルの作成

**顧客**、**製品**、**注文**の詳細を保存するためのテーブルをDataverseに作成します。

1.  管理者テナントの資格情報を使用して +++https://make.powerapps.com+++
    に ログインし、環境として Dev One
    を選択します。左のナビゲーションペイン から「Tables」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  **「+ New
    table」**の横にあるドロップダウンを選択し、その下の**「Create new
    tables」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  新しいテーブルを作成するには、**Import an Excel file or .csv**を選択
    します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Excel または .CSV ファイルのエクスポートの下で、**Select from
    device** オプションを選択します。

![A screenshot of a file AI-generated content may be
incorrect.](./media/image4.png)

5.  **C:\Labfiles**からExcelファイル「
    **Customers.xlsx」**を選択します。
    **「Import」**を選択してトラッカーからデータをインポートし、テーブルを作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  トラッカーからのデータを使用してテーブルが作成されます。

7.  ここで、そのテーブル名 は**Customer
    Record**。自動生成されるため、実際のテーブル名とは多少異なる場合があります。このテーブル名をメモし、ラボ実行中は適切なテーブル名を使用してください。

8.  テーブルをクリックし、 **「View
    data」**を選択して、テーブルに追加されたデータを表示します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  **\[Save and exit\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

10. 確認ダイアログで**「Save and exit」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. 2 から 10 までの手順を 2 回繰り返し、トラッカー**Product
    Catalog.xlsx**を使用して 1 回目、 **Orders.xls**を使用して 2
    回目にテーブルを作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

12. 3つのテーブルがあります。

    - 顧客記録

    - 製品記録

    - 注文

## 演習2 – ショッピング・エージェントを作成する

この演習では、Contoso Electronics
でのショッピング中に顧客を支援するショッピング
エージェントを作成します。

### タスク1 – エージェントを作成する

Copilot Studio で Copilot を使用してエージェントを作成します。Copilot
と　　　　チャットして、エージェントの設計方法や動作を指示すると、Copilot
が自動的に　　　エージェントを作成します。

1.  +++https://copilotstudio.microsoft.com/+++ で Copilot Studio
    にログインし、 **Dev One**環境を選択します。

![](./media/image12.png)

2.  **\[Agents\]**を選択し、 **\[+ New agent\]**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  チャットに以下を入力して送信してください。

+++Create an agent that will assist the customers in shopping with
Contoso Electronics. Name it as "Shopping agent".+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  +++ Help the users in finding products and their prices, give
    personalized suggestions and track order delivery+ ++
    と入力して**Enter** キーを押します。

![](./media/image15.png)

5.  以下のように追加の指示を入力してください。

+++ Maintain a polite tone +++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  **「Create」**をクリックして**ショッピング・エージェント**を作成します。

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image17.png)

7.  エージェントのセットアップが完了します。数分かかる場合があります。エージェントの準備が完了すると、以下のスクリーンショットのようにCopilot
    Studioに表示されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

### タスク2 – 知識を追加する

エージェントに知識を追加すると、エージェントはそれらの知識リソースに基盤を置くようになり、ユーザーのクエリにより効果的に回答できるようになります。このタスクでは、前の演習で作成したDataverseテーブルを知識ソースとしてこのエージェントに追加します。

1.  Test ペインに+++ What is the status of the order o 1001? + ++
    と入力します。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image19.png)

2.  エージェントにはこのことに関する情報がないため、応答は以下のものと同様になります。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image20.png)

3.  次に、エージェントにナレッジソースを追加します。エージェントの**Home**
    ページから、 **「Knowledge」**セクションの**「Add
    Knowledge」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

4.  利用可能なオプションのリストから**Dataverse を**選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

5.  ++++order+++ を検索し、 **Order
    Record**テーブルを選択して、**Next**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  **\[Add\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  ナレッジ ソースが追加された後、エージェントを再度テストする前に数分
    間待機します。

8.  「Knowledge」セクションで「**Order
    Record**」が「**Ready**」になったら、「Test」ペインで同じ質問をします。

エージェントがデータベースから情報を取得し、ユーザーに提供していることがわかります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

### タスク3 – エンティティの作成

1.  エージェントのホーム画面から**\[Settings\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

2.  左ペインから**Entities**を選択します。**Add an entity -\> + New
    entity**を選択します。

![](./media/image27.png)

3.  **Closed list**を選択します。

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image28.png)

4.  以下の詳細を入力してください。

Name - +++Laptop+++

Description - +++ Contains products under Laptop category +++

**\[List items\]**の下に+++Apple MacBook Air M3+++
と入力し、**\[Add\]**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

5.  同様に、以下の項目を追加し、 **「Save」**を選択します。

+++Dell XPS 13 Plus+++

+++HP Spectre x360 14+++

+++Lenovo ThinkPad X1 Carbon Gen 12+++

+++Asus ROG Zephyrus G14+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

6.  次に、以下のデータを使用して手順 2 ～ 5 を繰り返します。

Name - +++Desktop+++

Description - +++ Contains products under Desktop category +++

**\[List items\]**の下に+++Apple iMac+++ と入力し、
**\[Add\]**をクリックします。

7.  リストに追加されるその他の項目

+++ Microsoft Surface Studio 2+++

+++ HP Envy Desktop +++

+++ Dell Inspiron Desktop +++

+++ Lenovo IdeaCentre AIO 5i +++

8.  再度、以下のデータを使用して手順 2 ～ 5 を繰り返します。

Name - +++Tablet+++

Description - +++ Contains products under Tablet category +++

**\[List items\]**の下に+++Apple iPad Pro+++ と入力し、
**\[Add\]**をクリックします。

9.  リストに追加されるその他の項目

+++ Samsung Galaxy Tab S9 Ultra +++

+++ Microsoft Surface Pro 10+++

+++ Lenovo Tab P12 Pro +++

+++ Apple iPad Air +++

## 演習3 – トピックとエージェント・フローを作成し、　　　　　　　　エージェントを設計する

トピックの設計は、ユーザーの質問にどのように答えるか、詳細の流れはどうなるかというロジックを扱うため、エージェントを作成する上で非常に重要な部分です。

### タスク1 – Conversation Startトピックを編集する

Conversation
Startトピックは、エージェントのテスト時に最初に呼び出されるトピックです。　これは、Copilot
Studioで作成したすべてのエージェントでデフォルトで利用可能な　システムトピックです。ここでは、このトピックを編集して、エージェントからの挨拶メッセージから会話を継続できるようにしてみましょう。

1.  エージェントの**Overview**ページで、上部のメニューバーから**「Topics」**タブを選択します。
    **「Systems」**を選択して、システムトピックのリストを表示します。リストから「Conversation
    Start」トピックを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  既存のMessage ノードの後に、**Question ノード**を追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  以下のメッセージを入力してください。

+++ Welcome to Contoso Electronics. Please enter your **Phone number**
to 　proceed +++メッセージエリアに入力し**「Identity」**の**「User's
entire 　　　　　　　response」**を選択してください。 **「Save user
response as 」**フィールドの「 **Var1」**をクリックしてください。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

4.  **Var 1 の**名前を+++ MobileNumber +++
    に変更し、トピック間で使用できるように**\[Global\]**を選択してから**\[Save\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

### タスク2 – 顧客の詳細を処理するトピックを作成する

1.  エージェントのOverviewページで、上部のメニューバーから「Topics」タブを
    選択します。**「Add a topic -\> From
    blank」**の横にあるドロップダウンを選択 します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  エージェントの名前を +++Customer Details+++ にします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  **\[Change trigger\]**を選択し、Triggerとして**\[It’s redirected
    to\]** を選択 します。

![Screens screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

4.  トピックを保存するには、**\[Save\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

### タスク3 – 顧客の詳細を取得するためのエージェント・フローを作成する

このタスクでは、エージェント
フローを作成し、顧客が入力した電話番号を入力と　　して渡し、ユーザーが存在するかどうかを確認し、情報を取得して詳細をエージェントに返すフローを設計します。

1.  Triggerノードの下にノードを追加し、**\[Add a tool** -\> **New Agent
    flow\]**を　　選択します。

![](./media/image39.png)

2.  エージェント・フローデザイナーが開きます。 **「Save
    draft」**を選択してフローを保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  上部のメニューから**「Overview」**を選択し、
    **「Edit」**をクリックしてフローの名前を「+++
    GetCustomer+++」と入力します。 **「Save」**を選択します。![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image41.png)

4.  フローを設計するには、もう一度**「Designer」**タブに移動します。
    **「When an agent calls the flow」**ノードを選択し、 **「+ Add an
    input」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  **Text**を選択します。

![](./media/image43.png)

6.  入力内容を +++Phone number+++ として入力し、
    **\[Parameter\]**タブを折りたたみます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  フロー内の2つのノード間の**「Add an
    action」**をクリックします。「+++List rows+++」を検索し、
    **Microsoft Dataverse**の「 **List rows 」アクションを選択します**。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

8.  接続名を +++ **Dataverse** +++ と入力し、 **\[Sign
    in\]**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  管理者テナントの資格情報を使用して**Sign
    in**し、プロンプトが表示されたら **「Allow
    access」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. PowerApps（+++https://make.powerapps.com/+++）にアクセスし、
    **「Customer Record」**テーブルを開きます。 **「Mobile
    number」**フィールドの横にあるドロップダウンをクリックし、 **「Edit
    column」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. 下にスクロールすると、 **「Advanced option」**の下に**「Logical
    name」**という
    フィールドがあります。そのValueをメモ帳に書き留めておいてください。

**重要：** Dataverseでは、各フィールドにlogical nameが関連付けられます。
エージェント・フローで使用する際は、すべてのフィールドにlogical
nameのみを指定してください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. この場合、電話番号は**cr6dd_mobilecontact**です。メモしておいてください。

13. Copilot Studio – Agent flowタブに戻り、「
    Getcustomer」フローを開いて **「List
    rows」**アクションを選択します。

14. Filter行の下に、**\<Logical name of Mobile number\> eq
    'と入力します。　　　\<Logical name\>
    を**前の手順で取得したValueに置き換えます。カーソルを引用符で囲んだまま、「Phone
    number – dynamic variable」を追加します。

この場合は**c cr6dd_mobilecontact eq 'Phone number'**となります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

![A screenshot of a phone number AI-generated content may be
incorrect.](./media/image51.png)

15. リスト行ノードの下に、**Condition**ノードを追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

16. **/**を入力し、 **「Insert expression」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

17. 関数に+++ length(outputs(' List_rows ')?\['body'\]?\['value'\])+++
    と入力し、 **「Add」**を選択します。これにより、List rows
    がValueを返すかどうかがチェックされます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

18. 追加されたConditionの**Trueブランチ**の下にある**\[Add an
    action\]**をクリックし、 新しい**Condition**ノードを追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

19. Conditionの機能領域に「+++not(empty(first(outputs('List_rows')?\['body/value'\])?\[
    cr6dd_lastpurchasedproduct '\]))+++」と入力します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

> **重要– cr6dd_lastpurchasedproduct をCustomer
> Record**テーブルの**「Recent Products
> Purchased」**フィールドの**logical name**に置き換えてください。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image58.png)

20. Condition**を「is equal to true」に設定します。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

21. **Condition1**の**Trueパス**の下に新しいアクションを追加し、**Respond
    to the agent**ノードを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

22. 追加された**「Respond to the agent」**ノードを選択し、「+++ If the
    customer has made a previous purchase +++」に名前を変更して、 **「+
    Add an output」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

23. **Text**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

24. 名前として +++Customer ID+++ と入力し、**Insert
    expression**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

25. +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
    +++ と 入力してください。**cr6dd_customeridentifier**は、Customer
    RecordテーブルのCustomer IDのlogical
    nameです。これを任意のValueに置き換えてください。

26. **\[Add\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

27. 同様に、以下の出力変数と式をそれぞれに追加します。各変数のlogical
    nameを、 ご自身のlogical nameに置き換えてください。

- +++ Customer Name +++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++ Product Category +++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_lastpurchasedproduct'\]+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

28. **Respond to the agent**
    ノードには、以下のスクリーンショットのように 3
    つの出力変数があります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

29. **Condition1ノード**の**False**パスの下に「Respond to the agent
    」ノードを追加します。名前を「+++ If the customer has not made a
    previous purchase +++」に変更します。 **「+ Add an
    output」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

30. 列のlogical nameを対応する列のlogical
    nameに置き換えて、以下の出力変数を入力します。

- +++ Customer ID +++ - +++
  first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
  +++

- +++ Customer Name +++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++ Product Category +++ - +++'1'+++

31. **Falseパス**の下の**Respond to the agent**
    ノードは、以下のスクリーンショットのようになります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

32. ここで、 Condition ノードの**Falseパスの下にRespond to the
    agent**ノードを追加し、名前を +++If the customer does not exist+++
    に変更して、以下のように出力を追加します。

- +++Customer ID+++ - +++'1'+++

- +++Customer Name+++ - +++'1'+++

- +++Product Category+++ - +++'1'+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

33. **GetCustomer**フローは**、**以下のスクリーンショットのようになります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

34. フローの最後にある共通の**Respond to the agent** を右クリックし、
    **「Delete」**を選択して削除します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

35. ラボを保存するには**、「Save draft」**を選択します。保存したら、
    **「Publish」**をクリックしてフローを公開します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

### タスク4 – 顧客を追加するためのエージェント・フローを作成する

このタスクでは、顧客が新規顧客である場合に、その新規顧客をDataverseに追加　するためのエージェント
フローを作成します。

1.  **\[Agent flows\]**タブから、 **\[+New agent flow\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  **「Add a trigger」**を選択し、 **「When an agent calls the
    flow」**に置き換えます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

3.  **\[+ Add an input\]**を選択し、**Text**入力を追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

4.  入力名として +++Name+++ と入力します。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

5.  同様に、次の入力Valueを追加します。

+++**Phone Number**+++

+++Email ID+++

+++ Address +++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image79.png)

6.  ノードの下にアクションを追加し、**Add a new row**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

7.  テーブル名として**Customer Record**を選択し、Advanced
    parametersで**Show all**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

8.  **Address**フィールドをクリックし、**Dynamic
    value**を選択してから、**Address**動的Valueを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image83.png)

9.  同様に、動的なValueを追加します。

- Customer Name – Name

- Email ID – Email ID

- Mobile Number - Phone Number

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

10. Ewqewqewq **Customer ID**の挿入式を開き、「 +++ guid ()+++
    」と入力して**「Add」**を選択します。これは、顧客のIDとして一意のValueを追加するためです。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

11. 新しいアクションを追加し、**Respond to the agent**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

12. +++Customer ID+++
    という名前の出力Valueを追加し、式を挿入して、Valueとして
    +++string(outputs('Add_a_new_row')?\['body/cr6dd_customeridentifier'\])+++
    を入力します。

**cr6dd_customeridentifier を**、列**Customer IDの**logical
name**に**置き換えます。

**\[Add\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

13. フローを保存するには、 **\[Save draft\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

14. フローを保存したら、 **「Publish」**を選択してフローを公開します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

15. **「Overview」**タブを選択します。
    **「Edit」**をクリックします。フローの名前を「+++Add customer
    +++」と入力し、 **「Save」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

### タスク5 – フローを追加し、Customer Detailsトピックを設計する

このタスクでは、顧客の電話番号を取得し、詳細がDataverse内に既に存在するかどうかを確認し、まだ存在しない場合は追加するCustomer
Details トピックを設計します。

1.  Customer Detailsトピックに戻ります。

2.  Trigger ノードの下にノードを追加し、**Add a tool-\>
    GetCustomer**を選択 します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

3.  入力で、変数**MobileNumber**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

4.  **Output**Select a
    variableし、下のスクリーンショットのように、Customer IDとProduct
    Categoryを**Global**としてマークします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

5.  **Actionノード**の下に**Conditionノード**を追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

6.  **Select a variable**で**CustomerID を**選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

7.  Conditionとして**「is not equal to」**を選択し、と入力します。
    **Value**
    フィールドに+++「1」+++を入力します。これは、顧客の詳細がデータベースに既に存在するかどうかを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

8.  Conditionノードの下に、**Set a variable**ノードを追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

9.  **「Select a variable」**をクリックし、 **「Create a new
    variable」**を選択 します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

10. 変数に +++ IsNewCustomer +++ という名前を付け、
    **Global**としてマーク します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

11. Valueを +++'No'+++
    に設定してください。これは、顧客が既にDataverseにデータが存在する古い顧客であることを意味します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

12. 変数ノードの横に新しいノードを追加し、顧客にウェルカム Send a
    messageします。

13. 「ノードを追加」を選択し、 **「Send a
    message**」ノードを選択します。
    メッセージエリアに「+++Welcome+++」と入力し、{x}アイコンをクリックしてSelect
    a variableします。「 **Customer Name」**Select a variableします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

**GetCustomer**を呼び出し、Customer
Recordがすでに存在するかどうかを確認し、存在する場合は顧客に Welcome
メッセージを追加しました。

ここで、Customer Recordがまだ存在しない場合のトピックの部分を設計
します。

13. **\[All other conditions\] ノード**の下に\[Set a variable\]
    ノードを追加し、 **isNewCustomer**変数のValueを +++'Yes'+++
    に設定します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

14. 変数ノードの横に**Message**ノードを追加し、「+++ We do not have your
    details in our system. Please fill in your details below to help us
    serve you better +++」と入力します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

15. Messageノードの横に、**Ask with adaptive card**ノードを追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

16. 画面の右上にある 3 つのドットをクリックし、
    **\[Properties\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

17. **Edit adaptive card**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

18. **Card payload editor領域**に以下の**JSONを入力します**。
    **「Save」を選択 します**。

> {
>
> "type": "AdaptiveCard",
>
> "body": \[
>
> {
>
> "type": "TextBlock",
>
> "size": "Medium",
>
> "weight": "Bolder",
>
> "text": "Please enter your details"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Name",
>
> "label": "Name"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Mobile Number",
>
> "label": "Mobile Number"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Email ID",
>
> "label": "Email ID"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Address",
>
> "label": "Address"
>
> }
>
> \],
>
> "actions": \[
>
> {
>
> "type": "Action.Submit",
>
> "title": "Submit"
>
> }
>
> \],
>
> "version": "1.5",
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json"
>
> }
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image107.png)

19. エディターを閉じるには、 **\[Close\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

20. 作成されたアダプティブ カード ノードの \[Outputs\]
    セクションを展開し、\[Mobile Number\] のValueを選択し、
    Global.MobileNumberSelect a
    variableして、ユーザーが入力した電話番号のValueを保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

21. その他のValueはデフォルトのままにしておきます。

22. アダプティブ
    カードには、顧客の詳細を取得するためのフォームが用意されています。

23. アダプティブ カード ノードの横で、フロー**「Add
    Customer」**を呼び出します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

24. **「Enter or select a value」**の**3 つのドット**をクリックし、
    **CustomerName**を　選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

25. 同様に、フローに渡される他のフィールドの入力変数を追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

26. フローからの出力が保存される出力変数として**Global.CustomerID**を選択　　　します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

27. アクションノードの後に**Message**ノードを追加し**、「+++** Thank
    You! Customer detail has been added to the database. Please select a
    product type to shop .+++」というValueを入力します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

28. トピック**を保存します。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

29. Conversation Startトピックを開き、そこから Customer
    Detailsトピックを 呼び出します。

30. トピック内のQuestionノードの後にノードを追加します。 **「Topic
    management -\> Go to another topic」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

31. **Customer Details** トピックを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

32. トピックを保存するには、 \[Save\]を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### タスク6 – 製品の詳細を取得するためのエージェントフローを作成する

このタスクでは、選択した製品に基づいてDataverseから製品の詳細を取得するエージェント
フローを作成します。

1.  Copilot Studio から**\[Flows\]**タブを選択し、 **\[+ New agent
    flow\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  Triggerノードを選択し、**When an agent calls the flow**アクションを
    呼び出したときを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  テキスト入力を追加し、「+++Product Name +++」という名前を付けます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

4.  フローを保存するには、 **\[Save draft\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

5.  **「Overview」**タブを選択し、
    **「Edit」**をクリックします。名前を「+++ GetProductDetails
    +++」と入力し、 **「Save」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

6.  **「Designer」タブ**に戻り、 **「When an agent calls the
    flow」ノード**の下にある「**Add an action」を選択します。「+++list
    rows+++」を検索し、 「Microsoft Dataverse」の下にある「 List rows**
    」アクションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

7.  以下のValueを入力してください

- **Table name –Product Record**を選択

- Filter rows – +++cr6dd_producttitle eq ' **\<Product Name \>** '+++ \<
  **Product Name** \> を動的なValue ProductName に置き換えます。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image125.png)

8.  **「List rows」ノード**の下に**「Respond to the
    agent」ノード**を追加します。 **「+ Add an
    output」を選択し**、テキスト出力変数を追加します。以下のValueを入力し、「**insert
    expression**」で「Add」をクリックします**。**

    - 名前を入力してください - +++Product Name+++を入力してください

    - 式 - +++ first(outputs('List_rows' )?\[ 'body/value' \])\[
      'cr6dd_producttitle '\]+ ++ (
      **cr6dd_producttitleを**、テーブル内の列 Product Nameのlogical
      nameに置き換えます。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image126.png)

9.  同様に、以下の詳細を持つ別の出力ノードを追加します。

- 名前を入力してください - +++Price+++を入力してください

- 式 - +++ first(outputs(' List_rows ' )?\[ 'body/value' \])\[
  'cr6dd_productprice '\] + ++
  **cr6dd_productpriceを**テーブル内の列**Priceの**logical nameに
  置き換えます

> ノードは次のようになります。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image127.png)

10. **\[Save draft\]**を選択してトピックを保存し、 **\[Publish\]
    を選択して**フローを公開します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

### タスク7 – 顧客から製品カテゴリを取得するためのトピックを作成する

1.  Copilot Studio の \[Topics\] タブから、 **\[++ Add a topic -\> From
    blank\]**を選択 します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

2.  トピック名を「+++Place Order+++」に変更します。Triggerノードの
    Triggerを**「It's redirected to」に変更します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

3.  トピック**を保存します。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image131.png)

4.  Copilot Studio の \[Topics\] タブから、 **\[+ Add a topic -\> From
    blank\]**を選択 します。

![](./media/image129.png)

5.  トピック名を「+++Get Product
    Categories+++」に変更します。Trigger**ノード**で「**Change
    trigger」**オプションを選択し、 **「It’s redirect to」**オプションを
    選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

6.  Trigger**ノード**の下に、**Condition**ノードを追加します。

Global variable **IsNewCustomer** を選択し、Condition「**IsNewCustomer**
**is equal to** +++**'Yes'**+++.」を追加します。。

**+ New condition**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

7.  **Or を**選択します。

OrConditionの下で、Global
Variable**ProductCategoryを選択し**、Conditionを追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image136.png)

8.  Conditionノードの下にQuestionノードを追加し、「+++ Select a category
    +++」と入力して、 **「+New option」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

9.  オプション +++Laptop+++ を入力し、+ New optionを再度選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

10. 同様に、他の2つのオプション「+++**Desktop**+++」と「+++**Tablet+++」を追加します。
    「Save user response as」**で変数を選択し、「+++ **ProdCatchoice**
    +++」という名前を付けます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

11. Questionノードの下に**Set a variable
    value**ノードを追加して、Questionノードから受け取った選択肢を文字列に変換します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

12. Global Variable**「ProductCategory」を選択します**。「 **To
    value」**フィールドで3つの点をクリックし、「**Formula」**タブを選択します。式「+++
    Text( Topic.ProdCatchoice )+ ++」を入力し、
    **「Insert」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

13. Set variableノードの下に、新しいノード**「Topic management** -\>
    **Go to another topic** -\> **Place Order」を追加します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

14. これで、1つのパスが完全に完成しました。ユーザーからカテゴリーを取得し、「注文」トピックを呼び出します。

15. このトピックの先頭に戻ります。その他のConditionに該当する場合は、Questionノードを追加してください。「**+++**
    Based on your recent purchase we suggest you products in \<Product
    Category\> category. Would you like to continue? +++
    」というメッセージを追加します。

メッセージ内の**\<Product
Category\>をGlobal.ProductCategory**に置き換えます。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image143.png)

16. 2つの選択肢「+++Yes+++」と「+++No+++」を追加します。「Save user
    response as」の下の変数をクリックし、名前を「+++
    Userschoiceofcategory +++」に変更します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

17. Questionノードの下にConditionノードを追加します。

最初のConditionを**「Userschoiceofcategory is equal to
Yes」**に設定します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

36. このノードの下に**Topic management nodeし**、**Place
    Order**トピックを呼び出します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

18. Conditionノードで、Conditionノードの右上隅にある 3
    つのドットを選択し、**Insert new condition**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image147.png)

19. Condition「 **Userschoiceofcategory is equal to No」**を追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

20. Conditionノードの下にQuestionノードを追加し、「+++ Select a category
    +++」と入力して、 **「+New option」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

21. オプション +++Laptop+++ を入力し、+ New optionを再度選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

22. 同様に、他の 2 つのオプション +++**Desktop**+++ と +++Tablet+++
    を追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

23. Questionノードの下に**Set a variable
    value**ノードを追加して、Questionノードから受け取った選択肢を文字列に変換します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

24. Global Variable**「ProductCategory」**を選択します。 **「To
    value」**フィールドで3つの点をクリックし**、「Formula」**タブを選択します。式「+++
    Text( Topic.Var 1)+ ++」を入力し、 **「Insert」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

25. Set variable valueノードの下に、新しいノード**「Topic management**
    -\> **Go to another topic** -\> **Place Order」を追加します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

26. トピックを保存するには、 \[Save\]を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image151.png)

27. トピック**「Customer Details」**を開き、最後のノードに移動します。

28. トピック**Get Product Categories**を呼び出すための**Add a new
    node**します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image152.png)

29. トピックを保存するには、 \[Save\]を選択します。

![](./media/image153.png)

### タスク8 – 注文を行うエージェント・フローを作成する

このタスクでは、顧客が選択した製品に基づいて注文を行うエージェント
フローを　　作成します。

1.  **\[Agent flows\]タブ**から、 **\[+ New agent flow\]**
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image154.png)

2.  **Add a trigger ノード**をクリックし、**When an agent calls the
    flow**ノードを選択します。

![](./media/image155.png)

3.  2 つの**Text**変数 +++Product Name+++ と +++Customer ID+++
    を**Input**として追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image156.png)

4.  フローを保存するには、 **「Save Draft」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image157.png)

5.  上部のメニューから**「Overview」**を選択し、
    **「Edit」をクリックして**フローの名前を「+++ PlaceOrder
    +++」と入力します。 **「Save」を選択します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image158.png)

6.  **「Designer」タブ**に戻り、「Add a new action」を選択し、
    「Dataverse」の下の**「Add a new row」を選択します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image159.png)

7.  テーブル名として**「Order Record」を選択し**、 「Advanced
    parameters」の**「Show all」をクリックします**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image160.png)

8.  以下のValueを入力してください。

Customer Identifier - **Customer ID** (Dynamic value

Order identifier – Insert expressionにguid( )を入力

Order Status - +++**Order Placed**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image161.png)

9.  **Respond to the agent**ノードを追加します。![A screenshot of a
    computer AI-generated content may be
    incorrect.](./media/image162.png)

10. 変数を追加し、+++Order ID+++ という名前を付けます。

Valueを次のように入力します +++ string(outputs('Add_a_new_row' )?\[
'body/cr6dd_orderidentifier' \])+ ++ (
**cr6dd_orderidentifier**を、Order Recordテーブルの列 Order ID のlogical
nameValueに置き換えます。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image163.png)

11. **「Save draft」**をクリックしてフローを保存し、
    **「Publish」**をクリックして フローを公開します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image164.png)

### タスク9 –Place Orderトピックの設計

このタスクでは、注文を配置して Dataverse
テーブルを更新するトピックを設計 します。

1.  エージェントの**Topicタブから**トピック「**Place
    Order」を開きます**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image165.png)

2.  メッセージを含むMessage ノードを追加します +++ Options based on the
    category will be listed below + ++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image166.png)

3.  「ProductCategory （Global Variable）が +++Laptop+++
    と等しい」というConditionを入力します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image167.png)

4.  ノードの下にQuestionノードを追加し、「+++ Select a Laptop product
    +++」と いうメッセージを入力します。
    **「Identity」**の下で**「Laptop」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image168.png)

5.  **\[Select」**をクリックし、利用可能な 5
    つのオプションをすべて選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image169.png)

6.  Variable nameを +++ProdNameLapChoice+++ と入力します

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image170.png)

7.  次に、同じ手順に従って、 ProductCategoryが+++Desktop+++ および
    +++Tablet+++ に等しいConditionノードを追加します。

8.  ValueをVariable namesに保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image171.png)

9.  **「Select a Laptop product」**Questionノード**の**下にある**「Set
    variable value」ノード**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image172.png)

10. 作成された変数の名前を +++ ProdNameSelected +++ に変更し、
    **Globalに設定します**。![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image173.png)

11. FormulaフィールドのValueを +++ Text( Topic.ProdNameLapChoice )+ ++
    に設定 します。 (別のVariable
    nameを使用している場合は置き換えてください)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image174.png)

12. 同様に、**Desktop**と**Tabletのブランチ**の下に**Set variable
    valueノードを追加 します**。**Set variable
    value**で**ProdNameSelectedを選択します。** 使用したVariable
    nameに応じて、\[To value\] フィールドに式を挿入します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image175.png)

13. これらすべてのノードの下に共通のActionノードを追加し、
    GetProductDetailsフローを呼び出します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image176.png)

14. フローに渡す入力変数**ProdNameSelected**を選択します。その他のValueは
    デフォルトのままにしておきます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image177.png)

15. アクションの下にMessageノードを追加し、以下のメッセージを入力します。\<roductName\>と\<Price\>を対応するVariable
    nameに置き換えます。

Product Details

- Product Name - \<ProductName\>

> ​

- Price - \<Price\>

​

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image178.png)

16. Messageノードの下に、 「+++ Would you like to place order for this
    item？+++」というメッセージを含むQuestionノードを追加します。オプションとして**「Yes」**と**「No」**を追加し、Variable
    nameを「+++ PlaceOrder +++」にします。

![](./media/image179.png)

17. Question ノードの下にConditionノードを追加し、 1 つのブランチに
    **PlaceOrder isequal to Yes** というConditionを追加します。**all
    other conditions**は 2 番目のブランチになります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image180.png)

18. 次のステップとしてフロー**PlaceOrderを呼び出します。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image181.png)

19. フローへの入力として**ProductName**と**CustomerID を**選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image182.png)

20. 次に、この下に「+++ Your order is placed. This is your Order ID for
    reference
    -\<OrderID\>+++」というメッセージを含むメッセージノードを追加します（\<**OrderID**\>を変数OrderID（フローの出力変数）に置き換えます）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image183.png)

21. これにより、**PlaceOrder isequal to
    Yes**ブランチ**が完了しました**。次に、**all other conditions
    ブランチに進みます**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image184.png)

22. その下に、「+++ Do you want to go to the main
    menu?+++」というメッセージと「Yes」および「No」のオプションを含むQuestionノードを追加します。変数の名前を
    +++GoToMainMenu+++ にします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image185.png)

23. **「GoToMainMenu is equal to
    Yes」**というConditionを追加します。このConditionのもう一方の分岐は**「All
    other conditions」**になります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image186.png)

24. **Select Product Category +++**を含むQuestionノードを追加し、3 つの
    オプション +++ **Laptop** +++、+++ **Desktop** +++、および +++
    **Tablet** +++ を追加 します。

結果が保存されるVariable
nameをメモしておいてください。次のステップでテキストに変換します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image187.png)

25. **Set variable valueノード**を追加し、**Set
    variableの下のProductCategory** 変数を選択し、**Formulaタブの下に
    +++ Text( Topic.Var 1)** + ++というValueを入力します。

**Var1 を**Variable nameに置き換えます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image188.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image189.png)

26. Set variable valueノードの下に、**Go to step**ノードを追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image190.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image191.png)

27. ノードを追加したら、この時点で制御を渡すステップを選択する必要があります。上**にスクロールして、このトピックの先頭にある**Messageノードを選択してください。顧客から**ProductCategoryを**取得済みなので、最初から実行する必要があります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image192.png)

28. 最後に、「+++ Thank you for shopping with us! Please visit again!+++
    」という
    メッセージを記載した共通Messageノードを追加します。次に、\[Save**\]
    を選択して**トピックを保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image193.png)

## 演習4 – Triggerを追加する

この演習では、Orderテーブルに新しい行が追加されたとき、または既存の行が変更されたときにトリガーを起動し、顧客に自動的にメールを送信するトリガーを追加します。これにより、このシナリオにおけるエージェントの自律機能が定義されます。

1.  エージェントのOverviewタブを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image194.png)

2.  ページを下にスクロールして、 **「Add trigger」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image195.png)

3.  **When a row is added, modified or
    deleted**オプションを選択し、**Nextを選択 します**。

![](./media/image196.png)

4.  **Microsoft Copilot Studio**と**Dataverseが接続され**たら、
    **\[Next\]をクリック します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image196.png)

5.  以下のオプションを選択し、残りはデフォルトのままにして**「Create
    trigger」を選択します**。

- Change Type – Added or Modified or Deleted

- Table name – Order Record

- Scope - Organization

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image197.png)

6.  完了するまで数分かかる場合があります。完了したら、 「Add
    trigger」ダイアログで**「Close」**を選択してください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image198.png)

7.  エージェントの**Overviewページ**のトリガー
    セクションで、追加したトリガーの横にある**3
    つのドットをクリックし、Edit in Power Automate**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image199.png)

8.  フローの最初のノードを選択し、 **\[Select columns\]**の下に列名 +++
    cr6dd_orderidentifier、cr6dd_customeridentifier+++を追加します(これを、**Order
    Recordテーブル**の**Order ID列**と**Customer ID列**のlogical
    nameに**置き換えます**)。

![](./media/image200.png)

9.  新しいノードを追加し、その中で**List rows**アクションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image201.png)

10. 行のリストアクションで、**Table name**として**Customer
    Recordを選択します**。

**Filter rows**の下に「+++ **cr6dd_customeridentifier eq ''**
+++」と入力し、列名を**Customer IDの**logical
name**に置き換えます**。**カーソルを**
一**重引用符の内側に入力します**。

![A screenshot of a list AI-generated content may be
incorrect.](./media/image202.png)

11. \[Insert expression\] を選択し、 +++String(triggerOutputs( )?\[
    'body/cr6dd_customeridentifier' \])+ ++ と入力し、
    **cr6dd_customeridentifier を**CustomerID のlogical
    nameに置き換えて、 **\[Add\]を選択します**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image203.png)

12. **List rows**の横に、アクション**「Send an email
    (V2).」**を追加します。

![A screenshot of a mail box AI-generated content may be
incorrect.](./media/image204.png)

13. **「Sign in」**をクリックし、資格情報でサインインします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image205.png)

14. **\[To\] フィールド**に式を挿入し、 +++first(outputs('List_rows'
    )?\[ 'body/value' \])\[ 'cr6dd_emailaddress '\]+ ++ と入力
    します。cr6dd_emailaddress**を**Customer Recordテーブルの電子メール
    ID フィールドのlogical nameに置き換えて、 **\[Add\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image206.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image207.png)

15. 以下の詳細を入力してください。

> Subject - +++Order Placement+++

Body –

Hi,

This is to update you that your order has been placed. Thank you for
shopping with us.

Thank You.

16. フローを保存して公開します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image208.png)

17. Copilot Studio エージェント ページに戻り、
    **\[Publish\]を選択して**エージェントを公開します。

![](./media/image209.png)

18. 確認ダイアログで**「Publish」を**選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image210.png)

19. うわぁぁぁぁぁ

## 演習5 – エージェントのテスト

この演習では、エージェントがどのように動作するかをテストします。

1.  エージェント ページから**\[Test\]を選択して**\[Test\]
    ペインを開きます。

2.  +++3148987666+++
    と入力してください。これは既存の顧客の電話番号です。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image211.png)

3.  指定されたオプションから**「Yes」**を選択します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image212.png)

4.  指定されたオプションから**product**を選択します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image213.png)

5.  指定されたオプションから「Yes」を選択します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image214.png)

6.  注文が確定し、参照 ID が顧客に提供されます。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image215.png)

7\.
受け取ったIDの注文の配送状況を追跡するなど、他の質問もできます。そのためのトピックは設定していませんが、ナレッジソースに基づいて回答が提供されます。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image216.png)

異なるオプションを選択して、他のシナリオをテストしてください。新しい顧客を追加し、顧客レコードテーブルに追加されたメールが自分のメールアドレスに届いていることを確認してください。

## まとめ：

このラボでは、自律型ショッピングエージェントの設計を学びました。主なトピックは以下のとおりです。

- 変数

- エンティティ

- トピック

- エージェントフロー

- トリガー

- 知識源
