# ラボ 04 – Gen AI機能でReal Estate copilot を強化　強化

**ラボ期間**– 80 分

**目的:**

Copilot for Real
Estateアプリにエンティティ、スロット入力、変数の使用を実装します。Generative
AIを実装することで、Real
Estateアプリ用に作成されたCopilotを強化し、顧客体験を向上させます。

## 手順 1: エンティティを活用してコパイロットを改善

Microsoft Copilot Studio
は、エンティティを使用してユーザーの意図を理解します。よく使用される情報に対応する、多数の事前構築エンティティが用意されています。また、特定の目的に合わせてカスタムエンティティを作成することもできます。

### タスク 1: 事前構築のエンティティを表示する

1.  !\![https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/)!!
    でCopilot Studio を開き、**Real Estate Booking
    Service**エージェントをを開きます**。**

2.  右上の画面で**Settings**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  **Entities**タブを選択する。事前構築のアプリのリストを表示されます。![](./media/image2.png)

### タスク 2: プロパティタイプEntityを作成する

1.   **+ Add an entity** を選択し、**+ New entity**を選択する。

![](./media/image3.png)

2.  **Closed list**のタイルを選択する。

![](./media/image4.png)

3.  以下の詳細を入力する

    - Name - !!Property Type!!

    - List itemsの下にアイテムを入力する – !!Apartment!! -
      **Add**を選択する

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

4.  **Enter
    item**フィールドに!!**Condominium**!!を入力し、**Add**を選択する。

5.  **Enter
    item**フィールドに!!**Duplex**!!を入力し、**Add**を選択する。

6.  **Enter item**フィールドに!!**House**!!を入力し、**Add**を選択する。

7.  

![](./media/image6.png)

7.  **Apartment**に**+
    Synonyms**を選択し、!!**Flat**!!を入力して **+** アイコンを選択し、**Done**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  **House**に**+ Synonyms**を選択し、!! **Single-family
    home**!!を入力して **+** アイコンを選択し、**Done**を選択します。

9.  **Condominium**に**+ Synonyms**を選択し、!!
    **Townhouse**!!を入力して **+** アイコンを選択し、**Done**を選択します。

10. **Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. **Close**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

### タスク 3: ベッドルーム数エンティティの作成

1.  **+ Add an entity**を選択して**+ New entity**を選択します。

![](./media/image10.png)

2.  **Regular expression (Regex)** を選択します。

![](./media/image11.png)

3.  以下の詳細を入力し、**Save**を選択する。

    - Name - !!**Number of Bedrooms**!!

    - Pattern - !!**\[1-5\]**!!

![A screenshot of a cell phone AI-generated content may be
incorrect.](./media/image12.png)

4.  **Close**を選択する。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image13.png)

5.  **Settings**画面を閉じる。

![](./media/image14.png)

### タスク 4: エンティティを使用する

1.  **Topics**タブを選択する。**Book a Real Estate
    Showing**トピックを選択する。

![](./media/image15.png)

2.  プロパティの質問ノードの上にある **+**
    アイコンを選択し、**質問する** を選択します。

![](./media/image16.png)

3.  Fill in the below details.

    - **メセッジを入力**- !!What type of property do you want to see?!!

    - **Identify** –**Property Typeを選択**

    - \[**ユーザーのオプションを選択\]**
      を選択し**、**すべてのリスト値に対して **\[表示**\]
      オプションをオンにします 。

![](./media/image17.png)

4.  Select the variable in **Save user response
    as**の中に変数を選択して**Variable name**に!!**PropertyType**!!
    を入力する。

![](./media/image18.png)

5.  新しい質問ノードの下にある **+** アイコンを選択し、**Ask a
    questionを選択します**。

&nbsp;

1.  以下の詳細を入力し、\[Save\]をクリックします。

    - **Enter a message** - !!How many bedrooms do you need?!!

    - **Identify -** Select **Number of Bedrooms**

    - **Save user response as** - Enter !!NumberofBedrooms!!
      for **Variable name**

![](./media/image19.png)

## 手順 2: アクションの作成

Microsoft Copilot Studio can access data in Microsoft Dataverse using
Power Automate cloud flows

### タスク 1: プロパティを取得するための Power Automate フローを作成する

1.  トップメニューから「**Actions**」タブを選択します。\[**+ Add an
    action\]** を選択します。

![](./media/image20.png)

2.   **+ New action** -\> **New Power Automate flow**を選択する。

![](./media/image21.png)

3.  プロンプトされた場合Power Automateにサインインする。

4.  右上隅にある \[New Designer**\]** のトグルを有効にします
    (まだ行っていない場合)。\[**Save and switch\]** を選択します。

