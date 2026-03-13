# ラボ 2 - テンプレートベースのエンタープライズ アシスタントの構築と強化

**目的**

**エージェントテンプレート**は**、カスタムエージェント**の作成を始めるのに役立つように設計されています。エージェントテンプレートの使用およびビジネスに合わせてカスタマイズする際の、あらゆる安全性および法的側面について評価する責任は、お客様自身にあります。

**Safe
Travelsエージェントテンプレート**に基づいて構築されたエージェントは、企業従業員に**旅行支援**を提供するBusiness-to-Employee
（B2E）エージェントです。このエージェントは、従業員が次の出張に向けて十分な準備を整え、必要な情報を入手できるようサポートします。natural
language処理を活用した対話型インターフェースを備えているため、従業員は必要な情報に簡単かつ直感的にアクセスできます。ただし、このエージェントがデフォルトで使用するウェブサイトは現在、米国内の旅行先のみを対象としています。デフォルトのウェブサイトは、独自のナレッジソースに置き換えることができます。

このラボでは、**Safe Travels**
テンプレートからエージェントを作成し、ラボ 05 でそれを強化します。

## 演習 0 - Entra ID でセキュリティグループを作成し、Copilot Studio Authorsを構成する

これは、このコース全体を通じて Copilot Studio
でエージェントを公開し、シームレスに操作できるようにするための前提条件タスクです。

1.  Azureポータル+++https://portal.azure.com/+++にアクセスし、**Resources** タブに記載されているテナントの資格情報を使用してログインします。

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  「Keep your account
    secure」ウィンドウで「**Next** 」を選択し、**プロンプト**に従います。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Authenticator
    アプリをまだインストールしていない場合は、携帯電話にダウンロードしてください。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  プロンプトに従ってセットアップを完了します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  Azure のようこそ画面で、\[**Get Started**\] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  +++Microsoft EntraID+++ を検索して選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  左側のペインから、**Manage** -\> **Groups**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  新しいセキュリティ グループを作成するには、\[**New group** \]
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  以下の詳細を入力してください

    - Group type – **Security**を選択します。

    - Group name – +++copilotagentsecurity+++ と入力します。

    - Microsoft Entra roles can be assigned to the group – \[**Yes**\]
      を選択します
      (このオプションが表示されない場合は、この手順を無視してください)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. 「**No owners selected**」を選択し、「**Add owners** 」ページから
    **MOD Administrator** を選択して、「**Select**」をクリックします。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. 同様に、「**No members selected**」を選択し、リストから **MOD
    Administrator** を追加して、「**Select**」をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. 「**No roles
    selected**」を選択します。このオプションが**表示されない**場合は、この手順と次の手順を無視してください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. +++**Global admin**+++ を検索して選択し、\[**Select**\]
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. すべての詳細を追加したら \[**Create** \] を選択し、確認ダイアログで
    \[**Yes** \] を選択します。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. **成功**メッセージが表示されたことを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. 左上から Contoso|Groupsを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. 左側のペインから \[**Manage** \] の下にある \[**Properties** \]
    を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. \[**can manage access to all Azure subscriptions and management
    groups in this tenant** \] オプションを \[Yes\]
    に切り替えて、\[**Save**\] をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. 次に、左側のペインの \[**Manage** \] の下にある \[**Roles and
    administrators** \] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. +++privileged role admin+++ を検索し、**Privileged Role
    Administrator**ロールをクリックします
    (**チェックボックスを選択せず**​​、名前をクリックします)。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

21. **+ Add assignments**を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

22. 「**No members selected**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

23. **MOD Admin id** を選択し、\[**Next**\] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

24. \[**Assign**\]を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

25. ロールの割り当てが成功したことを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

26. 新しいタブから、+++<https://admin.powerplatform.microsoft.com/+++>に移動します。左側のペインから
    \[**Manage** \] を選択し、\[**Tenant Settings** \]
    オプションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

27. 利用可能なリストから **Copilot Studio Authors** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

28. 設定を編集するには、**Edit** アイコンをクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

29. 先ほど作成した +++**copilotagentsecurity**+++
    グループを検索して選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

30. 設定を保存するには、\[**Save** \] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

## 演習 1: テンプレートから Safe Travels エージェントを作成する

この演習では、Safe Travels エージェント テンプレートを使用して Copilot
Studio でエージェントを作成します。

1.  ブラウザから+++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/)にログインします。「Start
    free trial page」ページが開きます。国を選択して、「**Start free
    trial**」をクリックします。　

![](./media/image39.png)

2.  **Dev One** 環境を選択します。

> ![](./media/image40.png)
>
> 重要: 以下のスクリーンショットのように、Copilot Studio
> に**Environment** を選択するオプションが表示されない場合は、以下の手順に従ってください。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image41.png)
>
> +++<https://admin.powerplatform.microsoft.com/+++>を開きます。**Manage** -\> **Environments
> -\> Dev One** を選択し、**Environment ID**の値を選択します。![A
> screenshot of a computer AI-generated content may be
> incorrect.](./media/image42.png)
>
> Copilot
> Studioタブに戻り、+++<https://copilotstudio.microsoft.com/environments/>**\<
> EnvironmentID \>**+++ を開きます。(\< **EnvironmentID** \>
> を上記で取得した値に置き換えます)

