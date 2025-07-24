
# ラボ 06 - Copilot Studio で Azure AI Search を活用した HR 向け Knowledge Assistant エージェントを作成する

## 客観的

大企業では、SharePoint、PDF、社内 Wiki、ドキュメントなどに分散している
HR 関連の情報 (ポリシー、福利厚生、休暇ガイドラインなど)
を従業員が検索するのにかかる時間を短縮したいと考えています。

この問題を解決するために、このラボでは、Azure AI Search を使用して企業の
HR ドキュメントのインデックス作成と意味的な検索を行う**Knowledge
assistant** エージェントを Copilot Studio で構築します。

## 演習 1: Azure AI Search リソースを作成する

1.  Azure ポータルのホーム ページから、 **Azure AI Foundry**
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  **AI Foundry ページ**で、左側のペインから**AI Search**を選択し、 **+
    Create** を 選択します。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image2.png)

3.  以下の詳細を入力し、 **「Review + create」**を選択します。

- Subscription –**割り当てられたサブスクリプション**を選択します

- Resource group –**割り当てられたリソース グループ**(
  **ResourceGroup1** )を選択します。

- Storage account name – +++ **searchleaves** +++

- Location –**割り当てられた地域**を選択してください

![A screenshot of a search service AI-generated content may be
incorrect.](./media/image3.png)

4.  検証に合格したら、 **\[Create\]**を選択します。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image4.png)

5.  デプロイには数分かかります。Search serviceが作成されたら、 **「Go to
    resource」を**選択してください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  **「Overview」ページ**から、
    Urlバリューをコピーし、今後の演習で使用するためにメモ帳に保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  左ペインの**「Settings」**から**「Keys」**を選択します。**Primary
    admin keyを**
    コピーし、メモ帳に保存して、今後の演習で使用してください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  左側のペインの**\[Settings\]**の下にある**\[Identity\]**を選択します。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image8.png)

9.  **「System assigned」の**ステータスを**On**に切り替えて、
    **「Save」**をクリックします。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image9.png)

10. **Enable system assigned managed
    identity**確認ダイアログで**\[Yes\]**を選択 します。

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image10.png)

## 演習2: ストレージアカウントを作成する

1.  +++https://portal.azure.com/+++
    でAzureポータルにログインし、資格情報でログインします。ホーム画面から「Storage
    accounts」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  新しいストレージ アカウントを作成するには、 **\[+
    Create\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

3.  以下の詳細を入力し、他のフィールドではデフォルトバリューを受け入れて、
    **「Review + create」**をクリックします。

- Subscription –**割り当てられたサブスクリプション**を選択します

- Resource group –**割り当てられたリソース グループ**(
  **ResourceGroup1** )を選択します。

- Region –**割り当てられた地域**を選択します。

- Storage account name – +++ **leavepolicystorage** +++

- Primary service – **Azure Blob Storage または Azure Data Lake Storage
  Gen 2**を選択します**。**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

4.  検証に合格したら、 **「Create」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  リソースの作成が成功したら、 **「Go to
    resource」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  **「Data storage」**の**「Containers」**を選択します。 **「+
    Container」**を選択し、名前を「++ + **document
    +++」**と入力して**「Create」**をクリックし、
    コンテナーを作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

7.  作成されたコンテナ**document**を選択し、そこに休暇ポリシー
    ドキュメントをアップロードします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  **\[Upload\]**をクリックし、 **\[Browse for files\]**を選択します。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image19.png)

9.  **C:\Labfiles**から**LeavePolicy.docx**を選択し、
    **「Upload」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

10. **leavepolicystorage**に移動し（ Azureポータルの**ホーム画面**で
    **「Storageaccounts」**を選択し、 **「leavepolicystorage
    」を選択**）、左側の ペインから**「Access Control
    (IAM)」**を選択します**。「Add -\> Add role
    assignment」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

11. +++ **Storage Blob Data Reader** +++
    を検索し、選択して**「Next」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

12. **「+ Select members」**をクリックし、**user
    id**を検索して選択し、リストに 表示された**user
    id**を選択して**「Select」**をクリックします。これにより、
    ストレージBLOBデータリーダーロールがユーザーIDに追加されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

13. **「Managed identity」**を選択し、 **「+ Select
    members」**を選択します。 **「Managed identity」**の下の**「Search
    service」**を選択し、リストに表示
    される**searchleaves**サーチ・サービスを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

14. **「Select」**をクリックしてサーチ・サービスを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

15. Add role assignment画面に戻り、**Review + assign**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

16. 次の画面でもう一度**「Review + assign」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

17. ロールを追加したら次の手順に進みます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

この演習では、ストレージ
アカウントを作成し、ドキュメントと必要な　　　　ロール権限を追加しました。

## 演習 3: Azure OpenAI サービスを作成し、モデルをデプロイ　　する

1.  Azure ポータルのホーム ページから、+++Azure OpenAI++
    を検索して選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

2.  **+ Create**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

3.  以下の詳細を入力し、 **「Next」**を選択します。

- Subscription –**割り当てられたサブスクリプション**を選択します

- Resource group –**割り当てられたリソース グループ**(
  **ResourceGroup1** )を選択します。

