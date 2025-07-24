# ラボ 04 - エージェントを Dynamics 365 Customer Service アプリに統合し、ライブエージェントへの自動ケースエスカレーションを実装する

## 客観的

このラボでは、エージェントからライブエージェントに会話をエスカレートする手順について詳しく説明します。

\[!Alert \]**重要:このラボは、ラボ 02 - Dynamics 365 Customer Service
を構成 する**に従って Dynamics 365
試用版が有効になっている場合にのみ実行できます。

## 演習 1: Dynamics 365 Customer Service ワークスペースを構成する

### タスク 1: Omnichannel Power Virtual Agent 拡張機能を構成する

1.  リンク +++
    [https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++を開き、](https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++)
    Omnichannel Power Virtual Agent Extension ページで \[**Get it
    now\]**をクリックします。

![](./media/image1.png)

2.  **\[Resources\]**タブからテナント資格情報を使用してサインインします。

![](./media/image2.png)

3.  **「Get it now」**をクリックします。

![](./media/image3.png)

4.  **「Select an environment」**で**CustomerService
    Trial**を選択し、チェック ボックスをオンにして、
    **「Install」をクリックします**。

![](./media/image4.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

## タスク 2: Power Platform admin centerで検索設定を構成する

1.  テナントの詳細を使用して、 +++
    [https://admin.powerplatform.microsoft.com/+++にログインします。](https://admin.powerplatform.microsoft.com/+++)左側のペインで**「Manage」**を選択し、環境リストから**「CustomerService
    Trial」環境を選択します。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  上部のペインから**\[Settings\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  **Product -\> Features**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  **Dataverse Search**と**Single table
    search**オプションを**Onに**切り替えて、 **Save**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

## 演習2: エージェントを作成する

1.  Copilot Studio のホームページ (+++
    [https://copilotstudio.microsoft.com+++ )
    で](https://copilotstudio.microsoft.com+++/)、右上にある**CustomerService
    Trial**環境を選択します。

![](./media/image10.png)

2.  左ペインから**「Agents」**を選択します。「**+ New
    Agent** **」**をクリックして 新しいエージェントを作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  「Type your message」テキスト領域に、「+++ **You are a customer
    service agent who helps in identifying stores
    nearby**+++」と入力し、 **「Send」**をクリックします。

![](./media/image12.png)

4.  エージェントは、作成するエージェントの**名前**を提案する場合があります。その名前を受け入れるか、新しい名前を提案してください。

5.  メッセージを入力し、「+++ **Maintain a polite tone** +++
    次に\[**Send」**を クリックします。

![](./media/image13.png)

6.  **「Create」**をクリックします。

![](./media/image14.png)

7.  作成されたエージェントが開き、**「Your agent is
    ready」**というメッセージが表示されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## 演習3: CopilotをDynamics 365 Customer Serviceに接続し、 エスカレートトピックを構成する

### タスク 1: エスカレート・トピックを構成する

ここでは、ライブエージェントへのエスカレーションというコンセプトを紹介することに焦点を当てています。そのため、他の新しいトピックを作成せずに、直接　　そのコンセプトに取り組んでいきます。

1.  **「Topics」**タブを選択し、 **「System」**タブを選択します。
    **「Escalate」** トピックを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  トピックのメッセージノードを選択し、既存のコンテンツを次のように
    置き換えます。+++ You will be transferred to a live agent shortly
    +++

![](./media/image17.png)

3.  \+ 記号をクリックして、メッセージ ノードの横にノードを追加します。

4.  **Topic management** -\> **Transfer conversation**を選択します。

![](./media/image18.png)

5.  会話転送ノードで、「+++The customer wants to talk to a live
    agent+++」というメッセージを送信します。

![ ](./media/image19.png)

6.  トピックを**Save**します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  エージェントを**Publish**します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### タスク 2: Copilotを Dynamics 365 Customer Service に接続する

1.  公開したら、Copilot
    ページの右上にある**\[Settings\]**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  **\[Security\]**を選択し、 \[Security\] の下の**\[Authentication\]**
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  **「No authentication」オプション**を選択し、
    **「Save」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  確認ダイアログボックスで**「Save」**を選択します。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  **Settings**パネルを閉じます。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image26.png)

6.  **Channels**をクリックします（チャンネルが表示されない場合は、+1を
    クリックして**Channels**オプションを表示します）

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  顧客エンゲージメント・ハブ・ペインから**Dynamics 365 Customer
    Service**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  Dynamics 365 Customer Service ページで、
    **\[Connect\]**をクリックします。

![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  **successfully connected** を示すメッセージが表示されたら、
    **「Close」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## 演習 4: Dynamics 365 admin centerでワークストリームと チャネルを作成する

### タスク 1: 顧客サービス向けOmnichannelでユーザーを管理する

1.  管理者テナントの資格情報を使用して、 +++
    [https://admin.powerplatform.microsoft.com+++](https://admin.powerplatform.microsoft.com+++/)にログインします。左ペインから**「Manage」**を選択
    します。 「**Environments**」から「**CustomerService
    Trial**」環境を選択 します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  **Environment URL**の下の**URLバリュー**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  ヘッダー・バーから**Customer Service workspace**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  **Appsページ**が開きます。そこから**「Customer Service admin
    center** **」**を 選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  これにより、 **Dynamics 365 Customer Service admin centerページ**が
    開きます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

### タスク2: ワークストリームを構成する

1.  Admin centerのページで、左側のペインから**\[Customer
    support** **\]**の下にある**\[Workstreams\]**を選択し、 **\[+New
    workstream** **\]**オプションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

2.  Inboundを選択します。

![](./media/image37.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

3.  以下の詳細を入力し、下にスクロールして**「Create」**をクリックします。

    - Name - +++ **New Workstream** +++

    - Owner – **MOD Administrator** （デフォルトで選択）

    - Type – **Messaging**

> Channel –**Chat**![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image39.png)

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  ワークストリームが作成されたら、 **「Set up
    chat** **」**をクリックして チャット・チャネルを設定します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  **Live chat setup – Channel
    details** **画面**で、以下の詳細を入力します。

    - Name - +++ **Chat Channel** +++

    - Language – **English - United States**

![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  下にスクロールして**「Next」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  次の2ページでは、Chat
    widget画面が表示されるまでデフォルト設定をそのままにしておきます。Live
    chat setup - チャットウィジェット画面で、 名前を「+++ **Store
    Locator Assistant +++」**と入力し、その他の設定は
    デフォルト設定のまま**「Next」**をクリックします。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  **Live chat setup –
    Behaviors画面**で、デフォルトを受け入れて**\[Next\]**を
    クリックします。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  **Live chat setup – User features** **画面**で、**File
    attachment** と**Voice and video
    calls** のオプションを**off**に切り替えて、
    **\[Next\]**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. 通知画面でデフォルト値を受け入れ、 **「Next」**をクリックします。

11. **Live chat setup – Review and finish** 画面で、**Create
    channel**を選択 します。

![](./media/image47.png)

12. **Live chat setup–
    Success**画面に表示されるウィジェットの値をコピーし、メモ帳に**保存**します。これは、今後の演習でウェブページに追加するために役立ちます。
    **「Done」**をクリックして設定を完了します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### タスク3: エージェントをワークストリームに追加する

1.  **「New Workstream** **」ページ**に戻り、下にスクロールして、ボット
    セクションで**「+ Add bot** **」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  \[Add bot\] 画面のCopilotのリストから、 **Store Locator Assistant**
    エージェントを選択し、 **\[Connect\]**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  以下のスクリーンショットのように、ボットがワークストリームに追加
    されていることを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  左側のペインから、 **AI Agents**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  **Store locator** エージェントが接続されていることを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## 演習5: ウェブページを作成し、エージェントへの エスカレーションをテストする

1.  テナント管理者の資格情報を使用して、 +++
    [https://make.powerpages.microsoft.com/+++にログインします。](https://make.powerpages.microsoft.com/+++)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  **CustomerService Trial環境**にいることを確認してください。

3.  **「Get started」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  **「Tell us about
    yourself** **」ページ**で「Skip」をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  次のページで下にスクロールし、 **「Start with a
    template** **」**オプションをクリックして、テンプレートを使用してサイトの作成を開始します。

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  テンプレートを選択し、「**Choose this template」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  \[Give your site a name\] テキスト ボックスに「+++Contoso Store
    assistant+++」という名前を入力し、他の既定値を受け入れて \[Done\] を
    クリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  サイトが作成されたら、 **「Edit」**をクリックします。

> ![](./media/image60.png)

9.  **Company name**タイトルの**Edit site header** をクリックします。

![](./media/image61.png)

10. **\[Edit site header\]**ウィンドウで、**Site title** **を**+++
    **Contoso Store assistant** +++ と入力し、ダイアログを閉じます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. ページの右上隅にある**「Edit code」**をクリックします。

![](./media/image63.png)

12. **Open Visual Studio Code**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

13. **「Allow」**をクリックします。必要に応じて、テナントの資格情報を使用して**ログインします。**

![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

14. Web ページのホーム ページがVisual Studio Code で開きます。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

15. ファイルの最後までスクロールします。ワークストリームの作成時にコピーした**スクリプト**を、このファイルの最後の行の後に追加します。

![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

16. ファイルを保存し、Visual Studio Codeタブを閉じてPowerページに
    戻ります。**「Sync」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. 同期が完了したら、 **「Preview** -\> **Desktop」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

18. ウェブページが新しいタブで開きます。ウェブページの右下に埋め込まれている**Store
    Locator Assistant** を探します**。Click**してください。

![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

19. +++Talk to agent+++と入力します。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

20. カスタマー サービス管理ページで、**Customer Service admin
    center** を クリックし、そこからアプリの**Customer Service
    workspace** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

21. **Chat request**を受け取ります。**Accept**してください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

22. 承認されると、エスカレーショントピックで指定したメッセージを含む
    チャット画面が開きます。また、ユーザーがライブエージェントに提供したその他の情報もここで追加できます。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

23. ライブ・エージェントと顧客間のチャットがどのように機能し、終了するかを確認したい場合は、そのチャットをシミュレートします。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image77.png)

## まとめ

この研究室では、

- Copilot Studio からエージェントを構築し、エスカレート
  トピックを構成します。

- エージェントを Dynamics 365 ワークスペースに公開し、Web
  ページに統合します。

  - 
