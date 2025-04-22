# ラボ 05 - エージェントを Dynamics 365 Customer Service アプリに統合し、ライブエージェントへの自動ケースエスカレーションを実装します。

## タスク 1: Dynamics 365 Customer Service ワークスペースを構成する

### Task 1: Omnichannel Power Virtual Agent Extensionを構成

1.  +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com>+++
    リンクを開きOmnichannel Power Virtual Agent ExtensionページでGet it
    nowをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image3.png)

2.  Select the **CustomerService Trial** under **Select an
    environment**の下に**CustomerService
    Trial**を選択して、チェックボックスを選択し、**Install**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

3.  Dynamics 365 appsページに page, **Update
    available**を表示するエントリーをクリックし、
    **チェックボックス**を**選択して**条件の同意し、**Update**をクリックする。

\[Status\]として**\[更新が利用可能\]**の**すべて**のエントリに対してこれを行う

![A screenshot of a computer Description automatically
generated](./media/image5.png)

![A screenshot of a computer Description automatically
generated](./media/image6.png)

### Task 2: Power Platform 管理センターで検索設定を構成する

1.  テナントの詳細を使用して
    +++<https://admin.powerplatform.microsoft.com/>+++
    にログインします。**Environment** - \> **CustomerService
    trialを**選択.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  \[**Resource**\] の横にあるドロップダウンを選択し
    (上部画面内)、**Dynamics 365 apps**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  **Omnichannel for Customer
    Service**が**Installed**されていることを確認する。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

1.  管理センターの Environment -\> CustomerService Trial
    **ページに戻ります** 。　 **上部**画面**から** \[**Settings**\]
    を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  **Product** -\> **Features**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

5.  **Dataverse Search**と**Single table
    search**オプションを**ONに切り替える。**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

下にスクロールして、右下の\[**Save**\]ボタンをクリックします。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

## タスク 2: エージェントの作成

1.  Copilot
    Studioホームページ!!https://copilotstudio.microsoft.com!!で右上から**CustomerService
    Trial** Environmentを選択する。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  左画面から**Agents**を選択する。新しいエージェントを作成するには+
    New Agentを選択する。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

3.  メセッジのテキストを入力するところに**!!You are a customer service
    agent who helps in identifying stores
    nearby.**!!を入力して**send**をクリックする。

![A screenshot of a chat Description automatically
generated](./media/image16.png)

4.  次に!!**Maintain a polite
    tone**!!メセッジを入力して**send**をクリックする。

![A screenshot of a chat Description automatically
generated](./media/image17.png)

5.  **Create**をクリックする。

![A screenshot of a chat Description automatically
generated](./media/image18.png)

1.  作成されたエージェントが開き、「**Your agent is
    ready**」というメッセージが表示されます。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

## タスク 3: コパイロットを Dynamics 365 Customer Service に接続し、Escalateピックを構成する

### タスク 1: Escalateトピックの構成

ここでは、ライブエージェントへのエスカレーションというコンセプトを紹介することに焦点します。そのため、他の新しいトピックを作成せずに、直接そのコンセプトに取り組んでいきます。

1.  **Topics**タブを選択してから**System**タブを選択する。**Escalate**トピックを選択する。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

2.  トピックのメセッジノードを選択して既存の内容を !!**You will be
    transferred to a live agent shortly**!!に置き換える。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

3.  +符号をクリックしてメセッジの横にノードを追加します。

4.  **Topic management** -\> **Transfer conversation**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  Transfer conversationノードに!!The customer wants to talk to a live
    agent!!メセッジを入力する。

![A screenshot of a chat Description automatically
generated](./media/image23.png)

6.  トピックを**Save**する。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  エージェントを**Publish**する。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

### Task 2: CopilotをDynamics 365 Customer Serviceに接続する

1.  Publishしたらcopilotページの右上から**Settings**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

2.  Securityの下に**Security**, と **Authentication**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  **No authentication**オプションを選択して**Save**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  確認ダイアログボックスで**Save**をクリックする。

![A screenshot of a computer screen Description automatically
generated](./media/image29.png)

5.  **Settings**画面を閉じる。

&nbsp;

1.  **Channels**をクリックする。
    (Channelsが表示されていない場合は、+1をクリックしてチャンネルオプションを表示します
    )

