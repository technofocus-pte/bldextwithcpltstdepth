# ラボ - Hiring Agentをスケーラブルなマルチエージェントアーキテクチャに変換する

前回のラボでは、メインのHiring
Agentを構築し、採用ワークフローを管理するための強固な基盤を構築しました。しかし、エージェント1つでできることには限界があります。

もしこの任務を引き受けるなら、その任務とは「**オペレーション・シンフォニー**」です。それは、単一のエージェントをマルチ・エージェントシステムへと変革すること。つまり、複雑な採用課題に対処するために連携して働く、専門エージェントからなる組織化されたチームを構築することです。これは、単独で活動するオペレーターから、専門部隊を指揮する立場へとステップアップするようなものだと考えてください。

まるで交響楽団のように、それぞれの演奏者が完璧なハーモニーを奏でるように、既存のHiring
Agentに2人の重要な専門家を加えます。履歴書を自動的に処理するApplication
Intake Agentと、包括的な面接資料を作成するInterview Prep
Agentです。これらのエージェントは、メインの指揮者のもと、シームレスに連携して機能します。

マルチ・エージェントを作成した後、エージェントは人間の入力を待つ状態から、外部イベントに積極的に反応し、監視なしでインテリジェントな行動をとるように変化します。

これは、質問に答えるだけのエージェントから、*ニーズを予測して自律的に行​​動する*エージェントへとアップグレードするようなものです。イベントトリガーと自動ワークフローを活用することで、Hiring
Agentは受信した履歴書メールを検知し、添付ファイルを自動的に処理し、データをDataverseに保存し、Microsoft
Teams経由で人事採用チームに通知します。それを実現できて、より付加価値の高い業務に集中できるのです。

## 目的

このミッションでは、次のことを学びます。

1.  **子エージェント**と**接続エージェント**を使用する場合

2.  スケーラブルな**マルチ・エージェントアーキテクチャ**の設計方法

3.  集中タスクのための**子エージェント**の作成

4.  エージェント間の**コミュニケーションパターン**の確立

5.  Application Intake AgentとInterview Prep Agentの構築

6.  イベントトリガーがユーザーの介入なしに自律的なエージェントの動作を可能にする仕組み

7.  Copilot Studio
    におけるインタラクティブエージェントと自律エージェントの違い

8.  メールの添付ファイルを自動的に処理し、ファイルを Dataverse
    にアップロードするイベントトリガーを作成する方法

9.  通知用にアダプティブ カードを Teams
    チャネルに投稿するエージェントフローを構築する方法

10. エンド・ツー・エンドの自動化のために、イベントトリガーとエージェントフロー間でデータを渡す方法

## 子エージェント: Application Intake Agent

マルチ・エージェント採用システムの構築を始めましょう。最初のスペシャリストは、**Application
Intake
Agent** です。これは、受信した履歴書と候補者情報の処理を担当する子エージェントです。

![](./media/image1.png)

**Application Intake Agentの責任**

- インタラクティブチャットを通じて提供されたPDFファイルから**履歴書の内容を解析します。**（今後の課題で、履歴書を自動的に処理する方法を学びます。）

- **Structured data** **を抽出します。**（名前、スキル、経験、学歴）

- 応募者の資格とカバーレターに基づいて、**募集中の職務に最適な候補者を  
  選定します。**

- **候補者の情報**を後で処理するためにDataverseに保存します。

- **応募書類の重複**を排除し、同じ候補者を二度登録しないようにします。履歴書から抽出したメールアドレスを使用して、既存の記録と照合します。

**なぜこれが子エージェントであるべきなのか**

Application Intake Agentは、次の理由により子エージェントとして最適です。

- 文書処理とデータ抽出に特化しています。

- 別途出版する必要はない。

- これは、同じチームが管理する、当社の総合的な採用ソリューションの一部です。

- これは特定のトリガー (新しい履歴書の受信) に焦点を当てており、Hiring
  Agentから呼び出されます。

## 接続エージェント: Interview Prep Agent

2
番目のスペシャリストは、包括的な面接資料の作成と候補者の応答の評価を支援する、コネクテッド
エージェントであるInterview Prep Agentです。

Interview Prep Agent**の責任**

- 企業情報、職務要件、評価基準などを記載した**面接資料を作成します。**

- • 特定の職務や候補者の経歴に合わせて**面接質問を作成します。**

- •
  関係者とのコミュニケーションのために、職務内容や応募に関する**一般的な質問に回答します。**

