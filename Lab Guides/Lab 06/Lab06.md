# **Lab 06_Teams からの Microsoft Copilot Studio コパイロットの作成とデプロイ**

**ラボ期間**– 30分

**目的:**

このラボでは、Microsoft Teams に Copilot Studio
アプリをインストールし、チームに新しい Copilot
を作成してからテストします。

## **手順 1: Microsoft Teams に Copilot Studio アプリをインストールする**

1.  Select **Start** menu from the
    VMから**Start**メニューを選択して+++teams+++を検索し、**Microsoft
    Teams app**を選択します。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  **Resourcesタブから資格情報を使用してサインインする。**

![A screenshot of a sign in Description automatically
generated](./media/image2.png)

3.  Click on **Apps**をクリックする。+++**Copilot
    Studio**+++を検索し**Microsoft Copilot
    Studioを選択して、Add**をクリックする。

**注:** Copilot Studio が見つからない場合は、**Power Virtual
エージェント**を検索して選択し、追加する必要があります。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![](./media/image4.png)

4.  **Open**をクリックする。

![A screenshot of a phone Description automatically
generated](./media/image5.png)

5.  **Start now**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

## **手順 2: チームで新しい副操縦士を作成する**

1.  **Office 365** テナントの資格情報を使用して **Teams**
    に**サインインします**。

> ![A screenshot of a sign in Description automatically
> generated](./media/image7.png)

1.  \[アプリ**\]をクリックします**。+++Copilot Studio+++
    を検索し、**Microsoft Copilot Studio** を選択して \[追加**\]
    をクリックします**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![A screenshot of a phone Description automatically
generated](./media/image4.png)

**重要:** Copilot Studioが見つからない場合は、**+++Power
Virtualエージェント+++**を検索して選択し、追加する必要があります。

![A screenshot of a search engine Description automatically
generated](./media/image8.png)

![A screenshot of a computer Description automatically
generated](./media/image9.png)

1.  **Start now**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

2.  **Contosoを選択してContinue**をクリックする。

![A screenshot of a chatbot Description automatically
generated](./media/image10.png)

![A screenshot of a chatbot Description automatically
generated](./media/image11.png)

**重要:** この手順には約 10
分かかる場合があります。時間がかかりすぎる場合は、閉じて、左側のウィンドウで
アプリから Copilot Studio または Power Virtual Agents を選択し、手順 4
をやり直します。

1.  \[Create a copilot\] 画面で、コパイロットの名前を **+++HR Support
    Copilot+++** として指定し、\[**Create**\] をクリックします。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

3.  **Your chatbot is provisioned**という成功メセッジが表示されます。

![](./media/image13.png)

## **手順 3: 一般的な休暇クエリの従業員の休暇トピックを作成する**

1.  左側のペインから「**トピック」をクリックします** 。\[**+
    新しいトピック -\> 空白から\]** をクリックします**。**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  ここで \[トリガー フレーズ\] ウィンドウを**閉じます**.

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

1.  \[Details**\]** アイコンをクリックします。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

1.  \[**Details**\] ウィンドウで、名前を +++Employee time off+++
    と指定し、\[**Description**\] を \[+++Employee time off topic for
    common time-off queries+++\] として指定します。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

3.  Detailsウィンドウを**Close**する。![A screenshot of a computer
    Description automatically generated](./media/image18.png)

4.  **Save**をクリックする。

![A screenshot of a chat Description automatically
generated](./media/image19.png)

5.  **Trigger phasesをクリックする。**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

1.  トリガーフレーズ**+++I need help with time
    off+++**を追加し、+をクリックします **。**

![](./media/image21.png)

6.  以下のトリガーフレーズを追加する。

- +++**Need information on time off**+++

- +++**How many days of paid vacation do I have**+++

- +++**What are the national holidays**+++

- +++**I need extended leave**+++

![A screenshot of a computer Description automatically
generated](./media/image22.png)

トリガーフレーズウィンドウを閉じる。

7.  メセッジノードを追加して+++I can help with questions related to
    time-off*+++*のテキストを入力する。

> ![A screenshot of a chat Description automatically
> generated](./media/image23.png)

8.  人事担当者であれば、休暇に関する最も一般的な質問は有給休暇と祝日に関するものであることをご存知でしょう。ユーザー回答オプション付きの質問ノードを追加すると、トピックは回答ごとに自動的に分岐します。

9.  メッセージノードの下にある（+）アイコンを選択し、「**Ask a
    question**」を選択してトピックに質問ノードを追加します。「**Ask a
    question**」テキストボックスに「どのような情報をお探しですか？」と入力する。

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)

10. **Options for userの下に**、二つのオプションとして +++Paid
    vacation*+++* と +++National Holidays*+++* を追加する。

> ![A screenshot of a questionnaire Description automatically
> generated](./media/image25.png)

11. ユーザーの選択は変数に格納され、トピックはユーザーが選択したオプションに基づいて分岐します。変数の名前を変更して、トピック内で変数を追跡しやすくすることができます。

12. 変数の **\[Save response as**\]
    で、鉛筆アイコンを選択して変数のプロパティを編集します。

13. \[**変数のプロパティ**\] ウィンドウが開きます。変数の名前を
    +++TimeoffType+++ に変更します。**\[変数のプロパティ**\]
    ウィンドウを閉じると、オーサリング キャンバスに変更が反映されます.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

14. 有給休暇ブランチのメッセージ
    ノードを追加し、次のメッセージをユーザーに送信します:
    +++有給休暇の場合は、www.contoso.com/HR/PaidTimeOff+++
    にアクセスして休暇申請を送信する。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

15. 「National Holidays**」パスに**
    、次のテキストを含むメッセージノードを追加します:

2025年の祝日:

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

![](./media/image28.png)

16. **Save**をクリックする

![A screenshot of a computer Description automatically
generated](./media/image29.png)

![A screenshot of a chat window Description automatically
generated](./media/image30.png)

## **手順 4: 予想される動作について副操縦士をテストする**

1.  画面の上部にある **Copilot/Power Virtual Agent アイコンを選択して**
    、テスト Copilot キャンバスを起動します.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

2.  Copilotチャットに**I need time off information**を入力する。 

3.  \[**有給休暇**\] を選択**します**。

4.  弊社の設定に従って応答を受け取ります

> ![A screenshot of a chat Description automatically
> generated](./media/image32.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)
>
> **要約:**
>
> このラボでは、Copilot Studio アプリを Teams に追加し、Teams
> でクラシック ボットを作成する方法を学習しました。