![A screenshot of a chat Description automatically
generated](./media/image30.png)

1.  Customer engagement ハブ 画面から **Dynamics 365 Customer Service**
    を選択します。

![](./media/image31.png)

1.  Dynamics 365 Customer Service ページで、**Connect
    をクリックします**。

![A screenshot of a message Description automatically
generated](./media/image32.png)

6.  **Successfully
    connected**メセッジが表示されたら**Close**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

## タスク 4: Dynamics 365 管理センターでワークストリームとチャネルを作成する

### タスク 1: Customer Serviceの Omnichannelにユーザを管理する。

1.  管理者テナントの資格情報を使用して!!https://admin.powerplatform.microsoft.com!!
    にログインし、左側タブから**Environments**を選択する。**CustomerService
    Trial** will be listed here. **Select** を選択する。

![A screenshot of a computer Description automatically
generated](./media/image34.png)

2.  **Environment URL**下の**url valueをクリックする**

![A screenshot of a computer Description automatically
generated](./media/image35.png)

1.  これにより、\[**アプリ**\] ページが開きます。そこから **Customer
    Service admin center** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  これが**Dynamics 365 Customer Service admin center**
    ページを開きます。

![A screenshot of a customer service Description automatically
generated](./media/image37.png)

4.  In **Dynamics 365 Customer Service admin
    centerに、サイトマップの中にCustomer support**
    グループの下にselect **User managementを選択する。**

5.  On the **User
    managementページでUsers**の横にある**Manageを選択する。**

![A screenshot of a computer Description automatically
generated](./media/image38.png)

6.  **Enabled Users**の横のドロップダウンをクリックして**Omnichannel
    Users**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

7.  **Omnichannel Usersページでリストに**ユーザ**MOD
    Administratorを選択する。**

![A screenshot of a computer Description automatically
generated](./media/image40.png)

8.  **MOD AdministratorページにOmnichannelタブを選択する。**

![A screenshot of a computer Description automatically
generated](./media/image41.png)

1.  値が次の表のとおりであることを確認する。

\- Capacity: 100

\- Default Presence: available

![A screenshot of a computer Description automatically
generated](./media/image42.png)

9.  **Save and close**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

### タスク 2: ワークストリームの構成

1.  管理センターのページから、左側画面から**Customer
    support**の下に**Workstreamsを選択して、+ New
    workstreamオプションを選択する。**

![A screenshot of a computer Description automatically
generated](./media/image44.png)

1.  以下の詳細を入力し、下にスクロールして\[Create\]をクリックします。

- Name - +++**New Workstream**+++

- Owner – **MOD Administrator** (Selected by default)

- Type – **Messaging**

- Channel – **Chat**

> ![A screenshot of a chat Description automatically
> generated](./media/image45.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image46.png)

2.  ワークストリームが作成されたら、Set up chatをクリックしてチャット
    チャネルを設定します.

![A screenshot of a chat Description automatically
generated](./media/image47.png)

3.  **Live chat setup – Channel
    details**画面に以下の詳細を入力して**Nextをクリックする。**

- Name - +++**Chat Channel**+++

- Language – **English -** **United States**

![A screenshot of a chat channel Description automatically
generated](./media/image48.png)

4.  In the Live chat setup – Chat widget画面に名前を+++**Store Locator
    Assistant**+++と入力して、他のデフォルトをそのまま使用し、**Next**をクリックする。

![A screenshot of a chat Description automatically
generated](./media/image49.png)

5.  **Live chat setup – Behaviors**
    画面にデフォルトをそのまま使用し、**Next**をクリックする。

![A screenshot of a computer screen Description automatically
generated](./media/image50.png)

6.  **Live chat setup – User features画面にFile attachment** と**Voice
    and video callsのオプションをoffにトグルしてNextをクリックする。**

![A screenshot of a computer Description automatically
generated](./media/image51.png)

7.  **Live chat setup – Review and finish画面にCreate
    channel**を選択する。

![A screenshot of a chat setup Description automatically
generated](./media/image52.png)

ライブチャット設定 –
成功画面に表示されるウィジェットをコピーし、メモ帳に保存して、今後のタスクのウェブページに追加します。「**Done**」をクリックして設定を完了します。

![A screenshot of a chat Description automatically
generated](./media/image53.png)

