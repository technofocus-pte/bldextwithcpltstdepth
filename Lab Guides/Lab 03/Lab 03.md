# ラボ – ナーレジグラウンディングとライブコネクタを備えたインテリジェントエージェントの設計

**紹介**

現代のユーザーは、単純なキーワードマッチングを超えた、インテリジェントで文脈に基づいた応答を期待しています。このラボでは、複数のナーレジソースを横断的に推論し、リアル・タイムでアクションを実行して包括的かつ正確な回答を提供するインテリジェントエージェントの作成方法を学びます。

**目的**

このラボでは、単純なQ&Aの域を超え、文脈に基づいた複数の要素を含む回答を提供するインテリジェントアシスタントを構築します。

ラボの最後には、会話作成エクスペリエンスを活用して、インテリジェントエージェントを作成します。エージェントのトーン、動作、指示をブランドに合わせて設定します。Wikipediaなどの公開ウェブサイトをナーレジソースとして追加し、事実に基づいた情報を提供します。一般知識を無効にすることで、ハルシネーションを減らし、正確性を確保できます。　

## タスク1: 新しいエージェントを作成し、ナーレジを追加する

Copilot Studio の会話型セットアップ
エクスペリエンスを使用して、カスタム指示と Wikipedia
のナーレジ統合を備えた Nova Aを作成します。

1.  ブラウザを開き、+++copilotstudio.microsoft.com+++
    に移動し、資格情報を使用してログインします。

2.  **Dev One** 環境を選択します。

3.  ホーム ページで、\[**Create agent**\] を選択します。

![](./media/image1.png)

4.  エージェントが作成されたら、**Details**に対して**Edit**を選択します。

![](./media/image2.png)

5.  以下の詳細を入力し、「**Save**」を選択します。

    - Name - +++Researcher agent+++.

    - Description - +++Answers multi-part questions by combining
      historical facts, biographical data, and real-time information
      like weather. Ideal for deep research, exploration, and knowledge
      synthesis+++

> ![](./media/image3.png)

6.  「**Instructions**」の下に以下の内容を入力し、「**Save**」を選択します。

You should answer complex questions using verified public information
and real-time lookups like weather or conversions. You should give
clear, concise answers and handle multiple questions one at a time. You
must not speculate, share unverified or sensitive information, or
compare products or companies. You should communicate clearly and
professionally, using a friendly tone and light emojis when appropriate.

![](./media/image4.png)

7.  下にスクロールして「**+ Add knowledge**」を選択し、ナレッジ
    ソースを追加します。

![](./media/image5.png)

8.  リストから「**Public Website**」オプションを選択します。

![](./media/image6.png)

9.  次の画面で「**Add**」を選択し、「**Add to agent**」を選択します。

![](./media/image7.png)

![](./media/image8.png)

10. 次に、ハルシネーションを軽減するために一般知識を無効にします。右上から「**Settings**」を選択してください。

![](./media/image9.png)

11. \[Knowledge\] セクションの \[**Use general knowledge**\]
    オプションを**オフ**に切り替えます。

![](./media/image10.png)

12. Testペインに以下のメッセージを入力し、\[**Send**\]
    をクリックして出力を確認します。

> Write a draft email to request refund from a toaster that is not
> working properly (bread keeps burning)

![](./media/image11.png)

![](./media/image12.png)

## タスク2: 天気コネクタを追加する

このタスクでは、天気コネクタを追加してリアル・タイムのデータ取得を可能にし、生成オーケストレーションをテストします。エージェントが事実に基づいた制御された応答のみを提供すると同時に、天気予報などのリアルタイムアクションを実行して包括的かつ複数ステップの回答を得られるようにします。

1.  上部のメニューから\[**Tools**\]タブを選択します。

![](./media/image13.png)

2.  検索ボックスに+++MSN Weather+++と入力し、「**Get current
    weather**」を選択します。

![](./media/image14.png)

3.  「**Not
    connected**」メッセージの横にあるドロップダウンを選択し、「**Create
    new
    connection**」を選択します。次の画面で「**Create**」を選択します。

![](./media/image15.png)

![](./media/image16.png)

4.  \[**Add and configure**\]
    を選択して、ツールをエージェントに追加し、必要に応じて構成します。

![](./media/image17.png)

5.  追加したら、「**Additional details**」を選択します。

![](./media/image18.png)

6.  \[Credentials to use\] の下で、\[**Maker-provided credentials**\]
    を選択します。

**注記：**作成者提供の認証情報を使用する場合、エージェントのエンドユーザーは、サービスに接続する際に独自のコンテキストと接続を使用するように求められません。代わりに、エージェントを設定したユーザーのコンテキストと接続が使用されます。-
ユーザー固有のデータを必要としないアクションには、作成者認証のみを使用してください。他のユーザーの認証情報を使用すると、データ漏洩のリスクが生じる可能性があります。-
ロールベースのアクセスシナリオにはユーザー認証を使用してください。-
認証方法の選択がセキュリティに与える影響を常に確認してください。

![](./media/image19.png)

7.  **Inputs**, **Units**, -\> **Fill using** -\> **Custom
    value**を選択して、「**Metric**」を選択します。

![](./media/image20.png)

8.  \[**Inputs**\] の \[**Location**\] では、\[**Fill using**\] を
    \[**Dynamically fill with AI**\] のままにして、\[**Customize**\]
    を選択して説明を設定します。

![](./media/image21.png)

