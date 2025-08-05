# ラボ 03 – テンプレートから Safe Travels エージェントを作成する

**客観的**

エージェントテンプレートは、カスタムエージェントの使用を開始する際に役立つように設計されています。エージェントテンプレートの使用に関するすべての安全性と法的影響を評価し、ビジネスに合わせてカスタマイズする責任はお客様にあります。

Safe Travels エージェントテンプレートから構築されたエージェントは、企業の従業員に出張支援を提供するために設計された、企業対従業員 (B2E) エージェントです。このエージェントは、従業員が次の出張に向けて十分な準備を行い、十分な情報を得られるように支援します。このエージェントは自然言語処理を使用して会話型インターフェースを提供し、従業員が必要な情報に簡単かつ直感的にアクセスできるようにします。ただし、エージェントが使用するデフォルトのウェブサイトは現在、米国の旅行先のみをカバーしています。デフォルトのウェブサイトを独自のナレッジソースに置き換えることができます。

このラボでは、Safe Travels テンプレートからエージェントを作成し、ラボ 05 で拡張します。

## 演習 1: テンプレートから Safe Travels エージェントを作成する

この演習では、Safe Travelsエージェントテンプレートを使用してCopilot Studioでエージェントを作成します。

1.  ブラウザから+++https://copilotstudio.microsoft.com+++にログイン
    します。「Start free trial」ページが開きます。国を選択し、 **「Start
    free trial」**をクリックします。

    ![](./media/image1.png)

2.  **Dev One環境**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  新しいエージェントを作成するには、左側のペインから**\[+
    Create\]**を選択 します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  **\[Start with an agent template\]**の下で、 **\[Safe
    Travels\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

5.  Safe Travels
    テンプレートは、会社の従業員に旅行支援を提供するように設計された新しいエージェントを作成します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  設定ページを参照してください。 **「Knowledge」**の下に、 **US Travel
    Website
    が**ナレッジソースとして既に追加されていることがわかります。必要に
    応じて編集できます。ここでは、同じウェブサイトを使用しています。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  **「Create」**を選択して、Safe
    Travelsエージェントを作成します。ここでは
    何も変更せず、テンプレートをそのまま使用します。エージェントは、
    ユーザーの要件に応じていつでもアップグレードできます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  **エージェントが作成され**、自動的に開き、**Overviewページ**が表示されます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

9.  Testペインで、「 +++How to apply for passport?+ ++」と入力し、
    **\[Send\]**をクリックします。

    Testパネルはデフォルトで開いています。開いていない場合は、右上のTest
アイコンをクリックしてください。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

10. エージェントがナレッジソースからパスポートの申請方法に関する情報を
    提供していることがわかります。

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image10.png)

## 演習 2: エージェントを Teams と Microsoft 365 Copilot に公開する

この演習では、Copilot Studioで作成したエージェントをMicrosoft TeamsおよびMicrosoft 365 Copilotチャネルに公開します。

1.  エージェント・ページの右上から**\[Publish\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  確認ダイアログで**「Publish」**を選択します。

    ![](./media/image12.png)

3.  上部のナビゲーション バーから**\[Channels\]**を選択します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

4.  利用可能なチャネルの一覧から、**Teams and Microsoft 365
    Copilot**を選択 します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  **Add channel**を選択します。

    ![](./media/image15.png)

6.  **「See agent in Teams」オプション**をクリックして、エージェントを
    Teams に追加します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

7.  これにより、Microsoft Teams でエージェントが開きます。
    **「Add」**を選択 してエージェントを追加します。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  追加すると、エージェントを開くオプションが表示されます。
    **「Open」**を 選択してください。

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image19.png)

9.  Teams からエージェントをテストします。

    ![](./media/image20.png)

10. Copilot Studio に戻り、 Teams と Microsoft 365 Copilot
    チャネル・ウィンドウを閉じます。

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)


