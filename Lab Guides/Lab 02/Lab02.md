# Lab 02 – OneDrive で作成された新しいファイルを追跡するための自律エージェントを構築する

**紹介**

ある組織のOneDrive For
Businessでは、複数のファイルが作成されており、管理者がそれらを追跡することが困難になっています。

**目標**

新しく追加されたファイルの詳細をファイル詳細トラッカーに入力する自律エージェントを構築します。これにより、ファイルの追加を追跡する問題が解決され、ファイル詳細トラッカーには新しく作成されたすべてのファイルの詳細が記録されます。

## 手順 1: 環境の設定

1.  Resourcesタブからのパスワードを使用してVMにログインします。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

### タスク 1: OneDriveを設定する

1.  ブラウザを開き、+++**https://office.com**+++へナビゲートする。**Resources**
    タブからの資格情報を使用して**サインイン**する**。**

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  左側のメニューから**OneDrive**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

3.  左上にある**+** 符号をクリックして**Files upload**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

4.  **C:\LabFiles**からのファイル**File
    details**を選択して**Open**を選択する。

5.  ファイルがアップロードされてから、ファイルが通常処理されたとのメセッジが画面にポップアップされます

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  左側のメニューから「マイファイル」をクリックすると、新しいファイルがそこに表示されているのがわかります。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

### タスク 2 : 開発環境を作成する

1.  Resourcesタブからテナント情報を使用して+++<https://admin.powerplatform.microsoft.com/>+++
    へログインする。

2.  左側のナビゲーション画面から **Environments**選択して**+
    New**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  開いたNew
    Environment画面で、以下の詳細を入力し、「**Next**」をクリックします。.

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image8.png)

![A screenshot of a computer Description automatically
generated](./media/image9.png)

4.  **Add Dataverse**画面にデフォルトを選択し、**Save**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

5.  新しく作成されたEnvironmentがアドミンセンターにリストされ、その状況がEnvironment画面に表示します。

6.  **Status**が**ready**になってからEnvironmentが利用できます。このenvironment
    を今後の手順に使用します。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

### タスク 3: Copilot Studio のトライアルを有効にする 

1.  新しいタブで+++**https://copilotstudio.microsoft.com/**+++を開く

2.  ラボVMの**Resources**タブで提供された**資格情報**を使用し、**サインイン**する。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  ログインしてから**Welcome to Microsoft Copilot Studio**
    ページで国を**United States**のままにしておき**、Get
    Started**をクリックする。

![A person sitting at a computer Description automatically
generated](./media/image13.png)

4.  **Welcome**画面で**Skip**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

## 手順 2: 自律エージェントの構築とテスト

### タスク 1: Copilot Studioからエージェントの作成

1.  エージェント作成ページに表皮されるSkip to
    configureオプションをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

2.  エージェント作成画面に以下の詳細を入力して、**Create**をクリックする。

- **Name** - +++New file tracker agent+++

- **Description** - +++This agent will update the File details tracker
  placed in the OneDrive, each time a new file is created in the
  OneDrive

![A screenshot of a computer Description automatically
generated](./media/image16.png)

### タスク 2: エージェントにトリガーを追加する

1.  エージェントが作成されてからスクロールダウンして、**Trigger**セクションで**+
    Add trigger**を選択する

![A screenshot of a computer Description automatically
generated](./media/image17.png)

2.  **Turn on generative orchestration to continue**のダイアログで**Turn
    it
    on**を選択する。このオプションの設定をオンにすることでトリガーを追加します。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  Add triggerメニューから**When a file is created**
    トリガーを選択する。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

4.  **Add trigger**画面に**Continue**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

> 次の画面で、トリガー名が入力されていることを確認できます。Microsoft
> Copilot Studio と OneDrive for Business
> への接続が確立されるまでお待ちください（各コネクタに緑色のチェックマークが表示されます）。「Next」をクリックします。![A
> screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  以下の詳細を選択します。

- **Folder** – Root

- **Include subfolders** – Yes

> 他のフィールドをデフォルトのままにして**Create trigger**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  トリガーが作成されてから**Time to test your
    trigger**メセッジが表示される。それを**Close**します。トリガーの基本的なフローを少し調整して機能を実装し、テストします。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

### タスク 3: トリガーにロジックを追加する

1.  **New file track
    agent**ページにトリガーのセクションへスクロールダウンする。

2.  **When a file is
    created**のトリガーの横にある三つのドットをクリックして、**Edit in
    Power Automate**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

3.  **When the file is created**と**Sends a prompt action**
    の間にある+アイコンを選択して**Add an action**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

4.  +++add a row+++ を検索して、**Add a row into the table**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

5.  各行に対して以下の値を選択し、Saveをクリックする。

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image29.png)

![A screenshot of a computer Description automatically
generated](./media/image30.png)

6.  フローは以下のスクリーンショットのようになります。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

7.  フローを保存して**publish**する**。**

### タスク 4: トリガーをPublishする

1.  Copilot Studioで**Settings**を選択する

![A screenshot of a computer Description automatically
generated](./media/image32.png)

2.  **Security** -\> **Authentication** -\> **No
    authentication**選択し、**Save**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

3.  確認ダイアログで**Save**を選択する。

![A screenshot of a computer error Description automatically
generated](./media/image34.png)

4.  次に、**Publish**選択し、エージェントを公開する。

![](./media/image35.png)

5.  確認ダイアログでで **Publish**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

### タスク 5: トリガーをテストする

1.  ブラウザで**OneDrive**に戻ります。「+」をクリックして**Word文書**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

2.  ドキュメントに名前を付けて、「**Create**」を選択します。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

3.  プライバシーのオプションを閉じるよう**Close**をクリックする

![A screenshot of a computer screen Description automatically
generated](./media/image39.png)

4.  同様に、さらにいくつかのファイルを追加します。

5.  次に、OneDrive からファイル details.xlsx
    を開き、作成されたファイルの詳細がトラッカーに追加されていることを確認します。

![A screenshot of a computer Description automatically
generated](./media/image40.png)

6.  OneDrive
    にファイルが作成されると、トリガーが起動され、**ファイルが追加されたとき**のフローが実行され、トラッカーが更新されます。

7.  Copilot
    Studioのアクティビティタブで自律エージェントの詳細を確認することもできます。

**要約**

このラボでは、Copilot Studio
から自律エージェントを作成、公開、テストする方法を学習しました。