3.  ようこそ画面で「Skip」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

4.  左側のペインから \[**Agents** \] を選択し、\[**Start with an agent
    template**\] の下にある \[**Safe Travels**\]
    テンプレートを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

5.  Safe Travels
    テンプレートは、会社の従業員に旅行支援を提供するように設計された新しいエージェントを作成します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

6.  設定ページを参照してください。「**Knowledge**」の下に、**US Travel
    Website**がナレッジソースとして既に追加されていることがわかります。必要に応じて編集できます。ここでは、同じウェブサイトを使用しています。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

7.  「**Create** 」を選択してSafe
    Travelsエージェントを作成します。ここでは何も変更せず、テンプレートをそのまま使用します。エージェントは、ユーザーの要件に応じていつでもアップグレードできます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

8.  **エージェント**が**作成され**、自動的に開き、**Overview** ページが表示されます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

9.  Testペインで、+++How to apply for passport?+++と入力し、\[**Send**\]
    をクリックします。

Testペインは、デフォルトで開いています。開いていない場合は、右上のTestアイコンをクリックしてください。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

10. エージェントがナレッジソースからパスポートの申請方法に関する情報を提供していることがわかります。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image50.png)

## 演習 2: エージェントを Teams と Microsoft 365 Copilot に公開する

この演習では、Copilot Studio で作成したエージェントを **Microsoft
Teams** および **Microsoft 365 Copilot** チャネルに**公開します**。

1.  **MS
    Teams** （+++<https://teams.microsoft.com/v2/+++>）をブラウザからアクセスし、\[**Resources** \]
    タブからテナント資格情報を使用して**ログインします。**

2.  Copilot Studio に戻り、エージェント ページの右上から
    \[**Publish** \] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

3.  「**Force newest
    version** 」チェックボックスをオンにし、確認ダイアログで「**Publish** 」を選択します。

![](./media/image52.png)

![](./media/image53.png)

4.  上部のナビゲーション バーから \[**Channels** \] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

5.  利用可能なチャネルの一覧から、**Teams and Microsoft 365
    Copilot** を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

6.  **Add channel**を選択します。

![](./media/image56.png)

7.  「**See agent in Teams** 」オプションをクリックして、エージェントを
    Teams に追加します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

8.  これにより、Microsoft Teams でエージェントが開きます。「**This site
    is trying to open Microsoft
    Teams**」というポップアップで「**Cancel** 」を選択し、「**Use the
    Web App instead** 」オプションを選択してください。　

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  エージェントを追加するには、\[**Add** \] を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

10. 追加すると、エージェントを開くオプションが表示されます。「**Open**」を選択してください。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image61.png)

11. Teams からエージェントをテストします。

![](./media/image62.png)

12. Copilot Studio に戻り、Teams and Microsoft 365 Copilotチャネル
    ウィンドウを閉じます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

## 演習3 – 既存のSafe Travelsエージェントをテストする

この演習では、**Safe Travels**
エージェントをテストして、旅行の承認について尋ねられたときにどのように応答するかを確認します。

1.  Copilot Studio -\> Safe Travels
    エージェントに戻り、**Test** アイコンを選択してエージェントをテストします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

2.  Testウィンドウに +++ Need travel approval +++
    と入力し、\[**Enter**\] をクリックします。　

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image65.png)

3.  エージェントが、旅行の承認を得るために従うべき一般的な指示セットで応答していることがわかります。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image66.png)

## 演習4 – 企業固有のナーレジアセットで、エージェントを強化する

この演習では、Contoso に固有のナーレジアセットである**Travel
Policy** を追加します。

1.  エージェントのOverviewページで下にスクロールし、「**+ Add
    knowledge**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

2.  「**select to browse** 」オプションを参照します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

3.  **C:\Labfiles\Lab Files** フォルダーから、**Travel Policy.docx**
    を選択し、\[**Open**\] をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

4.  ファイルを追加するには、「**Add to agent** 」をクリックします。

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image70.png)

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image71.png)

5.  ファイルが追加されていることを確認してください。ステータスが「**In
    progress**」から「**Ready**」に変わるまでお待ちください。数分以上かかる場合は、「Ready」に変わるのを待っている間、次のステップに進むことができます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image73.png)

6.  次に、同じ質問でエージェントをテストし、追加されたナレッジ
    アセットから会社固有のポリシーで、エージェントが応答することを確認します。

## まとめ

このラボでは、Microsoft Copilot Studio の **Safe Travels エージェント
テンプレート**を使用して、**Business-to-Employee** **(B2E)**
向け出張支援エージェントを作成しました。エージェント
テンプレートでは、会話機能とナレッジ
ソースを事前に構成することで迅速な開始点を提供しながら、組織や法的要件に合わせて将来的にカスタマイズできることを確認しました。組み込みの**米国旅行
ウェブサイト**を**ナレッジ ソース**として使用し、natural
languageによる対話を通じて従業員の出張関連の質問にエージェントが回答する能力をテストしました。最後に、エージェントを
**Microsoft Teams and Microsoft 365 Copilot**に**公開し**、Teams
での可用性を検証し、従業員が日常的に使用するコラボレーション ツールから
Safe Travels
エージェントに直接アクセスして対話できることを確認しました。　　
