**ラボ08 - Microsoft Copilot の会話型アクションの作成**

**ラボ期間**– 20分

**目的**

Microsoft Copilot
は、組織全体のコンテンツやリソースにアクセスするための、すぐに使えるエクスペリエンスを提供します。状況によっては、外部システムへの回答やインタラクションが必要になることもあります。Microsoft
Copilot Studio を使用すると、Copilot
プラグインとして公開できる会話型トピックを作成できます。テナント管理者がプラグインを承認すると、組織の
M365 Chat エクスペリエンスに追加できます。

組織が有効なライセンスを保有している場合、これらのアクションは運用環境の
Microsoft Copilot で利用できます。

このラボでは、会話型アクションの作成方法を学習します。

## **手順 1: Create a Conversational action**

1.  まだログインしていない場合は、テナントの資格情報を使用して
    **+++https://copilotstudio.microsoft.com/+++** にログインします。

2.  右上から環境を **Dev one** として選択します。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  左側のウィンドウから **\[Agent\]** を選択します。

4.  **Copilot for Microsoft 365**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

5.  **Actions**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

6.  **Add an action**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

7.  **New actionウィンドウでConversational**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

8.  アクションの名前を!!**Conversational
    action**!!.として提供する。**Create**を選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  準備ができたら、作成したアクションが作成キャンバスで開きます。**Topics**を選択する。

10. 開かない場合は、ページを更新して、\[**ライブラリ -\> 会話\]**
    の下にリストされているかどうかを確認します。

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image7.png)

11. **Conversational action**を開く。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

12. トピックに**!!Holidaylist!!**と名前を付ける。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

トリガーノードの説明には、会話型プラグインがユーザーにどのように役立つか、何ができるかを明確に説明する。このトピックは、ユーザーが2025年の祝日リストを見つけるのに役立つとします。

トリガーノードの説明に「+++**This plugin helps to retrieve the list of
holidays for the year 2025**+++」と入力する。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

この説明には機能的な目的があり、Microsoft Copilot
がプラグインを起動すかどうかを決定するために使用されます.

13. 休日のリストを含むメッセージノードを追加する.

- 2025年の祝日：

- New Year’s Day: Jan 1

- Martin Luther King Jr. Day: Jan 20

- Washington’s Birthday (Presidents’ Day): Feb 17

- Memorial Day: May 26

- Juneteenth National Independence Day: June 19

- Independence Day: July 4

- Labor Day: Sep 1

- Columbus Day / Indigenous Peoples’ Day: Oct 13

- Veterans Day: Nov 11

- Thanksgiving Day: Nov 27

- Christmas Day: Dec 25

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

14. **Save**をクリックしプラグインを保存する**。**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

![A screenshot of a chat box Description automatically
generated](./media/image13.png)

## **手順 2: 会話型アクションを Microsoft Copilot に公開する**

1.  会話型プラグインを公開すると、テナントのDataverseレジストリに新しいプラグインが作成されます。そこで利用可能になったら、テナント管理者がMicrosoft
    Copilotプラグインカタログでユーザーにプラグインを承認する必要があります。

2.  **Publish**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

3.  **Publish**を選択する。

![A screenshot of a computer program Description automatically
generated](./media/image15.png)

4.  **Publish latest content**ダイアログで**Publish**を選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image16.png)

5.  Publishの状況が画面に表示される。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

注: 公開はすぐに完了しますが、Microsoft Admin Center
で実際に利用可能になるまでには最大 4 時間かかる場合があります。

**重要: :** 管理者が管理センターに一覧表示するには、会社が有効な Copilot
ライセンスを保持している必要があります。

6.  管理者は、Microsoft 管理センターの \[**Settings**\] の
    \[**Integrations to be reviewed and approved**\] で **Dataverse** と
    **Microsoft Copilot Studio** の統合アプリを見つけることができます。

&nbsp;

7.  テナント管理者が Dataverse と **Microsoft Copilot Studio**
    の統合アプリを承認すると、そのアプリはユーザーの **Microsoft Copilot
    UI** のプラグインのリストに表示されます。

**要約:**

このラボでは、会話型アクションを作成し、それを公開する方法を学習しました。