![](./media/image22.png)

5.  画面左上の **\[Run a flow from Copilot**\] を選択し、「!!**Get
    Property**!!をフロー名として使用します。

![](./media/image23.png)

6.  トリガー ステップ \[**Run a flow from Copilot**\] を選択し、**\[+
    Add input\]** を選択します。

![](./media/image24.png)

7.  **Text**を選択する

![](./media/image25.png)

1.  以下の詳細を入力する。

    - **Input** – !!Bedrooms!!

    - **Please enter your input** - !!Number of Bedrooms!!

![](./media/image26.png)

1.  フローの 2 つのステップの間にある \[+\] アイコンを右クリックし
    、\[**Add an action\]** を選択します。

![](./media/image27.png)

8.  Enter !!**Dataverse**!! in
    the **Search**フィールドに!!**Dataverse**!!を入力して **Microsoft
    Dataverse connectorでSee moreを選択する。**

\![\](./media/image27.png)

11. **List rows**アクションを選択する。

![](./media/image28.png)

1.  プロンプトされたら、\[**OAuth**\] を選択し、\[Sign-in\]
    を選択します。プロンプトで、テナント ID を使用してサインインします。

![](./media/image29.png)

12. テーブル名として **\[Real Estate Properties\]** を選択します。

13. すべてのオプションが自動的にリストされない場合は**、\[Show all**\]
    を選択します

14. **Filter Rowsフィールドに** !!contoso_bedrooms eq!! を入力する。

&nbsp;

1.  **eq** の横にある**スペースバー**を使用して
    、スペースの後に値を追加していることを確認します。**動的コンテンツ**を使用して
    **Bedrooms** パラメーター を選択し 、追加 を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

15. **Respond to Copilotアクションを選択して** **+ Add an
    output**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

16. **Text**を選択する。

17. 以下の詳細を入力する

    - **Enter a name** - !!PropertyId!!

    - **Enter a value to respond with** - 「**Insert
      Expression**」を選択し、次の式を入力します。
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_realestatepropertyid'\]!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

18. **Add**を選択

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

19. !\![https://make.powerapps.com](https://make.powerapps.com/)!!
    から、Real Estate Property テーブルを開きます。「Property
    Name」（Copilot で作成した場合は Real Estate Property
    または若干異なる可能性があります）列に移動し、「Edit
    column」→「Advanced
    options」を選択します。論理名の値を確認します。contoso_newcolumn
    のような形式になっているはずですが、多少異なる場合もあります。contoso\_
    の後の部分をローカルに保存します。論理名が contoso_newcolumn
    の場合、次の手順で使用するため、newcolumn をメモしておいてください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

20. Power Automate フロー ページに戻り、 **\[+ Add an output\]
    を選択します**。

21. **Text**を選択する。

    - **Enter a name** - !!PropertyName!!

    - **Enter a value to respond with** - 「**Insert
      Expression**」を選択し、次の式を入力します。
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]!!

上記の式の **contoso_propertyname** の **propertyname**
を、この前の手順で保存した値**(newcolumn**) に置き換えます。

::: 付帯
この列の論理名は標準値ではなく、テーブルの値に基づいてチェックおよび更新する必要があるため、この値の置換を行う必要があります。:::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

22. **Settings**を選択する**。Asynchronous
    Response**は**Off**に設定されていることを確立する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

23. **Save draft**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

24. 保存されてから**Publish**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

25. Power Automateタブを閉じる。

### タスク 2: プロパティを取得するための Copilot アクションを追加する