**なぜこれがコネクテッドエージェントであるべきなのか。**

Interview Prep
Agentは、接続エージェントとしての方が効果的に機能します。その理由は次のとおりです。　

- 人材獲得チームは、複数の採用プロセスで独立してこれを使用したい場合があります。

- 面接のベストプラクティスと評価基準に関する独自の知識ベースが必要であります。

- 採用マネージャーによっては、チームごとに動作をカスタマイズしたい場合もあります。

- 外部採用だけでなく、社内ポジションにも再利用できます。

## 演習 1 - Application Intake Agentの追加

最初の子エージェントを既存のHiring Agentに追加しましょう。

### タスク1 - ソリューションのセットアップ

1.  Copilot Studio 内で、左側のナビゲーションの \[Tools\] の下の省略記号
    (...) を選択します。

2.  **Solutions**を選択します。

> ![](./media/image2.png)

3.  **Operative**ソリューションを見つけ、その横にある省**略記号（...）**を選択し、「**Set
    preferred
    solution**」を選択します。ポップアップ表示されるダイアログボックスで「**Apply** 」を選択します。これにより、すべての作業がこのソリューションに追加されます。

> ![](./media/image3.png)

4.  \[Set your preferred solution\] ダイアログ ボックスで \[Apply\]
    を選択します。

![](./media/image4.png)

### タスク2 - Hiring Agentの指示を設定する

1.  Copilot Studio へ**移動します**。右上の**Environment
    Picker**で環境が選択されていることを確認してください。

2.  **Hiring Agent**を開きます。

3.  エージェントの \[**Overview** \] タブの \[**Instructions** \]
    セクションで \[**Edit** \] を選択します。

![](./media/image5.png)

4.  以下の手順をコピーして、手順入力欄に貼り付けます。

**You are the central orchestrator for the hiring process. You
coordinate activities, provide summaries, and delegate work to
specialized agents.**

5.  \[**Save**\]を選択します。

> ![](./media/image6.png)

6.  画面の右上にある「**Settings** 」ボタンを選択します。

> ![](./media/image7.png)

7.  ページを確認し、次の設定が適用されていることを確認してから、\[**Save**\]
    を選択します。

[TABLE]

> ![](./media/image8.png)
>
> ![](./media/image9.png)
>
> ![](./media/image10.png)
>
> ![](./media/image11.png)

8.  設定メニューを閉じるには、右上隅の**X** をクリックします。

> ![](./media/image12.png)

### タスク3 - Application Intake子エージェントを追加する

このタスクでは、Hiring Agentに子エージェントを追加します。

1.  Hiring Agent内の**Agents** タブ (ここで専門エージェントを追加します)
    に**移動し**、\[**Add**\] を選択します。

![](./media/image13.png)

2.  **New child agent**を選択します。

![](./media/image14.png)

3.  エージェントの**名前**を+++ Application Intake Agent
    +++ト入力します。

4.  「**When will this be
    used?** 」ドロップダウンの説明に基づいて「**The agent
    chooses** 」を選択します。これらのオプションは、トピックに設定できるトリガーと似ています。　

5.  **Description** を次のように設定します - +++ Processes incoming
    resumes and stores candidates in the system +++

![](./media/image15.png)

6.  「**Advanced**」を展開し、「Priority」を「10000」に設定します。これにより、この質問の前に、Interview
    Agentが一般的な質問に回答するようになります。ここで、少なくとも1つの添付ファイルがあることを確認するなどの条件を設定することもできます。　

![](./media/image16.png)

7.  **Web
    Search**トグルが**Disabledに** 設定されていることを確認します、親エージェントから提供された情報のみを使用するためです。**Save**を選択します。

![](./media/image17.png)

### タスク4 - 履歴書アップロードエージェントフローを構成する

エージェントは、ツールやトピックが提供されなければ、アクションを実行できません。

*履歴書アップロード*のステップでは、トピックではなく**Agent Flow
tools** を使用しています。これは、この複数ステップからなるバックエンド処理には、確実な実行と外部システムとの連携が必要となるためです。トピックは会話型ダイアログを誘導するのに最適ですが、Agent
Flowsは、ユーザーの操作に依存することなく、ファイル処理、データ検証、およびデータベースへのアップサート（新規挿入または既存データの更新）を確実に処理するために必要な構造化された自動化機能を提供します。

1.  Application Intake Agent
    ページ内の**Tools** セクションを見つけます。

> **重要：**これは親エージェントの \[Tools\]
> タブではありませんが、子エージェントの説明の下までスクロールすると見つかります。

