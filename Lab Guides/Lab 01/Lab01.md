# ラボ01:Copilot Studioから不動産アプリケーションを管理するためのエージェントの作成と使用

**ラボ 期間** – 90分

**紹介**

Contoso Real
Estateは、商業用不動産と住宅用不動産の両方の販売と管理を専門としています。現在、顧客情報はDataverseインスタンス内に効率的に保存されており、効率的なデータ管理を実現しています。しかし、予約プロセスには大きな課題があります

現在、お客様は電話でのみ予約をリクエストできるため、電話回線が混雑し、待ち時間が長くなっています。この状況は、お客様の不満を招くだけでなく、多くのお客様がオフィスに繋がらずサービスをリクエストできないため、潜在的なビジネスを失うリスクもあります。

これらの問題に対処するため、Contoso Real
Estateは包括的なデジタルソリューションの開発に取り組んでいます。このソリューションにより、顧客は予約プロセスに関する情報に簡単にアクセスし、オンラインで予約リクエストを送信できるようになります。

**目的**

- Copilot Studio から Contoso Real Estates
  用のスタンドアロンエージェントを構築します（これにより、顧客は不動産予約プロセスに関する情報を入手し、オフィスで確認するための予約リクエストを作成できます）。

- 予約ロジックを設定するためのトピックを作成します。

- 予約に必要なデータバーステーブルを作成します。

- Copilot を公開します。

:::danger **2 日目のラボを実行するには、1 日目の終わりまでにラボ 03
を完了する必要があります。ラボ01、02が完了していなくても、Day1終了までにラボ03を必ず完了してください。**.
:::

## 手順 0: 環境の設定

### タスク 1: VMにログイン

1.  \[ホーム\] タブの \[**ユーザー名**\] と \[**パスワード**\]
    を使用して VM に**ログイン**します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

### タスク 2: VM クロックを同期する

1.  VMにログインしたら、画面の右下隅にある時計を右クリックします。

2.  **Adjust date and time**を選択する

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  開いたSettings画面でAdditional Settingsの下に**Sync
    now**をクリックする。

![](./media/image3.png)

4.  これにより、自動同期が機能しない場合に備えて、時刻の同期が処理されます。

5.  Settings画面を**閉じる**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

6.  「**Sign in required**」というアラートが表示された場合は、「**Sign
    In**」をクリックし、「**Sign in with a different
    account**」を選択して、VM
    の「**ホーム**」タブで利用できる**管理者資格情報**を使用してサインインします。

![A blue screen with white text AI-generated content may be
incorrect.](./media/image5.png)

![](./media/image6.png)

7.  **Sign in to this app only**を選択する。

![](./media/image7.png)

1.  ログインしたら、**Teams**アプリ**を閉じます**。3日目のラボで使用します。

## 手順 1: Power Apps と Dataverse の設定

### タスク 1: Sign up for the Microsoft Power Apps Developer Planにサインアップする

1.  ブラウザを開き、!\!<https://powerapps.microsoft.com/free/>!!
    にアクセスし、\[**Start free**\] または **\[Try for free**\]
    を選択します。![](./media/image8.png)

2.  **ホーム**タブからOffice Tenant Credentials
    の**ユーザー名とパスワード**を入力してログインします。この**認証情報**は、ラボで使用するすべてのMicrosoftサイトとアプリへのログイン情報となります。

![](./media/image9.png)

3.  「**Lets get started**」の下で、テキスト
    ボックスに「**Home**」タブの**管理者ユーザー名**を入力し、同意のボックスをオンにして、「**Start
    free**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

4.  Microsoftアカウントを既にお持ちであることを示すプロンプトが表示された場合は、「**サインイン**」を選択し、パスワードを入力してください。

5.  プロンプトが表示されたら、「はい」を選択してサインイン状態を維持します。

6.  画面右上の「**Environment**」をクリックし、「**Dev
    One**」が選択されていることを確認します。選択されていない場合は、「**Dev
    One**」を選択してください。

![](./media/image11.png)

### タスク 2: ソリューションを作成する

1.  Power Apps Maker
    Portal(!\!<https://make.powerapps.com/>!!)から左画面から**Solutions**を選択する

![](./media/image12.png)

2.  **+ New solution**をクリックする。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image13.png)

