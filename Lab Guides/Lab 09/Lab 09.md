
# ラボ 09 - クイズ生成エージェントのトピックにプロンプ​​トアクションを実装する

## 手順 1: 自然言語を使用してエージェントを作成する

1.  ブラウザを開いて +++https://copilotstudio.microsoft.com/+++
    にログインし、\[リソース\] タブの資格情報でログインします
    (まだそのページが表示されていない場合)。.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  すでにCopilot
    Studioページが表示されている場合は、\[**Home**\]をクリックして
    ホームページに移動します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  ホームページの「エージェントの説明」のテキストエリアに「+++I want
    you to be a question and answering assistant that can answer common
    questions from users using the content of a
    website+++」を入力し、「Send」をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

1.  エージェントの名前が提案される場合があります。それを受け入れるか、自分の名前を入力する。

&nbsp;

4.  エージェントの機能に関するその他の詳細を以下のように提供する。

+++help answer common product and support questions using the content of
a website, and help answer HR questions from an uploaded file+++

5.  ナレッジソースを使用する Web サイトに +++www.microsoft.com+++
    を提供します。

![A screenshot of a chat Description automatically
generated](./media/image4.png)

1.  指示の入力が完了したら、\[**Create**\]をクリックして
    エージェントを作成します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image5.png)

6.  エージェントが作成され、詳細が表示されます。ページをスクロールして、エージェントが指定した手順で作成されたことを確認する。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

7.  \[**Test\]**
    アイコンをクリックして、エージェントをテストします。「+++Copilot
    Studioとは？+++」と入力し、**Enter**キークリックする。

![A screenshot of a phone Description automatically
generated](./media/image8.png)

8.  +++What is the latest xbox model?+++を入力する。

![A screenshot of a chat Description automatically
generated](./media/image9.png)

上記の両方の手順で、エージェントが一般的な知識を使用するため、エージェントから一般的な回答が受け取ります。

## 手順 2: 生成的な回答のためのトピックのプロンプトアクションを作成する

アクションを使用して、エージェントの機能を拡張できます。Microsoft
Copilot Studio では、複数の種類のアクションをエージェントに追加できます:

- 事前構築されたコネクタ アクションが**Power Platform**
  コネクタを使用して、**Salesforce、Zendesk、MailChimp、GitHub**
  などの一般的なエンタープライズ製品などのよう他のシステムからデータにアクセスします。.

- **カスタム コネクタ アクション** は、パブリック API またはプライベート
  API からデータにアクセスするようにコネクタを構築できます。

- **Power Automate クラウド フロー**はPower Automate クラウド
  フローを使用して、アクションの実行、データの取得、および操作を行います.

- **AI ビルダープロンプト**は、AI
  ビルダーと自然言語理解を使用して、ビジネス内の特定のシナリオとワークフローをターゲットにします**。**

- **Bot Framework
  スキル**は、スキルの入力および出力パラメーター、スキルのエンドポイント、スキルのディスパッチ
  モデルなど、スキルが実行できるアクションの概要を示すスキル
  マニフェストを使用します**。**

この手順では、トピックノードにアクションプロンプトを追加する方法を学習します。

1.  エージェントで**Topics**を選択し、**+Add a topic**を選択して**From
    blank**選択します.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

2.  Topic名を「+++Generate questions for a
    quiz+++」と入力します。トリガーの「Phrases」の下にある「Edit」のハイパーリンクを選択する。トリガーフレーズは最低5つ入力する必要があります。

以下のフレーズを1つずつ追加します。各フレーズを追加し、 \[+\]
オプションを選択してトリガーを追加します。

> +++create a number of questions for a quiz based on a topic and format
> the quiz based on the instruction provided+++
>
> +++creates a quiz with a number of questions based on the topic
> provided and formats the quiz+++
>
> +++generate a quiz with a number of questions using the topic provide
> and format the questions+++
>
> +++creates questions for a quiz on a specific topic and format+++
>
> +++format a quiz by a number of questions based on the topic
> provided+++

右上の \[**Save\]** を選択して 、トピックを保存します。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  トリガーノードの下にある+記号をクリックします。「**Add an
    action**」オプションを選択し、その下の「**New
    prompt（デフォルトのAIモデル）**」オプションを選択します。