2.  **+ Add**を選択します。

> ![](./media/image18.png)

3.  **+ New tool**を選択します。

> ![](./media/image19.png)

4.  **Agent flow**を選択します。**Agent
    flow**デザイナーが開きます。ここに履歴書アップロードのロジックを追加します。  
    ![](./media/image20.png)

5.  **When an agent calls the flow** ノードを選択し、**+ Add an
    input**を選択します。

> ![](./media/image21.png)

6.  以下の表に記載されている各**パラメータ**に**入力情報**を追加してください。表に示されている適切な入力タイプを選択し、名前と説明の両方を必ず追加してください。エージェントが入力内容を理解できるように、説明を必ず含めることが重要です。

[TABLE]

> ![](./media/image22.png)

7.  エージェントがフロー ノードを呼び出したときの下にある **+
    アイコン**を選択し、+++Dataverse add+++を検索して、**Microsoft
    Dataverse** セクションで \[**Add a new row** \]
    アクションを選択します。

> ![](./media/image23.png)
>
> ![](./media/image24.png)

**注記**

アクションを追加した後、Dataverseに新しい接続を作成するように求められる場合があります。接続名を入力し、addをクリックして接続を作成してください。

8.  3 つのドットを選択し、\[**Rename**\] を選択して、ノードに
    +++**Create Resume**+++ という名前を付けます。

> ![](./media/image25.png)

9.  **Table name** を **Resumes** に設定し、\[**Show all**\]
    を選択して、すべてのパラメータを表示します。

> ![](./media/image26.png)

10. 次のプロパティを設定します。

[TABLE]

> ![](./media/image27.png)
>
> ![](./media/image28.png)
>
> ![](./media/image29.png)

11. 「Create Resume」ノードの下の **+ アイコン**を選択し、+++Dataverse
    upload+++を検索して、「**Upload a file or an
    image** 」アクションを選択します。

![](./media/image30.png)

12. ノードに +++**Upload Resume File**+++ という名前を付けます。

> ![](./media/image31.png)

13. 次のプロパティを設定します。

[TABLE]

> ![](./media/image32.png)

14. 「**Respond to the agent**」ノードを選択し、「**+ Add an
    output**」を選択します。以下の表に定義されているプロパティを使用して出力を作成します。

> ![](./media/image33.png)

[TABLE]

> ![](./media/image34.png)

15. 右上の「**Save draft** 」を選択します

> ![](./media/image35.png)

16. 「**Overview** 」タブを選択し、「**Details** 」パネルで「**Edit** 」を選択します。以下のように名前と説明を入力し、「**Save**」を選択します。

    1.  **Flow name**:+++Resume Upload+++

    2.  **Description**:+++Uploads a Resume when instructed+++

> ![](./media/image36.png)

17. もう一度 \[**Designer** \] タブを選択し、\[**Publish**開\]
    を選択します。

> ![](./media/image37.png)

### タスク5 - フローをエージェントに接続する

次に、公開されたフローをApplication Intake Agentに接続します。

1.  **Hiring Agent**に戻り、「**Agents** 」タブを選択します。Application
    Intake
    Agentを開き、「**Tools** 」パネルで「**+Add**」を選択します。  
    ![](./media/image38.png)

2.  **Flow**  フィルターを選択し、**Resume Upload** フローを選択します。

> ![](./media/image39.png)

3.  \[**Add and configure**\]を選択します。

> ![](./media/image40.png)

4.  説明とツールを使用するタイミングについて、次のパラメータを設定します。

[TABLE]

> ![](./media/image41.png)
>
> **注記：**この説明は、エージェントに、このツールをいつ呼び出すかを指示します。説明で「strict
> rule」が使用されていることに注目してください。これは、ツールをいつ使用すべきかについての追加のガードレールを提供する手段となります。この場合は、添付ファイルがあり、会話のコンテキストが履歴書のアップロードである場合にのみ、ツールを使用します。このツールをいつ使用できるかを選択することも重要です。マルチエージェントシステムを構築しており、子エージェントが存在するため、このツールはメインエージェントではなく、子エージェントで**のみ**呼び出されるようにする必要があります。値を「only
> when referenced by topics or
> agents」に設定することで、これを実現できます。

5.  入力セクションまで下にスクロールし、「**Add
    Input** 」を選択して次の入力を追加します。

[TABLE]

> ![](./media/image42.png)