3.  Display
    nameに「!!**Bookings**!!」と入力し、**Publisher**で「**Contoso
    (contoso)**」を選択して、「**Create**」をクリックします。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image14.png)

**Contoso** オプションが **Publisher**
の下にリストされていない場合は、次の 2
つの手順を実行します。それ以外の場合は、手順 6 から続行します。

4.  **Contoso** オプションが **Publisher**
    の下にリストされていない場合は**+ New Publisher** を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

5.  以下の詳細を入力して**Saveをクリックする**。

[TABLE]

> ![](./media/image16.png)

6.  左上画面で**Back to solutions**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

### タスク 3: 優先ソリューションを設定する

1.  Under Solutions in the MakerポータルでSolutionsの下に**Set your
    preferred solutionで** **Manage**を選択する**。**

![](./media/image18.png)

2.  **Unless otherwise specified, save my changes inの下にBookings
    (contoso)** を選択し、**Applyを選択する。**

![](./media/image19.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

### タスク 4: 不動産物件カスタムテーブルを作成する

新しいテーブルを作成するには、2つの方法があります。1つは従来の手動方式で、もう1つはCopilotを使用する方法です。

#### タスク 4.1: Copilotを使用して動産物件カスタムテーブルを作成する

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

次の列とデータ型を持つテーブル「Real Estate Property」を作成します。  
1. プロパティ名 - 1 行の text

2.提示価格 - 通貨

3.通り - テキストの 1 行

4.市区町村 - 1 行のテキスト

5.クライアント - データ型 Lookup、関連テーブル - 連絡先  
  
不動産物件テーブルにBedroomとBathroomの2つの列を追加し、それぞれにデータ型の選択肢を追加します‐  
1. Label- 1, Value - 1  
2. Label- 2, Value -2  
3. Label- 3, Value 3  
4. Label- 4, Value 4  
5. Label- 5, Value 5

 

以下の列とデータ型を持つ「Booking Request」テーブルを作成します。

1\. 予約名 - 1行テキスト

2\. 物件 - データ型ルックアップ、関連テーブル- 不動産物件

3\. ビュー名 - 1行テキスト

4\. ビューアメールアドレス - 1行テキスト

5\. 予約日 - 日時

6\. メモ - 複数行テキスト

 

Booking Requestテーブルにデータ型の選択を含む「決定」の列を追加する

1\. Label：未決定、値：1

2\. Label：承認、値：2

3\. Label：辞退、値：3

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

すべての列が作成されたら、\[**Real Estate Property columns and
data\]**に次のテスト データを入力します。

- プロパティ名: !!**1100 High Villas**!!

- 希望価格: !!**250,000**!!

- バスルーム: **3**

- ベッドルーム: **2**

- 都市: !!**Redmond**!!

- 通り: !!**Main Avenue**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

#### タスク 4.2: Copilot を使用して Real Estate Properties カスタム テーブルを作成する

Dataverse に不動産物件用の新しいカスタム
テーブルを手動で作成するには、次の手順に従います。

1.  左側のナビゲーション ウィンドウで、 **\[Tables\]** を選択し、 **\[+
    New Table\] の横にあるドロップダウンを選択して** 、 \[**Create new
    tables\] を選択します**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  **Let’s set up your dataダイアログでGot it** を選択する。

![](./media/image32.png)

3.  Create new tables画面で**+ New table -\> Add columns and
    data**をクリックする。

![](./media/image33.png)

4.  テーブル名を **Table1** から !!**Real Estate
    Property**!!に変更して**Save and exit**をクリックする**。**

![](./media/image34.png)

5.  確認ダイアログで**Save and
    exitをクリックする。**![](./media/image35.png)

6.  保存したら、「**Custom**」タブをクリックして、新しく作成されたテーブルを見つけます。「**Real
    Estate Property** table」をクリックします。

![](./media/image36.png)

7.  **Real Estate Property columns and data**の下にある「**New
    Column**」という列の名前を変更し（「**New
    Column**」の横にあるドロップダウンをクリックし、「**Edit
    Column**」を選択して表示名を更新します）、!!**Property Name**!!
    に変更し、「**Save**」を選択します。

![](./media/image37.png)

8.  「+」ボタンを選択して、列とデータ画面に新しい列を追加します。「新しい列」画面で以下の値を入力し、「**Save**」を選択します。

    - Display name: !!**Asking Price**!!

    - Data type: Currency

![](./media/image38.png)

![](./media/image39.png)

9.  次の 2 つの列を追加します。

[TABLE]

10. 以下の値を持つ別の列を追加します

    - **Display name**: !!Bedrooms!!

    - **Data type**: Choice -\> Choice

![](./media/image40.png)

選択肢の値を作成する:

**Sync this choice with**オプションで**+ New choice** を選択する

![](./media/image41.png)

- **Choicesの下に**, Display nameで!!**Bedrooms**!!.を提供する

- 「**ラベル**」と「**値**」という2つの入力フィールドがあります。ラベルの下に「**1**」と入力する。Power
  Appsによって自動的に値が割り当てられますが、この値を1に変更することもできます。

- \+ 新しい選択を選択し、ラベルに 2 を、値に 2
  を新しいエントリとして入力します。

- \+ 新しい選択を選択し、ラベルに 3 を、値に 3
  を新しいエントリとして入力します。

 

- \+ 新しい選択を選択し、ラベルに 4 を、値に 4
  を新しいエントリとして入力します。

- \+ 新しい選択を選択し、ラベルに 5 を、値に 5
  を新しいエントリとして入力します。

 

- **Save**を選択する

![](./media/image42.png)

**Sync this choice
with**のドロップダウンをクリックして追加された選択肢**Bedrooms**を選択する。

![](./media/image43.png)

**Saveをクリックする**。

![](./media/image44.png)

11. \+ ボタンを選択して、列とデータ 画面に新しい列を追加します。

12. 新しい列画面で次の値を入力し、Saveを選択します:

    - **Display name**: !!Bathrooms!!

    - **Data type**: Choice -\> Choice

![](./media/image45.png)

選択肢の値を作成する:

**Sync this choice withの下に+ New choice** を選択する

- **Choicesの下に**, Display name で !!Bathrooms!!.を提供する

- 「**ラベル**」と「**値**」という2つの入力フィールドがあります。**ラベル**の下に「**1**」と入力してください。Power
  Appsは自動的に値を割り当てますが、1に変更することもできます。.

- \+
  新しい選択を選択し、ラベルに2、値に2を新しいエントリとして入力します。

- \+
  新しい選択を選択し、ラベルに3、値3を新しいエントリとして入力します。

- \+
  新しい選択を選択し、ラベルに4、値に4を新しいエントリとして入力します。

- \+
  新しい選択を選択し、ラベルに5、値に5を新しいエントリとして入力します。

- **Save**を選択する。

![](./media/image46.png)

作成した選択肢を選択し、列追加画面で \[Save\] をクリックします。

![](./media/image47.png)

13. 列とデータ ペインで + ボタンをもう一度選択して、別の列を追加します。

新しい列画面で次の値を入力し、**Save**を選択します:

- **Display name**: !!**Client**!!

- **Data type**: Lookup -\> Lookup

- **Related Table**: Contact

![](./media/image48.png)

14. すべての列が作成されたら、Real Estate Property columns and
    dataの下に次のテストデータを入力します:

::: 第2次注: 必要な列が表示されない場合は、+\<number\>more
を選択して表示される列を調整します:::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

- Property Name: !!**1100 High Villas**!!

- Asking Price: !!**250,000**!!

- Bathrooms: **3**

- Bedrooms: **2**

- City: !!**Redmond**!!

- Street: !!**Main Avenue**!!

- Client: **Select any contact**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

:::第2次 注: Contact テーブルにクライアント
レコードがない場合、その列へのデータの追加は無視されます。:::

### タスク 5: Bookings テーブルを作成する

次の手順に従って、Dataverse でReal Estate Property
Bookings用の新しいカスタム テーブルを作成します.

1.  左側のナビゲーション 画面から \[**テーブル**\]
    を選択し、\[**新しいテーブルの作成**\] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

2.  **Create new tables**画面で**+ New table -\> Add columns and
    data**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

3.  テーブル名を**Table1**から!!**Booking Request**!!に変更し、「**Save
    and exit**」をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

4.  確認ダイアログで「Save and exit」をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

5.  保存したら、「**カスタム**」タブをクリックして、新しく作成されたテーブルを見つけます。「Booking
    Request」テーブルをクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  「**New Column**」という列の名前を「**!!Booking
    Name!!**」に変更します (「**New
    Column**」の横にあるドロップダウンをクリックし、「**Edit
    column**」を選択して、表示名を更新します)。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

1.  列名の横にある **\[+**\] 記号をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

1.  以下で指定されている名前とデータ型で次の列を作成します。\[**Save\]
    を選択します**。

    - Display name – !!Property!!

    - Data type – Lookup -\> Lookup

    - Related Table – Real Estate Property

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

- Display name – !!Viewer Name!!

- Data type – **Single line of text**

 

- Display name – !!Viewer Email!!

- Data type – **Single line of text**

- Format – **Email**

 

- Display name – !!Booking Date!!

- Data type – **Date and time**

 

- Display name – !!Notes!!

- Data type – **Multiple lines of text**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

1.  以下の詳細を含むChoiceデータ型列を追加します。

    - Display name – !!Decision!!

    - Data type – Choice -\> Choice

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

**Sync this choice withの下に、+ New
Choice**をクリックする**。**Enter **Display
nameで**!!**Decision**!!.を入力する。

以下の詳細を入力して**Save**をクリックする。

- Label– !!**Undecided**!!

- Value – 1

- Label– !!**Accepted**!!

- Value – 2

- Label– !!**Declined**!!

- Value – 3

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

**Sync this choice
withフィールドの下に追加された**Choice**Decisionを選択して、** **Default
choice** として**Undecidedを指定してSave**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

## 手順 2: Copilot Studio での作業

### タスク 1: Copilot Studioの体験版に申し込む

1.  ブラウザの新しいタブに以下のurlへ移動する。!\!<https://copilotstudio.microsoft.com/>!!.

2.  **Choose your country/regionをデフォルト値のままにしてStart free
    trial**をクリックする。

![A person sitting at a computer AI-generated content may be
incorrect.](./media/image63.png)

3.  Click on **Environments** on the top left and select **Dev One**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

4.  Welcome to Copilot Studio!
    プロンプトが表示されたら**Skip**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

### タスク 2: Real Estate Booking Service agentの作成

1.  左側のナビゲーション ウィンドウから **\[Create**\] を選択し、
    **\[New Agent**\] タイルを選択します.

![A screenshot of a software AI-generated content may be
incorrect.](./media/image66.png)

2.   **Skip to configure**を選択する

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  以下の詳細を入力する

    - Name - !!**Real Estate Booking Service**!!

    - Description - !!**Create bookings for real estate properties**!!

    - Instructions - !!**Create a copilot for topics relating to
      creating bookings for real estate properties!!**

    - Language **–** **English**を選択する

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

1.  画面の右上にある \[Create\] ボタンの横にある 3
    つのドットを選択し、\[**Edit advanced settings\]** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

4.  Solutionsで**Bookingsを選択して、Save**.を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

5.  画面の右上に**Create**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

6.  エージェントが作成されたら、\[Test your copilot\] 画面に「!!**How do
    I make a
    booking?**!をクリックし、**Enter**をクリックして応答を確認します。一般的な応答が得られます.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

### タスク 3: セキュリティの構成

1.  画面の右上にある\[**設定**\]を選択します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image73.png)