1.  Copilot Studio ページに戻り、 \[**Refresh\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

1.  **Get Property** flowを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

2.  **Add action**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

3.  **Topics**タブを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

4.  **Book a Real Estate Showing**トピックを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

5.  Select the **+** icon below the **How many bedrooms do you
    need**質問ノードの下にある**+**アイコンを選択し、 **Add an
    action**を選択する。**Get Property**フローを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

6.  **Bedrooms**インプットパラメータで**NumberofBedrooms**変数を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

7.  **Which property do you want to
    see?**質問ノードで三つのドットを選択し、**Delete**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

8.  アクションノードの下に**+**アイコンを選択し、**Send a
    message**を選択する。

9.  以下の詳細を入力する。

    - **メセッジを入力**- !!Property!!を入力する

    - **Insert
      variable**アイコンを選択し、**PropertyName**変数を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. **Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. 保存したら、\[**Publish\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. Publishの確認ダイアログで**Publish**をクリックする。![A close-up of
    a white background AI-generated content may be
    incorrect.](./media/image50.png)

### タスク 3: Power Automate フローを作成して予約を行う

1.  \[**Action**\] タブを選択し、\[**+ Add an action\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

1.   **+ New action** -\> **New Power Automate flow**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

2.  Select 画面の左上から**Run a flow from
    Copilot**を選択してフロー名で!!**Booking Request**!! を入力する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

3.  トリガーステップ**Run a flow from Copilot**を選択して**+ Add an
    input -\> Text**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  以下の詳細を入力する

    - Input - !!**PropertyId**!!

    - Please enter your input **-** !!**Property**!!

5.  **+ Add an input -\> Text**を選択する

    - Input - !!**ViewerName**!!

    - Please enter your input **-** !!**Viewer Name**!!

6.  **+ Add an input -\>** **Text**を選択する

    - Input - !!**ViewerEmail**!!

    - Please enter your input **-** !!**Viewer Email**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

1.  フローの 2 つのステップの間にある **+** アイコンを選択し、**Add an
    action**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

7.  検索フィールドに!!**Dataverse**!!を入力してDataverseコネクターで**See
    more** を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

8.  **Add a new row**アクションを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

1.  テーブル名として **\[Booking Requests**\] を選択します。

&nbsp;

9.  **Booking Name**フィールドに!!**Copilot booking**!!を入力する。

10.  **Show all**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

11. **Property (Real Estate
    Properties)** フィールドに!!contoso_bookingrequests()!!
    を入力して、カーソルを括弧内に移動し**Dynamic content**を使用する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

12. PropertyId **パラメーター**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

13. **Dynamic content**を使用により**Viewer
    Name** フィールドに、**ViewerName**選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

1.  「**Dynamic content」**を使用して、**「Viewer
    Email」フィールドの**「**ViewerEmail」**パラメーター を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

14. パラメータは、次のスクリーンショットのようになります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

15.  **Respond to
    Copilot**アクションを選択する。**Settings**を選択して**Asynchronous
    Response**は**Off**に設定することを確実する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

16. **Save draft**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

17. 保存されてから**Publish**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

18. Power Automateタブを閉じる。

### タスク 4: 予約リクエストを作成するための Copilot アクションを追加する

1.  Copilot Studio ページに戻り、\[**Refresh\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

2.  **Booking Request**フローを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

3.   **Add action**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

4.  Review inputs and outputsで**Next**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

5.  **Review and finish**画面に**Finish**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

6.   **Topics**を選択して、 **Book a Real Estate
    Showing**トピックを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

7.  **What date and time do you want to see the
    property?**ノードの下にある**+**アイコンを選択し、**Add an
    action**を選択する。

8.  **Booking Request**フローを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

9.  **PropertyId**インプットパラメータの **PropertyId** 変数を選択する。

**ViewerName**インプットパラメータの**Name** 変数を選択する。

**ViewerEmail**インプットパラメータの**EmailAddress**変数を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

10. アクションノードの下にある **+** アイコンを選択します。 **Topic
    management**選択し、**Go to another topic**を選択してから**End of
    conversation**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

11. **Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

12. .

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)保存してから**Publish**を選択し、確認ダイアログで再度**Publish**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 手順 3: エージェントをテストする

### タスク 1: エージェントをテストし、予約リクエストを行う

1.  画面右上の「**Test**」ボタンを選択してテストパネルを開きます。画面右上のテストパネル上部にある**3つのドット**を選択します。「**Track
    between topics**」を選択します。.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  **「会話が開始**」メッセージが表示されたら、エージェントは会話を開始します。

&nbsp;

1.  応答として、作成したトピックのトリガー フレーズを入力します。

!!I want to book a real estate showing!!

3.  Copilotは「**名前は何ですか?**」の質問で応答します。

4.  名前を入力する。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image82.png)

5.  メールアドレスの入力をのプロンプトが表示されたら、メールアドレスを入力する。入力後、情報が正しいかどうかを確認する質問が表示され、「**はい**」または「**いいえ**」を選択できます。「**はい**」を選択する。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image83.png)

6.  Type of propertyプロンプトが表示されたら**House**を選択する。

7.  Number of bedroomsプロンプトで!!**2**!! を入力する。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image84.png)

8.  **What date and time do you want to see the
    property?**プロンプトで!!Tomorrow 2:00 PM!!を入力する。

9.  **Did that answer your question?**プロンプトで**Yes**を選択する。

10. 任意のレーティングを選択する。

11. **Can I help with anything else?**プロンプトで**No**を選択する。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image85.png)

### タスク 2: 予約リクエストの確認