![A screenshot of a quiz AI-generated content may be
incorrect.](./media/image12.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

4.  Prompt」ダイアログが表示され、プロンプトの作成方法を案内するポップアップが表示される場合があります。「**Next**」を選択してガイドに伴います。

5.  クイズの質問を生成するプロンプトを作成します。プロンプトの名前を「+++Quiz
    Generator+++」と入力する。

6.  以下の内容を「Prompt」フィールドに貼り付けます。

+++Generate a quiz with \[number\] questions to cover this \[topic\].
Decide on the format, such as multiple-choice questions or true/false
statements. Use this \[format\]. Designate the correct answer within
parentheses.+++

\[**入力**\] セクションを拡張し、\[**+ 入力の追加\]** を選択します。

**注:**
入力セクションが表示されていない場合は、下にスクロールして表示する。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

7.  **Add input**オプションの下に**Text**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

8.  Enter the name as +++number+++ and enter sample data such as
    +++5+++. Select **+ Add input** -\> **Text** to add the next input.
    名前を +++number+++ として入力し、+++5+++ などのサンプル
    データを入力します。**\[+ Add input-\> Text**\]
    を選択して、次の入力を追加します。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

9.  名前を +++topic+++ として入力し、+++Science+++ などのサンプル
    データを入力してから、 **\[+ 入力を追加** -\> **テキスト** \]
    を選択して次の入力を追加します。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

1.  名前を+++format+++として入力し、+++箇条書きポイント+++などのサンプルデータを入力します

![A screenshot of a computer Description automatically
generated](./media/image18.png)

10. これで、入力名とサンプルデータが追加されました。次に、入力をプロンプトに挿入する必要があります。プロンプトで
    **\[Number\]** を強調表示し、\[**+ Add**\] を選択し、**\[
    プロンプト内\]** タブでNumberを選択します。これで、number
    の入力が入力としてプロンプトに追加されました。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image20.png)

11. 残りの入力についても同じ手順を繰り返します。

12. すべての入力がプロンプトに追加されたら、\[**Test prompt**\]
    をクリックし、プロンプトの応答を確認します。

![A screenshot of a quiz generator Description automatically
generated](./media/image21.png)

13. \[Save**\]** を選択**して** プロンプトを保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

1.  プロンプトアクションノードがトピックのオーサリングキャンバスに表示されます。次に、エージェントが入力するために、入力パラメータの値を定義する必要があります。**\>**アイコンを選択します

![A screenshot of a quiz Description automatically
generated](./media/image24.png)

14. \[システム\] タブを選択し、アクションの入力値として
    \[Activity.Text\]
    を選択して、ユーザーの応答全体を使用し、形式の値を識別します。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

15. プロンプト・アクションの残りの入力パラメータについても同じ手順を繰り返します。

![A screenshot of a quiz Description automatically
generated](./media/image26.png)

16. 次に、プロンプトアクションの出力変数を定義する必要があります。これは、応答をトピックの下流で参照できるようにするためです。**\>**アイコンを選択し、\[**カスタム**\]
    タブで \[**新規作成**\]
    を選択し、変数に+++**VarQuizQuestionsResponse+++**名前を付けます。

![A screenshot of a quiz AI-generated content may be
incorrect.](./media/image27.png)

> ![A screenshot of a browser window Description automatically
> generated](./media/image28.png)

17. プロンプト アクションの下にある **+**
    アイコンを選択して新しいノードを追加し、**Send a
    message**を選択します。**{x}** 変数アイコンを選択します。

![A screenshot of a quiz Description automatically
generated](./media/image29.png)

18. **VarQuizQuestionsResponse.text**変数を選択する**。**これにより、プロンプト・アクション応答のテキスト・プロパティがSend
    a messageノードに追加されます. \[**Save\]** を選択して
    トピックを保存します。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

19. 次に、ジェネレーティブモードが有効になっているときに、エージェントがトピックをユーザーのインテントに関連付けるために使用するトピックの詳細を更新する必要があります。

Select **Details**を選択して以下の詳細を入力する**。**

- Display name - +++ generate questions for a quiz+++

- Description - +++ This topic creates questions for a quiz based on the
  number of questions, the topic and format provided by the user+++

\[**Save\]** を選択**して**トピックを保存します。

> ![A screenshot of a quiz Description automatically
> generated](./media/image31.png)

20. 次に、 エージェントがプロンプト
    アクションでトピックを呼び出すには、**ジェネレーティブ
    モード**設定を有効にする必要があります。エージェントの
    \[**Settings**\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

21. **Generative AI**設定を選択して**、** **Generate
    (preview)**を選択し **Save**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

22. これで、エージェントをテストする準備が整いました。 \[**Settings\]
    ウ**ィンドウ を閉じます。テスト
    ウィンドウで、**Refresh**アイコンを選択します。次に、次の質問を入力して、出力を観察します.

+++Create 5 questions for a quiz based on geography and format the quiz
as multi choice+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

> ![A screenshot of a cell phone Description automatically
> generated](./media/image35.png)

要約

このラボでは、カスタム
プロンプトを作成してテストすることで、トピックのプロンプト
アクションを作成する方法を学習しました。