1.  \[Security**\]** タブを選択し、\[**Authentication**\]
    タイルを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

1.  **No authentication**を選択して**Save**をクリックする

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  **Save this configuration**プロンプトで**Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

1.  認証設定を保存したら、\[**Close**\]オプションをクリックして\[**Settings**\]画面を閉じます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

### タスク 4: 不要なトピックを無効にする

新しいco-pilotには、サンプル トピックが含まれています。これらのサンプル
トピックを削除します。不要なシステムトピックを無効にします。

1.  Copilot Overview
    ページで右上のメニューから**Topics**タブを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

2.  **Custom** Topics ページに移動されます。

3.  **System**タブを選択する**。**「サインイン**」トピック**の**「Enabled」**を**「Off」**に切り替えます.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

### タスク 5: copilotの公開をテストする

1.  \[**Publish\]** を選択して、このエージェントを発行します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

2.  **Publish this agent**ダイアログの中に**Publish**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

### タスク 6: デモウェブサイト

デモ Web
サイトでは、ライセンスを持たないユーザーがco-pilotをテストできます。デモ
Web サイトへの URL を提供できます.

1.  画面の右上にある **\[Settings**\] または \[**Publish**\]
    ボタンの横にある **3 つのドット**を選択し、\[**Go to Demo
    website\]** を選択します。

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image82.png)