### タスク 3: copilotをワークストリームに追加する

1.  Back in the **New
    Workstreamへ戻り、下にスコロールしてBotセクションに+ Add
    botにクリックする。**

![A screenshot of a computer Description automatically
generated](./media/image54.png)

2.  From the list of copilots on the Add
    bot画面でcopilotのリストから**Store Locator Assistant**
    copilotを選択して、**Connect**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image55.png)

3.  次のスクリーンショットのように、ボットがワークストリームに追加されていることを確認します。

![A screenshot of a computer Description automatically
generated](./media/image56.png)

4.  左側の画面から、**ボット を選択します**。

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  Real Estate Booking Service copilotが接続していることを確実する。

![A screenshot of a computer Description automatically
generated](./media/image58.png)

## タスク 5: Web ページを作成し、エージェントへのエスカレーションをテストします

1.  Login to
    テナント管理者資格情報を使用して+++https://make.powerpages.microsoft.com/+++
    にログインする。

![A screenshot of a computer Description automatically
generated](./media/image59.png)

2.  **CustomerService Trial環境にいることを確認する。**

3.  **Get started**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image60.png)

4.  **Tell us about yourself**ページにSkipをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image61.png)

5.  Scroll down in the next page and click on
    次のページにスクロールして、**Start with a
    templateオプションをクリックして、テンプレートを使用にするサイトの作成を開始します。**

![A screenshot of a web page Description automatically
generated](./media/image62.png)

6.  テンプレートを選択し、**Choose this template**をクロックする。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

7.  Give your site a name のテキストボックスに名前として+++**Contoso
    Store
    assistant**+++を入力し、他のデフォルトをそのままにして、**Done**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

8.  サイトが作成されたら、**Company name**のタイトル**にある** \[**Edit
    site header**\] をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

9.  **Edit site header画面にサイトタイトルとして**!!**Contoso Store
    assistant**!!.を入力する。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

10. ページの右上隅にある**Edit code**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

11. **Open Visual Studio Code**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image68.png)

12. **Allow**をクリックする。

![A black screen with white text Description automatically
generated](./media/image69.png)

13. Web ページのホーム ページが Visual Studio Code で開きます。

![A screenshot of a computer program Description automatically
generated](./media/image70.png)

1.  ファイルの最後までスクロールします。
    ワークストリームの作成時にコピーした**スクリプト**を、このファイルの最後の行の後に追加します。

![A screen shot of a computer screen Description automatically
generated](./media/image71.png)

14. ファイルを保存し、\[Visual Studio Code\] タブを閉じて、Power
    ページに戻ります。**Sync**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

15. Syncが完了したら**Preview** -\> **Desktop**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image73.png)

16. Web ページが新しいタブで開きます。 **Web**
    ページの右下にあるページに埋め込まれている **Store Locator
    Assistant** を見つけます。**それをクリックします。**

![A screenshot of a website Description automatically
generated](./media/image74.png)

17. +++Talk to agent+++を入力する。

![A screenshot of a phone Description automatically
generated](./media/image75.png)

18. Customer Service adminページで**Customer Service admin center**
    をクリックしてそこから**Customer Service
    workspace**のアプリを選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image76.png)

![A screenshot of a computer Description automatically
generated](./media/image77.png)

19. Customer Service ワークスペース ページで、**チャット
    リクエストを**受け取ります。 **それを**承諾します。

![A screenshot of a computer Description automatically
generated](./media/image78.png)

20. 承諾すると、チャット画面が開き、「エスカレーション」トピックで指定したメッセージが表示されます。また、ここでユーザーから提供されたその他の情報をライブエージェントに追加することもできます。

![A screenshot of a chat Description automatically
generated](./media/image79.png)

21. チャットがどのように機能し、その後終了するかを確認したい場合は、チャットライブエージェントと顧客の間のチャットをシミュレートします。

![A screenshot of a chat Description automatically
generated](./media/image80.png)

![A screenshot of a chat Description automatically
generated](./media/image81.png)

**要約**

- このラボでは、以下の内容を学習しました。

- Copilot Studio
  からエージェントを作成し、エスカレーショントピックを設定する。

- エージェントを Dynamics 365 ワークスペースに公開し、Web
  ページに統合する。

- ライブエージェントへのエスカレーションを設定およびテストする。
