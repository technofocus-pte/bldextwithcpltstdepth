# ラボ 8 - Copilot Studio で Dataverse MCP Server を使用して、エージェントを作成する

Copilot Studio で Dataverse MCP Server 統合を使用して Copilot Agent
を作成および構成し、ビジネス ワークフローを効率化します。

このラボを完了すると、参加者は Copilot Studio で Copilot Agent
を作成して構成し、Dataverse MCP Server を統合してAccount
とContactのテーブルからアカウント情報を読み取って更新し、明確さとビジネス価値のために、エージェントの応答を構造化し、これらのスキルを適用して一般的なビジネス課題を解決できるようになります。

## タスク 1: Copilot エージェントの作成と構成

シームレスなデータ アクセスを実現するために、MCP サーバーを介して
Dataverse に接続する Copilot Agent を構築します。

このセクションでは、Copilot Studio で新しい Copilot Agent
を作成し、適切な手順と推奨プロンプトを使用して設定し、ライブ
データ接続のために Dataverse MCP Server を統合する方法を学習します。

1.  まだログインしていない場合は、ログイン資格情報を使用して
    +++https://copilotstudio.microsoft.com+++ で Copilot Studio
    にログインし、Dev One 環境にいることを確認します。

![](./media/image1.png)

2.  新しいエージェントを作成するには、\[**Create an agent**\]
    タイルを選択します。

![](./media/image2.png)

3.  エージェントがプロビジョニングされたら、**Details**ペインで \[Edit\]
    を選択します。

![](./media/image3.png)

4.  以下の詳細を入力し、「**Save**」を選択します。

- Name - +++Contoso Agent+++

- Description - +++This agent will help Contoso sales reps update their
  accounts and contacts using the Dataverse MCP Server+++

> ![](./media/image4.png)

5.  手順を**編集し**、以下の手順を入力して「**Save**」を選択します。

This agent will: Read accounts and contact information from the Account
and Contact Tables in Dataverse using the Dataverse MCP Server. Update
accounts and contact information from the Account and Contact Tables in
Dataverse using the Dataverse MCP Server. Create new accounts and
contact information in the Account and Opportunity Tables in Dataverse
using the Dataverse MCP Server. Do not use outside knowledge. Only use
the Dataverse MCP Tool to create, read, update and delete.

![](./media/image5.png)

![](./media/image6.png)

6.  下にスクロールして、「Suggested prompts」セクションで「**+ Add
    suggested prompts**」を選択します。

![](./media/image7.png)

7.  次のプロンプトを追加し、「Save」をクリックします。

- **Title**: +++Account Search+++ **Prompt**: +++List all accounts in
  Redmond+++

- **Title**: +++Contact Search+++ **Prompt**: +++List all contacts from
  Coho Winery+++

![](./media/image8.png)

8.  Toolsセクションから **+ Add tool**を選択します。

![](./media/image9.png)

9.  \[**Model Context Protocol**\] タブを選択し、\[+++Dataverse MCP
    Server+++\] を検索して、\[**Microsoft Dataverse MCP Server**\]
    を選択します。

注: Preview版ではないものを選択してください。Microsoft Dataverse MCP
Server (**Preview**) は選択しないでください。

![](./media/image10.png)

10. \[**Add and configure**\]を選択します。

![](./media/image11.png)

**注記：**Dataverse MCP
Serverを使用すると、Dataverse内のテーブルにnatural
languageでアクセスできます。AccountsとContactsのテーブルにはサンプルデータが用意されており、これらを使用します。利用可能なツールは、list
tables、describe table、read data、create record、update record、list
prompts、execute prompt、list knowledge sources及びretrieve
knowledgeです。

11. Dataverse MCP
    Serverで利用可能なツールを確認してください。エージェントが利用できるツールを選択または選択解除できます。ツールを実行すると、リストはMCPサーバーから動的に更新されます。このため、TopicからMCPサーバーを呼び出すことはできません。

![](./media/image12.png)

12. **Test**ペインに +++List the accounts in the state of WA+++
    と入力し、\[**Send**\] をクリックします。

![](./media/image13.png)

13. 初回実行時には、デフォルトでツールが「エンドユーザーの認証情報」を使用するように設定されているため、同意ダイアログが表示されます。続行するには「**Allow**」をクリックしてください。。

![](./media/image14.png)

14. 実行される一連のアクションとMCPサーバーからの出力を確認します。

![](./media/image15.png)

![](./media/image16.png)

15. 使用されたツールをクリックすると、そのツールのInputsとOutputsが表示されます。

![](./media/image17.png)

## タスク2: カスタムプロンプトを使用して、エージェントの応答を構成する

カスタム
プロンプトを作成して、エージェントからの一貫性のある構造化された応答がビジネス関連情報として提供されるようにします。

1.  Copilotで様々なテストを試したことがある方は、アカウントと連絡先で異なる属性が返されることに気付いたかもしれません。より構造化された応答が必要な場合は、「**Tools**」で**プロンプト**を作成できます。「**Tools**」タブで、「**+
    Add a tool**」をクリックし、「**+ New tool**」をクリックします。

![](./media/image18.png)

![](./media/image19.png)

2.  Promptを選択します。

![](./media/image20.png)

3.  上部の**プロンプト名**を +++Show Account Details+++ に変更します。

次に、**instructions**に+++ Find account which contains
+++と入力し、「**+ Add
content**」をクリックして、検索対象のアカウント名を入力します。入力欄に「**Text**」を選択し、「+++
**Account Name** +++」と入力します。「**close**」をクリックします。

> ![](./media/image21.png)

![](./media/image22.png)

4.  4\.
    これで、Dataverseから特定のフィールドを取得して、チャットでエンドユーザーに表示できるようになります。手順に戻り、+++and
    find relevant details like: +++を入力し、**+ Add
    content**クリックします。今回は**Dataverse**を選択し、エンドユーザーが**Account**について知りたいと思われるアカウントテーブルのいくつかのフィールドを選択します。　　

![](./media/image23.png)

5.  ドロップダウンをクリックして、以下の項目を選択しましょう：**Account
    Name**、**Account Number**、**Address 1**、**Annual
    Revenue**、**Email** 及び**Main
    Phone**。「**Add**」をクリックし、「**Save**」をクリックします。

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

6.  \[**Add and configure**\]を選択します。

![](./media/image27.png)

7.  これでプロンプトをテストできます。エージェントに戻ってもう一度テストしてみましょう。テストペインに移動してください。

8.  +++Show account Details for Fourth
    Coffee+++と入力し、「**Send**」をクリックします。カスタムプロンプトが作成された構造化レスポンスにレスポンスが含まれていることがわかります。　

![](./media/image28.png)

## まとめ

このラボでは、Microsoft Copilot Studio で Copilot Agent
を構築します。このエージェントは **Dataverse MCP Server**
と統合し、natural
languageを使用してビジネスデータに安全にアクセスし、管理します。エージェントは、外部の知識やカスタム
API に依存せずに、**Accounts、Contacts、Opportunities**などの Dataverse
テーブル全体のレコードを読み取り、作成、更新するように構成します。

また、カスタムプロンプトを使用して、**エージェントの応答を構造化する**方法も学習します。これにより、エンドユーザーにとって、最も関連性の高いデータフィールドを表示する、一貫性のあるビジネスフレンドリーな出力を実現できます。ラボの終了時には、営業およびアカウント管理ワークフローを効率化し、明確で構造化されたインサイトを提供するエージェントを設計できるようになり、MCP
を活用したエージェントが実際のエンタープライズデータを使用して、実際のビジネス課題を解決する方法を実証できるようになります。