2.  **Type your messageテキストボックスに、**!!**What information is
    needed to book a viewing for a real estate property?**!!
    を入力してエージェントからの応答を確認します。

![A screenshot of a chatbot AI-generated content may be
incorrect.](./media/image83.png)

まだ具体的なトピックの設定やエージェントへのロジックの実装は行っていないため、Studioでエージェントをテストした際に取得したものと似た汎用的な内容になります。以降の手順で設定を行います。

## 手順 3: Copilot を使用したトピックの作成と管理

### タスク 1: Copilot を使用してトピックを作成する

トピックは、自然言語を使用して作成および編集できます。

1.  Copilot Studio
    を開いたブラウザタブに戻ります。「**Topics**」タブから「**Add a
    topic**」を選択し、「**Create from description with
    Copilot**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

:::secondary::: **注:**
「クリップボードにコピーされたテキストと画像を表示する
::：」と表示された場合は、「Allow」を選択します。

2.  以下の詳細を入力して**Create**をクリックする

    - Name your topic - !!**Customer Details**!!

    - Create a topic to... - !!**Ask the customer for their name and
      email address**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

3.  トリガー フレーズと質問ノードを含む新しいトピックが表示されます。

4.  **Save**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

### タスク 2: 自然言語によるノードの更新

1.  画面の右側に「Edit with
    copilot」画面が表示されない場合は、オーサリング
    キャンバスの上部にあるcopilotアイコンを選択します。