1.  !\![**https://make.powerapps.com**](https://make.powerapps.com/)!!でPower
    Appsポータルに移動する。

2.  左側画面に**Tables**を選択し、**Custom**を選択する。

3.  **Booking Request**テーブルを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

4.  \[Booking Request columns and data**\] に** 、Copilot
    の予約リクエストが作成されたことが表示されます.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

## 手順 4: Generative AIを設定する

この手順では、Generativeアンサー機能を使用して副操縦士の応答を改善する方法を学習します。

### タスク 1: Generative AIを有効にする

1.  まだログインしていない場合!\![https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/)!!でテナント資格情報を使用して
    Copilot Studio にログインする。

2.  **Real Estate Booking Service**エージェントを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

3.  右上の画面にある**Settings**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

4.  **Generative AI**タブを選択する。

**How should your copilot decide how to
respond**の下に**Generative(preview)** を選択する。

**How strict should the content moderation
be?**については**Medium**を選択する。

Saveを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

5.  **Close** the Settings pane.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### タスク 2: Knowledgeを有効にする

1.  **Overview**タブをクリックする。

2.  Knowledgeセクションで一般的なナレッジが有効になっていることを確認する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

### タスク 3: ウェブサイトからknowledgeを追加する

1.  **Knowledge**セクションのしたに**+ Add knowledge** を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

2.  **Public websites**タイルを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

3.  Enter the public website link
    !\!<https://create.microsoft.com/templates/real-estate>!!.
    Select **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

4.  Nameフィールドに!!Real Estate Website!!
    名前を入力し、**Add**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

### タスク 4 Dataverseからナレッジを追加する

1.  **Knowledge**タブを選択する。**+ Add knowledge**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

2.  **Dataverse(preview)**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

3.  **Real Estate Property**テーブルを選択し**Next**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

4.  次の画面にデータプレビューし、**Next**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

1.  詳細を確認し、\[ **Review and
    finish\]**画面で\[**追加**\]をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

### タスク 5: ファイルからナレッジを追加する

1.  **Knowledge** タブで**+ Add knowledge**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

2.  **Upload files**セクション下に**click to
    browse**を選択し、**SummitRealtyCaseStudy.docx** at **C:\LabFiles** ファイルを参照して、選択する。 

3.  **Add**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

:::**注意:** ファイルのアップロードが完了し、インデックス作成が完了するまでに時間がかかります。\[ナレッジ\]
タブでステータスを確認して、ファイルが使用可能であることを確認します.
:::

### タスク 6: System fallbackトピックに generative回答を使用する。

1.  **Topics**タブを選択して**System**選択する。**Fallback**トピックを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

2.  メセッジノードにある三つのドットを選択して**Delete**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

3.  Conditionノードの下にある**+**アイコンを選択して、**Advanced**を選択し,
    **Generative answers**を選択する。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image106.png)

4.  **Input**フィールドを選択し、**Select a
    variable** 画面に**System**を選択する。**そこで Activity.Text**を選択する。 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image107.png)

5.  **Data sources**の下に**Edit**選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

6.  **Search only selected sources**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

7.  **SummitRealtyCaseStudy**文章を選択する。**Allow the AI to use its
    own general knowledge**の選択を解除にする。**Medium** for **Content
    moderation**の**Medium**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

8.  Saveを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

### タスク 7: セキュリティの構成

1.  \[概要**\]** タブを選択します 。

&nbsp;

1.  画面右上の**\[Settings**\]を選択します .

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

2.  **Security**タブを選択してから**Authentication**タイルを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

3.  Authenticate with Microsoft **(Entra ID authentication in Teams and
    Power App)**を選択する。

4.  Saveを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

5.  Saveを選択する。

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image115.png)

6.  **Close**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

7.  **Overview**タブを選択する

8.  Select **Publish**を選択してダイアログで再度**Publish**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

### タスク 8: エージェントの知識をテストする

1.  画面の右上にある \[Test**\]** ボタンを選択して 、テスト
    パネルを開きます.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

2.  Activity Mapを選択します (まだ選択されていない場合).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

3.  テスト パネルの \[**更新\]**
    ボタンを選択して、新しい会話を開始します 。

4.  !!What is Summit Realty group?!!
    を入力して、 **send**をクリックする。

5.  アップロードされたファイルはフォールバック
    トピックで検索するナレッジ
    ソースとして追加されているため、以下のスクリーンショットのように、アップロードされたファイルからの応答が返されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

**要約:**

このラボでは、次のことを学びました

- エンティティとスロット充填を使用する

- フローアクションの実装

- エージェントにナレッジを追加する

- Generative AIを有効にする

 