6.  次に、入力のプロパティを設定します。まずは、履歴書ファイルを保存する**contentBytes**入力から始めましょう。**contentBytes**入力の横にある「**Fill
    using**」ドロップダウンから「**Custom
    value**」を選択します。「Value」プロパティでは、**3つのドット（...）**を選択します。

> ![](./media/image43.png)

7.  「**Formula** 」タブを選択します。チャットからファイルを抽出する次の数式を貼り付け、「**Insert** 」ボタンをクリックします。

+++First(System.Activity.Attachments).Content+++

> ![](./media/image44.png)

8.  次に、履歴書ファイル名を保存する**名前**入力を設定します。これもハードコードされるため、「**Fill
    using** 」列で「**Custom value** 」オプションを選択してください。

9.  \[**Value** \] 列の **3 つのドット (...)**
    を選択し、チャットからファイル名を抽出する次の数式を貼り付けて、\[**Insert** \]
    ボタンをクリックします。

+++First(System.Activity.Attachments).Name+++

> ![](./media/image45.png)

10. 次に、**Message** 入力の設定を行います。この入力はAIを使って動的に入力したいので、fill
    using
    はそのままにしておきます。「**Value** 」列の「**Customize** 」ボタンを選択して、入力方法の詳細を入力します。　

![](./media/image46.png)

11. 入力欄の「**Description** 」フィールドに以下を入力します。「**Advanced**」を選択します。

**Extract a cover letter style message from the context. Be sure to
never prompt the user and create at least a minimal cover letter from
the available context. STRICT RULE - the message must be less than 2000
characters.**

**注記**

動的に入力される入力の説明を入力することは、エージェントが入力を正しく入力する方法を認識できるようにするための重要なステップです。

> ![](./media/image47.png)

12. **Advanced** セクションを展開して、この入力に関する追加のプロパティを設定します。**How
    many reprompts**セクションで、「**Don't repeat**」を選択します。

> ![](./media/image48.png)

**注記**

この設定により、エージェントが必要なデータを識別できない場合に同じ質問を何度も繰り返さないように、ユーザー
エクスペリエンスをカスタマイズできます。

13. 「**No valid entity
    found** 」セクションまでスクロールダウンします。「**Action if no
    entity found** 」ドロップダウンで「**Set variable to
    value** 」オプションを選択します。「**Default entity
    value** 」入力欄に+++ Resume upload +++と入力します。

> ![](./media/image49.png)
>
> **注記**
>
> この設定により、エージェントがこのメッセージ入力を動的に入力できない場合に、バックアップ値をハードコードできます。

14. 「**Fill using** 」列で「**Custom
    value** 」オプションを選択し、「**Value** 」列で **3 つのドット
    (...)** を選択して、**UserEmail** 入力を入力します。

> ![](./media/image50.png)

15. **System** タブを選択し、**User**を検索します。**User.Email**変数を選択して、エージェントを使用しているユーザーのメールアドレスを取得します。

> ![](./media/image51.png)

16. **Save**を選択します。

> ![](./media/image52.png)

### タスク6 - エージェントの指示を定義する

このタスクでは、Application Intake agentのエージェント指示を定義します。

1.  \[**Agents** \] タブを選択し、\[**Application Intake Agent**\]
    を選択して、**Application Intake Agent**に戻ります。

> ![](./media/image53.png)

2.  「**Instructions** 」フィールドに、子エージェント向けの次の明確なガイダンスを貼り付けます。