2.  2番目の質問ノード**What is your email address?**を選択する

3.  In the **Edit with Copilot** panel, in the **What do you want to
    do?フィールドのEdit with Copilot** パネルに以下のテキストを入力する

!!**Update the message in this question node to say thank you to the
Name variable from the previous node and then proceed to ask the email
address question**!!

::: :::

4.  **Update**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

5.  **Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

### タスク 3: 自然言語でノードを追加

既存のノードを更新するだけでなく、Copilot
を使用して新しいノードを追加できます。

1.  ノードが選択されていないことを確認するには、ノードの周りの空きスペースをクリックします。

&nbsp;

1.  **What do you want to do?
    フィールドに以下を入力してUpdate**を選択する**。**

!!**Add a new multiple-choice question to prompt the user if the details
are correct with two options Yes or No**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

2.  トピックの最後に新しい質問ノードが追加され、ユーザーが選択できるオプションが表示されます。

3.  **Are the details
    correct?**内容の下にある質問の部分に以下の内容を入力する。

> \<h3\>Summary\</h3\>
>
> \<p\>\<strong\>Full Name:\</strong\>
>
> Name string
>
> \</p\>
>
> \<p\>\<strong\>Email Address:\</strong\>
>
> EmailAddress string
>
> \</p\>
>
> **{x}** 記号を選択して、\<p\> タグ内の**名前文字列**と**メール
> アドレス**文字列を対応する変数に置き換えます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

4.  **Save**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### タスク 4: 変数のスコープを構成する

1.   **Variables**を選択し**、Variables**の画面を開く。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

2.  値を受け取る変数と値を返す変数があります。トピック変数は元のトピックに値を返します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

3.  トピック変数で右側のチェックボックスをオンにして**Save**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

## 手順 4: トピックを手動で作成および管理する

### タスク 1: 空白からトピックを作成する

1.  **Topics** tabを選択する。

2.   **Add a topic**を選択して**From blank**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

3.  **Details**を選択してTopicダイアログを開けます**。** ![A screenshot
    of a computer AI-generated content may be
    incorrect.](./media/image96.png)

4.  以下の詳細を入力して**Save**をクリックする。

    - **Name** - !!Book a Real Estate Showing!!

    - **Display Name –** !!**Book**!!

    - **Description** - !!Select the property and requested date and
      create a booking request!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

5.  **Detailsを選択してTopic details**ダイアログを閉じます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

### タスク 2: トリガー フレーズを追加する

