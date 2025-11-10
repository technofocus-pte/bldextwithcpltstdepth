# ラボ 02 - Dynamics 365 Customerを構成する

## 目標

このラボでは、Azure でセキュリティ グループを作成し、Copilot Studio
の設定を更新してから、**Dynamics 365 Customer Service
の試用版**をアクティブ化します。

## タスク 1: Entra ID でセキュリティ・グループを作成し、Copilot Studio Authorsを構成する

1.  +++https://portal.azure.com/+++ Azure
    ポータルに移動し、ログイン資格情報を使用してログインします。

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  「Keep your account
    secure」ウィンドウで「Next」を選択し、指示に従います。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  携帯電話に Authenticator
    アプリをまだダウンロードしていない場合はダウンロードします。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  指示に従ってセットアップを完了します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

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

7.  左側のペインから、「**Manage -\> Groups**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  新しいセキュリティ グループを作成するには、\[**New group**\]
    を選択します。![A screenshot of a computer AI-generated content may
    be incorrect.](./media/image13.png)

9.  以下の詳細を入力してください

- Group type – **Security**を選択

- Group name – +++copilotagentsecurity+++ を入力してください

- Microsoft Entraのロールをグループに割り当てることができます –
  **Yes**を選択します

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. 「No owners selected」を選択し、「Add owners」ページからMOD
    Administratorを選択して、「Select」をクリックします。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. 同様に、「**No members selected**」を選択し、リストから **MOD
    Administrator**を追加して、「**Select**」をクリックします。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. 「**No roles selected**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. +++Global admin+++ を検索して選択し、**\[Select**\]
    を選択します。![A screenshot of a computer AI-generated content may
    be incorrect.](./media/image19.png)

14. すべての詳細を追加したら「**Create**」を選択し、確認ダイアログで「**Yes**」を選択します。

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. 成功メッセージが表示されたことを確認します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. 新しいタブから、+++https://power platform.microsoft.com
    にアクセスします。左側のペインで「**Manage**」を選択し、「**Tenant
    Settings**」オプションを選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. 利用可能なリストから「**Copilot Studio Authors**」を選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. **Edit**アイコンをクリックして設定を編集します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. 先ほど作成した **copilotagentsecurity**
    グループを検索して選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. 「**Save**」を選択して設定を保存します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

## タスク 2: Dynamics 365 Customer Service の試用版にサインアップする

1.  +++https://dynamics.microsoft.com/en-us/customer-service/overview/+++
    にログインします

2.  プロンプトが表示されたら、\[**Home**\] タブ**から Office 365
    テナントの詳細**を使用してログインします。

3.  「**Try for free**」をクリックします。

![](./media/image28.png)

4.  \[**Resources**\] タブから **Office 365
    管理者ユーザー名**を入力し、チェック ボックスをオンにして、\[**Start
    your free trial**\] をクリックします。

![](./media/image29.png)

5.  Countryを「**United States**」に入力し、**Phone
    number**を入力して「**Submit**」をクリックします。

![](./media/image30.png)

6.  Engage
    顧客向けの試用版を起動するオプションが表示された場合は、**「Launch
    Trial」**をクリックします。

![](./media/image31.png)

7.  アクティブ化されると、カスタマー サービス ワークスペースが開きます。

![](./media/image32.png)

## 要約

このラボでは、**ラボ 04 (エージェントを Dynamics 365 Customer Service
アプリに統合し、ライブ エージェントへの自動ケース
エスカレーションを実装する)** で使用される Dynamics 365 Customer Service
をアクティブ化しました。