9.  以下のように説明を設定し、「**Save**」を選択します。

The location for the weather query. Valid inputs are City, State,
Country. Always include city and country, and state only for locations
where appropriate (e.g., in the US)

![](./media/image22.png)

![](./media/image23.png)

10. 次の複雑な質問で拡張エージェントをテストします。

> Who is the current CEO of the company that owns GitHub? Where did they
> earn their MBA? What's the average rent for a one-bedroom apartment
> near that campus? What's the air quality index in that area today?

![](./media/image24.png)

11. 生成オーケストレーションが複数の検索を実行し、天気コネクタをトリガーして包括的な回答を提供する方法に注目してください。

![](./media/image25.png)

## タスク3: AIアシスタントを微調整して会話をスムーズにする

システムトピックをカスタマイズして、インタラクションを強化し、よりスムーズなユーザーエクスペリエンスを実現します。

このセクションでは、組み込みのシステム
トピックをカスタマイズして、ユーザー
インタラクションを改善し、単なるナーレジソースを超えたよりシームレスなエクスペリエンスを実現します。

アシスタントのウェルカム
メッセージをカスタマイズして、より魅力的なものにし、ユーザーを効果的に誘導するための開始プロンプトの提案を追加し、エスカレーションなどのシステム
トピックを改良して組織のニーズに合うようにします。

1.  上部のメニューから「**Topics**」を選択します。

![](./media/image26.png)

2.  「**System**」の下にある「**Conversation
    Start**」トピックを選択します。

![](./media/image27.png)

3.  トピックの**Message**ノードに、以下のメッセージを入力します。

> Hi there! I'm Researcher agent, your intelligent assistant for deep
> research and discovery. I can break down complex questions and combine
> insights from historical facts, biographies, and real-time data like
> the weather. What are you curious about today?
>
> ![](./media/image28.png)

4.  同じノード内で、**+ Add** -\> **Quick reply**を選択します。

![](./media/image29.png)

5.  以下の質問を追加してください。

+++What caused the fall of the Roman Empire?+++

![](./media/image30.png)

6.  同様にさらに2つ追加します。

> +++Who is the current CEO of the company that owns GitHub? Where did
> they earn their MBA? What's the average rent for a one-bedroom
> apartment near that campus? What's the air quality index in that area
> today?+++
>
> +++What's the temperature in the city that hosted the last Olympic
> Games?+++

![](./media/image31.png)

7.  追加したら、「**Save**」を選択してトピックを保存します。

![](./media/image32.png)

8.  エスカレーションエクスペリエンスをカスタマイズします。**Topics** -\>
    **System** -\> **Escalate**を選択します。

![](./media/image33.png)

9.  エンドユーザーのブロックをより効果的に解除する以下のテキストを更新し、\[**Save**\]
    を選択します。

> I'm sorry, but I can't seem to be able to help you. I recommend
> reaching out to our \[Microsoft Copilot Studio community\]
> (https://aka.ms/CopilotStudioCommunity) or submitting a \[support
> request\]
> (<https://learn.microsoft.com/en-us/power-platform/admin/get-help-support>).

![](./media/image34.png)

## タスク4: エージェントを公開し、デモウェブサイトに公開する

このセクションでは、エージェントをパブリックにアクセス可能にするために、  
認証を削除し、テストと共有のためにデモ Web
サイトに公開します。Researcher
エージェントは一般的な情報を提供し、プライベートデータは処理しないため、  
シームレスなユーザー
エクスペリエンスを実現するために認証を無効にし、実際のサイトに展開する前にデモ
ウェブサイトに公開してフィードバックを収集します。

1.  \[**Settings**\]に移動します。

![](./media/image35.png)

2.  **Security** -\> **Authentication**を選択します。「**No
    authentication**」を選択し、「**Save**」を選択します。

![](./media/image36.png)

3.  確認プロンプトで \[**Save**\] を選択します。

![](./media/image37.png)

4.  これでSettingsペインを閉じることができます。

![](./media/image38.png)

5.  変更を有効にするには、「**Publish**」を選択します。

![](./media/image39.png)

6.  確認ダイアログで「**Publish**」を選択します。

![](./media/image40.png)

7.  公開が完了すると成功メッセージが表示されます。

![](./media/image41.png)

8.  次に、トップメニューから「**Channels**」を選択します。

![](./media/image42.png)

9.  利用可能なチャネルのリストから**Demo website**を選択します。

![](./media/image43.png)

10. ウェルカムメッセージに+++Welcome to your demo
    website+++と入力し、\[**Save**\] を選択します。

![](./media/image44.png)

11. 「**Open demo website**」をクリックしてサイトを開きます。

![](./media/image45.png)

12. これでエージェントと対話できるようになりました。

![](./media/image46.png)

## まとめ

このラボでは、以下のことをできる公共向けインテリジェント
エージェントを正常に提供しました。

- 複雑で複数の要素を含む研究課題に答えます。

- 検証済みの公開知識とリアル・タイムコネクタを使用します。

- 制御されたナーレジソースを通じて、ハルシネーションを最小限に  
  抑えます。

- 洗練されたユーザーフレンドリーな会話体験を提供します。

- ライブデモウェブサイトを通じて、展開およびアクセス可能。

このラボでは、単純な Q&A
を超えて、信頼性の高いリアル・タイムのコンテキスト認識型の分析情報を提供する、**本番環境対応のインテリジェント
エージェント**を設計、強化、公開する方法を説明します。