1.  Select **Edit** under **Phrases** in
    the **Triggerの下にあるPhrasesからEditを選択する。** **Add
    Phrases**の下に!!**I want to book a real estate showing**!!
    を追加して**+** アイコンを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

2.  以下の文章を一つずつ入力する。各文章を入力した後**+**アイコンを選択する**。**

    - !!**Schedule a real estate showing**!!

    - !!**Arrange the viewing for a real estate property**!!

    - !!**Set up an appointment to view a house**!!

    - !!**Plan a property viewing**!!

3.  これで全ての文章が追加された後**Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

### タスク 3: メッセージ・ノードの追加

1.  Trigger nodeの下にある**+**アイコンを選択し**、Send a
    message**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

2.  **Enter a messageフィールドに以下のテキストを入力する**：

!!Hi, I can help you with booking a real estate property showing.!!

3.  **Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

### タスク 4: トピック管理ノードを追加する

1.  send a messageノードの下にある**+アイコンを選択して、Topic
    management -\> Go to another topic**を選択する。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image103.png)

2.  **Customer Detailsトピックを選択する。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

3.  **Saveを選択する。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

### タスク 5: Add conditionノード

1.  Select the **+** icon under the topic
    managementノードの下にある**+アイコンを**選択して、**Add a
    condition**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

2.  変数に対して**DetailsCorrect**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image107.png)

3.  **Conditionでis equal to**を選択する**。**

4.  値で**Yes**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

5.  **Save**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

### タスク 6: questionノードの追加

1.  Select the **+** icon under the left-hand condition node and
    select 左側のcondition **ノードの下にある+アイコンを選択してAsk a
    question**を選択する**。**以下の詳細を入力して**Save**を選択する。

    - Enter a message - !!Which property do you want to see?!!

    - **Identify** - Select **User's entire response**.

    - **Save user response as** Enter !!**PropertyName**!!
      for **Variable name**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

2.  questionノードの下にある**+**アイコンを選択して**、Ask a
    question**を選択する**。**
    以下の詳細を入力して**Save**をクリックする**。**

    - **メセッジを入力する**- !!What date and time do you want to see
      the property?!!

    - Identify - Select **Date and Time**

    - **Save user response as** – Click on **Var1** to open the Variable
      properties pane and enter !!**DateTime**!! for **Variable name**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

### タスク 7: copilotをテストする

1.  画面の右上にある \[Test**\] ボタンを選択して** 、テスト
    パネルを開きます。 画面の右上にあるテスト パネルの上部にある 3
    つのドットを選択します。\[**Track between topics\] を選択します**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

2.  **Conversation Startメセッジが表示されたら**copilotが
    会話を開始します。

&nbsp;

1.  応答として、作成したトピックのトリガー フレーズを入力します。

!!I want to book a real estate showing!!

3.  The copilotが"**What is your name?**"質問で応答します。

4.  名前を入力する。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image113.png)

5.  次、メールアドレスのプロンプトが表示されたら、メールアドレスを入力する。入力後、情報が正しいかどうかを確認する質問が表示され、「Yes」または「No」を選択できます。「Yes」を選択してします

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image114.png)

6.  **Which property to you want to see?プロンプトで**!!555 Oak Lane,
    Denver, CO 80203!!を入力します。

7.  **What date and time do you want to see the
    property?** プロンプトで!!**Tomorrow 10:00 AM**!! を入力します。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image115.png)

## 手順 5: 予約が作成または更新されたときに自動的にメールを送信する自律エージェントを構築する

This 手順 is to showcase the **When a row is added, modified or
deleted** trigger of an Autonomous agent.

### タスク 1: エージェントを作成

1.  **左側ナビゲーションウィンドウで**Agentsを選択する**。**

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image116.png)

2.  **+ New agentをクリックして新しいエージェントを作成する。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

3.  **Skip to configureをクリックしてエージェントを構成できます。** ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image118.png)

4.  以下の詳細を入力して**Create**をクリックする。

**Name** - !!Autonomous agent!!

**Description** - !!You are an agent to detect the updates to the
Booking Requests table!!

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image119.png)

5.  エージェントのセットアップは数秒で完了します。完了すると、Autonomousエージェントが起動し、「**Your
    agent is ready**」というメッセージが表示されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

6.  Select **Settings** from the top right corner.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

7.  エージェントのトリガー作成を続行するには、Generative AI
    オプションを有効にする必要があります.