> You are tasked with managing incoming Resumes, Candidate information,
> and creating Job Applications.
>
> Only use tools if the step exactly matches the defined process.
> Otherwise, indicate you cannot help.
>
> Process for Resume Upload via Chat
>
> 1. Upload Resume
>
> - Trigger only if /System.Activity.Attachments contains exactly one
> new resume.
>
> - If more than one file, instruct the user to upload one at a time and
> stop.
>
> - Call /Upload Resume once. Never upload more than once for the same
> message.
>
> 2. Post-Upload
>
> - Always output the \[ResumeNumber\] (R#####).
>
> 。
>
> ![](./media/image54.png)

3.  指示にスラッシュ（/）が含まれている場合は、/に続くテキストを選択し、解決された名前を選択します。

    - System.Activity.Attachments (Variable)

    - Upload Resume (Tool)

> 注:
> 手順内のSystem.Acticvity.Attachementsをクリックすると、解決された名前が表示されます。これを選択してください。選択後、既存のテキストの一部が残っている場合は削除してください。　
>
> ![](./media/image55.png)
>
> ![](./media/image56.png)

4.  手順は次のようになります。

> ![](./media/image57.png)

5.  \[**Save**\]を選択します。

> ![](./media/image58.png)

### タスク 7 - Application Intake Agentをテストする

次に、子エージェントを呼び出して指示に従い、エージェントが正しく動作していることを確認しましょう。

1.  **「Test」**を選択して、テストパネルを開閉します。

> ![](./media/image59.png)

2.  添付ファイルアイコンを選択し、履歴書 – AVERY EXAMPLE pdf
    を選択して、「**Open**」をクリックします。

> ![](./media/image60.png)

3.  「+++ Process these resumes
    +++」というメッセージを入力し、「**送信**」をクリックします。

> ![](./media/image61.png)

4.  エージェントは「**The resume for Avery Example has been successfully
    uploaded. The resume number is
    R1001**」のようなメッセージを表示します。

> ![](./media/image62.png)

5.  **Activity map**には、履歴書のアップロードを処理する**Application
    Intake Agent**が表示されます。

> ![](./media/image63.png)

6.  アプリがまだ開いていない場合は、+++make.powerapps.com+++
    にアクセスしてください。右上のEnvironment Pickerで Dev One
    環境が選択されていることを確認してください。「**Apps** 」→「Hiring
    Hub」→省略記号(...)メニュー→「**Play**」を選択してください。  
    ![](./media/image64.png)

**注記：**再生ボタンがグレー表示になっている場合は、ソリューションがまだ公開されていないことを意味します。**Solutions** → **Publish
all customizations**を選択してください。

7.  Power Apps – Hiring Hub アプリで、\[**Resumes**\]
    に移動し、履歴書ファイルがアップロードされ、カバー
    レターがそれに応じて設定されていることを確認します。

> ![](./media/image65.png)

## 演習2: 面接準備接続エージェントの追加

次に、面接準備用の接続エージェントを作成し、既存のHiring
Agentに追加しましょう。

### タスク 1: 接続されたInterview Agentを作成する

1.  Copilot Studio の左側のナビゲーションで \[**Agents** \]
    タブを選択し、\[+ **Create blank agent**\]
    の横にある**ドロップダウン**を選択して、\[**Advanced create**\]
    を選択します。

> ![](./media/image66.png)

2.  **Solution**として「**Operative**」を選択し、「**Confirm and
    create**」を選択します。

> ![](./media/image67.png)

3.  Detailsに対して**Edit**を選択します。

> ![](./media/image68.png)

4.  以下の詳細を入力し、「**Save**」を選択します。

    - **Name**: +++Interview Agent+++

    - **Description**: +++Assists with the interview process.+++

> ![](./media/image69.png)

5.  \[**Instructions**\] に対して \[**Edit**\]
    を選択し、以下の手順を入力して \[**Save**\] を選択します。

> You are the Interview Agent. You help interviewers and hiring managers
> prepare for interviews. You never contact candidates.
>
> Use Knowledge to help with interview preparation.
>
> The only valid identifiers are:
>
> - ResumeNumber (ppa_resumenumber)→ format R#####
>
> - CandidateNumber (ppa_candidatenumber)→ format C#####
>
> - ApplicationNumber (ppa_applicationnumber)→ format A#####
>
> - JobRoleNumber (ppa_jobrolenumber)→ format J#####
>
> Examples you handle
>
> - Give me a summary of ...
>
> - Help me prepare to interview candidates for the Power Platform
> Developer role
>
> - Create interview assistance for the candidates for Power Platform
> Developer
>
> - Give targeted questions for Candidate Alex Johnson focusing on the
> criteria for the Job Application
>
> How to work:
>
> You are expected to ask clarification questions if required
> information for queries is not provided
>
> - If asked for interview help without providing a job role, ask for it
>
> - If asking for interview questions, ask for the candidate and job
> role if not provided.
>
> General behavior
>
> - Do not invent or guess facts
>
> - Be concise, professional, and evidence-based
>
> - Map strengths and risks to the highest-weight criteria
>
> - If data is missing (e.g., no resume), state what is missing and ask
> for clarification
>
> - Never address or message a candidate
>
> ![](./media/image70.png)

6.  **Web
    Search** は**Disabled**に設定されていることを確認してください。

> ![](./media/image71.png)

### タスク2: データアクセスを構成し、公開する

このタスクでは、データへのアクセスを構成し、エージェントを公開します。

1.  **Knowledge** セクションで、**+ Add knowledge**を選択します。

> ![](./media/image72.png)

2.  **Dataverse**を選択します。  
    ![](./media/image73.png)

3.  **検索ボックス**に「+++ppa\_+++」と入力します。これは、前のラボでインポートしたテーブルのプレフィックスです。

4.  5つのテーブルすべて（Candidate, Evaluation Criteria, Job
    Application, Job Role, Resume）**選択します**。「**Add to
    agent**」を選択します。

> ![](./media/image74.png)

5.  右上隅にある**Settings** ボタンを選択します

> ![](./media/image75.png)

6.  次の設定が構成されていることを確認してください。

    - **Let other agents connect to and use this one:** On

    - **Use general knowledge**: Off

    - **File uploads**: Off

    - **Content moderation level:** Medium

> ![](./media/image76.png)
>
> ![](./media/image77.png)
>
> ![](./media/image78.png)

7.  \[**Save** \] を選択し、右上隅の
    **Publish**を選択して設定メニューを閉じます。

> ![](./media/image79.png)

8.  \[**Publish**\]を選択します。

> ![](./media/image80.png)

9.  確認ダイアログで「**Publish**」を選択し、公開が完了するまで待ちます。

![](./media/image81.png)

### タスク3: Interview Prep AgentをHiring Agentに接続する

このタスクでは、Interview Prep AgentをHiring
Agentに接続して、マルチ・エージェント
オーケストレーションを実現します。　

1.  **Hiring Agent**の画面に戻り、「**Agents** 」タブを選択し、「+ **Add
    an agent**」を選択します。

> ![](./media/image82.png)

2.  **Interview Agent**を選択します。

> ![](./media/image83.png)
>
> **注記**
>
> Interview
> Agentがグレー表示になっていて、選択できない場合は、公開されていないことを意味します。Interview
> Agentに戻って、まず公開してください。

3.  **Description**を次のように設定します。

> Assists with the interview process and provides information about
> Resumes, Candidates, Job Roles, and Evaluation Criteria.
>
> 「Pass conversation history to this
> agent」にチェックが入っていることをご確認ください。これにより、親エージェントは接続中のエージェントに完全なコンテキストを提供できるようになります。　
>
> \[**Add and configure**\]を選択します。

![](./media/image84.png)

4.  **Application Intake Agent**と**Interview
    Agent**の両方が表示されていることを確認してください。一方が子エージェントで、もう一方が接続エージェントであることにご注意ください。　

> ![](./media/image85.png)
>
> ![](./media/image86.png)

### タスク4: マルチ・エージェントコラボレーションのテスト

1.  **「テスト」**を選択して、テストパネルを開閉します。

2.  テスト用の履歴書ファイルを**アップロードし**、親エージェントが接続されたエージェントに何を委任できるかを伝える以下の説明を入力してください。

> Upload this resume, then show me open job roles, each with a
> description of the evaluation criteria, then use this to match the
> resume to at least one suitable job role even if not a perfect match.
>
> ![](./media/image87.png)

3.  Hiring
    Agentがアップロードを子エージェントに委任し、その後、Interview
    Agentにその知識を使用して概要と職務の一致を提供するように依頼した点に注目してください。　

> ![](./media/image88.png)

4.  履歴書、職務内容、評価基準について、様々な質問方法を試してみましょう。例：

> ++++++Give me a summary of active resumes+++
>
> +++Summarize resume R1006+++
>
> +++Which active resumes are suitable for the Power Platform Developer
> role?+++

## まとめ

単一のHiring
Agentを、特殊な機能を備えた洗練されたマルチ・エージェントのオーケストレーションに正常に変換しました。

このラボで達成した成果は次のとおりです。

**マルチ・エージェントアーキテクチャの習得**  
これで、子エージェントと接続エージェントをいつ使用するか、またスケーラブルなシステムを設計する方法がわかりました。

**Application Intake子エージェント**  
履歴書を処理し、候補者データを抽出し、Dataverse
に情報を保存する特殊な子エージェントをHiring Agentに追加しました。　

**Interview Prepコネクテッドエージェント**  
面接準備用の再利用可能な接続エージェントを構築し、それをHiring
Agentに正常に接続しました。　

**エージェント通信**  
メインエージェントが専門エージェントと連携し、コンテキストを共有し、複雑なワークフローを調整する方法について学びました。

**自律のための基盤**  
強化された採用システムは、今後のミッションで追加される高度な機能（自律トリガー、コンテンツ
モデレーション、および深い推論）に対応できるようになりました。
