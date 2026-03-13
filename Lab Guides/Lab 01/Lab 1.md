# ラボ 1 - Copilot Studio Agent Builderを使用した AIアシスタントの設計

**目的**

このラボでは、**Copilot Studio Agent Builder**
を使用して、エージェントの目的、動作、トーンをnatural
languageで記述することで、カスタム会話エージェントを作成する方法を学習します。植物の手入れ、ベストプラクティス、そして日常生活における自然の重要性に焦点を当て、家庭菜園に関する専門的なアドバイスを提供する**ガーデニングアシスタント**を設計します。ラボの最後には、エージェントへの指示を反復的に改良し、機能的でドメイン固有のアシスタントを実現する方法を理解できるようになります。　

## 演習1: エージェントの作成

1.  ブラウザから+++<https://m365.cloud.microsoft/chat+++>をアクセスし、リンクを開き、資格情報を使用してログインします。

    - ユーザー名 -<+++@lab.CloudPortalCredential>(User1).Username+++

    - パスワード -<+++@lab.CloudPortalCredential>(User1).Password+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image1.png)

2.  **左**ペインから「**New agent** 」を選択してください。「**New
    agent**」オプションが**表示されない**場合は、**ブラウザ**を**更新し**、数分後にもう一度お試しください。完全に読み込まれるまで数分かかる場合があります。

![](./media/image2.png)

3.  「**Describe**」タブを選択します。

![](./media/image3.png)

4.  カスタムエージェントの定義を開始できます。テンプレートを選択するか、natural
    languageでエージェントの*説明*を入力することで、簡単にエージェントを定義することができます。まずは、次のような初期説明を入力してみましょう。

+++You are an expert gardener, and you help users to maintain and
improve their home garden providing detailed instructions and advice
about the best practices for home gardening.+++

![](./media/image4.png)

5.  指示を入力すると、初期の詳細が入力されます。

6.  必要に応じてエージェントの名前を変更できます。以下のプロンプトに従って名前を変更してください。

> +++Name it as “Gardening assistant”+++.

![](./media/image5.png)

7.  指示をさらに絞り込むよう求められた場合は、次の文を入力します。

+++Focus on suggesting ways to keep plants and flowers shining and
gorgeous+++

![](./media/image6.png)

8.  エージェントの作成に必要なすべての情報が揃うまで、エージェントビルダーとのやり取りを続けてください。次の文を入力してください。

9.  +++Focus on highlighting the importance of nature and plants/flowers
    to be present in every house!+++

> ![](./media/image7.png)
>
> ![](./media/image8.png)

10. 次に、エージェントトーンの指示を以下のように伝えます。

11. +++Use a professional, yet friendly, tone.+++

> ![](./media/image9.png)

11. エージェントを作成するには、右上の \[Create\] をクリックします。

![](./media/image10.png)

![](./media/image11.png)

12. エージェントが作成されたら、「**Go to agent** 」を選択します。

![](./media/image12.png)

13. 作成されたエージェントが開きます。

![](./media/image13.png)

> **警告**:
> エージェントが自動的に開かない場合は、ページを**更新**し、左側のペインから**作成したガーデニング
> エージェント**を選択してください。
>
> ![](./media/image14.png)

14. エージェントと会話するには、以下のようなプロンプトを提供します。

+++Give me tips to keep Rose plants fresh+++

![](./media/image15.png)

## まとめ：

このラボでは、Copilot Studio Agent Builder
エクスペリエンスを使用して、**ガーデニングアシスタントエージェント**を作成しました。シンプルなnatural-languageによる説明から始め、熟練した庭師としてのエージェントの役割を定義し、インタラクティブなプロンプトを通じて、エージェントの焦点、トーン、そして個性を段階的に洗練させてきました。植物を健康で生き生きと、そして美しく保つことに重点を置き、あらゆる家庭における植物や花の価値を強調しながら、専門的でありながら親しみやすいガーデニングアドバイスを提供するようにエージェントをカスタマイズしました。

エージェントを作成して起動した後、バラの苗を新鮮に保つためのヒントを求めるなど、実際のユーザープロンプトを使ってエージェントと対話することで、その動作を検証しました。このラボでは、会話型設計と反復的な指示の改良を活用することで、コードを記述することなく、Copilot
Studioを使用して目的主導型エージェントを迅速かつ直感的に構築できることを実証しました。