8.  設定画面の左側にあるオプションリストから「Generative
    AI」オプションを選択します。「Using Generative AI in
    conversations\]を使用する」で「Generative」を選択し、「Save」をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

9.  **Settings**画面を閉じる。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

### タスク 2: エージェントにトリガーを追加する

1.  自律エージェント ページに戻り、**Triggers (Preview)**
    セクションまで下にスクロールし**、** \[+ トリガーの追加**\]**
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

2.  **Add trigger**画面に**When a row is added, modified or
    deleted**トリガーを追加**する。** 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image125.png)

3.  次の画面に**Continue**をクリックする**。**

4.  選択すると、次の画面に**トリガー名**と**サインインオプション**が表示されます。入力には数分かかります。選択したトリガーには、**Microsoft
    Copilot Studio** と **Microsoft Dataverse** の 2
    つのアプリが表示されます。読み込まれたら、サインイン
    オプションの接続ステータスが**緑色**になっていることを確認して、\[Next\]
    をクリックして続行します。![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image126.png)

5.  In the Add trigger画面に以下の詳細を選択し、**Create
    trigger**を選択する。

    - Change type – **Added or modified**

    - Table name – **Booking Requests**

    - Scope – **Organization**

    - トリガーの指示–**デフォルト**のままにする。**これで、エージェントに全体の応答が戻ります。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image127.png)

6.  トリガーの作成完了に3分～5分かかる場合があります。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

7.  完了したら**Time to test your trigger!** 画面に、Screen
    **Closeをクリックする。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

8.  **Actionsタブをクリックして、+ Add action**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

9.  !!Send an email!! を選択して、**Send an email (V2)
    action**を選択する。

![A screenshot of a email conversation AI-generated content may be
incorrect.](./media/image131.png)

10. 接続が確立されたら、\[Next\]をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

11. **End user authenticationのドロップダウンからCopilot author
    Authentication**を選択してから**、Add action**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

12. 作成されたActionを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

13. **Inputsタブを選択する。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

14. **Description**フィールドにメールアドレスを入力して、**Save**をクリックする。このメールアドレスがアクセスできる任意のメールアドレスです。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image136.png)

### タスク 3: エージェントに指示を追加する

1.  **Overview**を選択し**、**Overviewページへ移動してからOverviewページの**Edit**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

2.  以下の手順を「**Instructions**」テキストエリアに貼り付け、セクションbの\<メールID\>のプレースホルダーを詳細を送信するメールIDに置き換えて、「**保存**」をクリックします。

!!a. Read the details of the row that gets added or modified!! !!b. Mail
the modified information only to \<Mail ID\> with a proper subject and
body added to the email!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

3.  **Publish**をクリックすると、エージェントが接続されているすべてのチャネルに公開されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

4.  **Publish this agentダイアログボックスでPublishをクリックする。**

![A screen shot of a computer AI-generated content may be
incorrect.](./media/image140.png)

5.  Publishされてから正常処理のメセッジが表示されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

### タスク 4: 予約table

1.  !\!<https://make.powerapps.com/>!!
    にログインして、左側ナビゲーション画面から**Tables**を選択する**。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

2.  Select **Custom**を選択して、そこで**Booking
    Request**のテーブルを選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image143.png)

3.  テーブル中に値を追加又は更新する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

### タスク 5: エージェントをテストする

1.  エージェント ページで \[テスト\] を選択し、**Activity Map**
    をオンにします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

2.  From the agent page, select the エージェントページから**Test
    triggerオプションを選択する。**予約テーブルに加えた更新がトリガーを起動したはずです。Copilot
    studioからテストするために使用します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

3.  最新のエントリを選択し、「**テストを開始**」をクリックします.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image147.png)

4.  トリガーが起動されます。![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image148.png).

5.  メールは特定されたメールアドレスに送信されます。![A screenshot of a
    computer AI-generated content may be
    incorrect.](./media/image149.png)

6.  該当するメールボックスを確認し、以下のようなメールを受信して​​いるかどうかを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

**要約**

本ラボでは次を学びました。

- Copilot Studio からエージェントを構築し、トピックを作成します。

- Copilot Studio
  からエージェントをテストし、デモウェブサイトに公開します。

- 自律エージェントを構築し、テストします。

 