- Region –**割り当てられた地域**を選択します

- Name – +++ **openaiservice52374668** +++

- Pricing tier –**Standard**を選択します

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  次の 2 つの画面で**\[Next\]**を選択し、\[**Review +
    submit\]**画面で**\[Create\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  サービスが作成されたら、 **「Go to resource」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

6.  左側のペインから**\[Access control (IAM)\]**を選択し、 **\[Add -\>
    Add role assignment\]**を選択します。

![](./media/image36.png)

7.  +++ **Cognitive Services OpenAI User**
    +++を検索し、ロールを選択して**Next**クリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

8.  **+ Select members**を選択、**user
    id**を検索して選択し、**Select**をクリック します。

![](./media/image38.png)

9.  **\[Add role assignment」**画面に戻り、 **「Managed
    identity」を選択します**。 次に、 **「+ Select
    members」を選択します**。 **「Select managed identities」**画面で、
    **「Managed identity」**の下にある**「Search service」を選択し**、
    **「seachleaves」**サービスを選択します。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image39.png)

10. 選択したら、 **「Select」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

11. 次の 2 つの画面で \[Review + assign\] を選択します。

![](./media/image41.png)

12. 次のタスクに進む前に、ロールの追加に関する**success**メッセージを
    待ちます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

13. Azure OpenAI サービス リソースの**Overviewページ**で、select **Go to
    Azure AI Foundry portal**を選択し、そこで Azure OpenAI
    サービスを開いてモデルを デプロイします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

14. 左側のペインから**「Deployments」**を選択します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

15. **+ Deploy model** -\> **From base models**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

16. +++ **text-embedding** +++ を検索し、
    **text-embedding-3-largeを選択して** から、**Confirm**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

17. 「Deploy text-embedding-3-large」で**「Deploy」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

18. モデルがデプロイされ、デプロイの詳細が画面に読み込まれます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

## 演習4: ベクトル・インデックスを作成する

1.  **searchleaves** AIサーチ・サービスリソースにアクセスし、 **「Import
    and 　　　　　vectorize data」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  **Azure Blob Storage**オプションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  **「What scenarios are you
    targeting?」画面**で**RAG**オプションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  以下の詳細を入力し、他のバリューはデフォルトのままにして、
    **「Next」**を クリックします。

- Subscription –**割り当てられたサブスクリプション**を選択します

- Storage account - **leavepolicystorage**を選択 します

- BLOB-container –**document**を選択します

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  「Vectorize your text」画面では、サブスクリプションとAzure OpenAI
    リソースの詳細が事前に入力されています。以下の詳細を入力し、
    **「Next」**をクリックしてください。

- Model deployment – **text-embedding-3-large**を選択

- Authentication type – **System assigned identity**を選択

- Azure OpenAI
  のコストアラートを確認するには、チェックボックスをオンにします。

6.  ここでは画像を扱わないため、「**Vectorize and enrich your
    images」**画面で「Next」を選択し、**Advanced
    settings**画面でも**「Next」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

7.  **\[Review + create\]**画面で**\[Create\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

8.  成功ダイアログボックスで**「Close」**をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

## 演習5:Knowledge Assistantエージェントを作成する

1.  ログイン資格情報を使用して、+++https://copilotstudio.microsoft.com+++
    にログインします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

2.  左側のペインから**\[Create\]**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

3.  **「+New agent」**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

4.  +++ You are a Knowledge assistant agent for HR who will answer
    questions related to leaves and leave policies to the employees + ++
    と入力し、 **\[Send\]**を選択します。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image60.png)

5.  Copilotがエージェントに名前を提案します。
    **「Create」**をクリックして エージェントを作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

6.  エージェントが作成されたら、\[Test\] ペインに「+++ How many days can
    I avail Maternity leaves? + ++」と入力し、 **\[Send\]**
    をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

7.  以下のスクリーンショットのように、一般的な返信が返されます。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image64.png)

## 演習 6: Azure AI Search をナレッジ ソースとして追加する

1.  エージェントの**Overviewページ**から、**Add
    knowledge**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

2.  利用可能なナレッジ ソースのリストから Azure AI Search を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

3.  次の画面で**「Not
    connected」**の横にある**ドロップダウン**をクリックし、 **「Create
    new connection」**を選択します。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image67.png)

4.  前の演習でメモ帳に保存した**Endpoint URL**と**Admin
    keyのバリュー**を入力し、
    **\[Create\]**をクリックして接続を作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

5.  接続が確立されると、利用可能なインデックスがリストされ、選択済みになります。
    **「Add」**をクリックしてください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

6.  AI サーチ・サービスがエージェントにナレッジ
    ソースとして追加され、現在は**Ready**状態になっています。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

7.  試したのと同じ質問でエージェントをテストしてみましょう。

8.  テスト ペインに、「+++ How many days can I avail Maternity
    leaves?+++」と入力し、 **\[Send\]** をクリックします。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

9.  エージェントからの応答は、AI サーチ・サービスにアップロードされた
    ドキュメントからのものであることがわかります。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image72.png)

## まとめ

このラボでは、エージェントをナレッジ ソースとして Azure AI Search
サービスに接続し、ソースに基づいてエージェントをテストする方法を学習しました。
