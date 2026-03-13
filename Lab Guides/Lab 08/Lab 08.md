# Laboratório 8 – Criar um agente no Copilot Studio com o Dataverse MCP Server

Crie e configure um agente do Copilot no Copilot Studio com integração
ao Dataverse MCP Server para otimizar fluxos de trabalho de negócio.

Após concluir este laboratório, os participantes serão capazes de criar
e configurar um agente do Copilot no Copilot Studio, integrar o
Dataverse MCP Server para ler e atualizar informações de conta da tabela
Account e Contact, estruturar respostas do agente para maior clareza e
valor comercial e aplicar essas habilidades para resolver desafios
comerciais comuns.

## Tarefa 1: Criar e configurar o agente do Copilot 

Crie um agente do Copilot que se conecte ao Dataverse por meio de um MCP
Server para acesso contínuo aos dados.

Nesta seção, você aprenderá a criar um novo agente do Copilot no Copilot
Studio, configurá-lo com instruções adequadas e sugestões de prompts e
integrar o Dataverse MCP Server para conectividade de dados em tempo
real.

1.  Faça login no Copilot Studio em
    +++https://copilotstudio.microsoft.com+++ usando suas credenciais de
    login, se ainda não tiver feito isso, e certifique-se de que está no
    ambiente Dev One.

![](./media/image1.png)

2.  Selecione o bloco **Create an agent** para criar um novo agente.

![](./media/image2.png)

3.  Após o agente ser provisionado, selecione Edit no painel
    **Details**.

![](./media/image3.png)

4.  Insira os detalhes abaixo e selecione **Save**.

- Name - +++Contoso Agent+++

- Description - +++This agent will help Contoso sales reps update their
  accounts and contacts using the Dataverse MCP Server+++

> ![](./media/image4.png)

5.  **Edite** Instructions, insira o conjunto de instruções abaixo e
    selecione **Save**.

This agent will: Read accounts and contact information from the Account
and Contact Tables in Dataverse using the Dataverse MCP Server. Update
accounts and contact information from the Account and Contact Tables in
Dataverse using the Dataverse MCP Server. Create new accounts and
contact information in the Account and Opportunity Tables in Dataverse
using the Dataverse MCP Server. Do not use outside knowledge. Only use
the Dataverse MCP Tool to create, read, update and delete.

![](./media/image5.png)

![](./media/image6.png)

6.  Role para baixo e selecione **+ Add suggested prompts** na seção
    Suggested prompts.

![](./media/image7.png)

7.  Adicione os seguintes prompts e, em seguida, clique em **Save**.

- **Title**: +++Account Search+++

> **Prompt**: +++List all accounts in Redmond+++

- **Title**: +++Contact Search+++

> **Prompt**: +++List all contacts from Coho Winery+++

![](./media/image8.png)

8.  Na seção Tools, selecione **+ Add tool**.

![](./media/image9.png)

9.  Selecione a guia **Model Context Protocol**, pesquise por
    +++**Dataverse MCP Server**+++ e selecione **Microsoft Dataverse MCP
    Server**.  
    Observação: Selecione a opção que não está em Preview. Não selecione
    **Microsoft Dataverse MCP Server (Preview)**.

![](./media/image10.png)

10. Selecione **Add and configure**.

![](./media/image11.png)

**Observação:** o Dataverse MCP Server permite acesso às tabelas do
Dataverse usando linguagem natural. Há dados de exemplo nas tabelas
Accounts e Contacts que serão utilizados. As ferramentas disponíveis
são: list tables, describe table, read data, create record, update
record, list prompts, execute prompt, list knowledge sources e retrieve
knowledge.

11. Revise as ferramentas disponíveis do Dataverse MCP Server. Você pode
    selecionar e desmarcar quais ferramentas estarão disponíveis para o
    Agente do Copilot. Quando uma ferramenta é executada, a lista é
    atualizada dinamicamente a partir do MCP Server. Por esse motivo,
    não é possível chamar um MCP Server a partir de um tópico.

![](./media/image12.png)

12. Insira +++List the accounts in the state of WA+++ no painel **Test**
    e clique em **Send**.

![](./media/image13.png)

13. Na primeira execução, você verá uma caixa de diálogo de
    consentimento, pois, por padrão, a ferramenta está configurada para
    usar “End user credentials”. Clique em **Allow** para continuar.

![](./media/image14.png)

14. Observe a sequência de ações executadas e a saída retornada pelo MCP
    Server.

![](./media/image15.png)

![](./media/image16.png)

15. Se você clicar na ferramenta que foi usada, poderá ver as entradas e
    saídas da ferramenta.

![](./media/image17.png)

## Tarefa 2 – Estruturar respostas do agente com prompts personalizados

Crie prompts personalizados para garantir respostas consistentes e
estruturadas do agente, fornecendo informações relevantes para o
negócio.

1.  Se você realizou alguns testes diferentes no Copilot, pode ter
    percebido que são retornados atributos diferentes para accounts e
    contacts. Caso deseje uma resposta mais estruturada, você pode criar
    um **prompt** em **Tools**. Na guia **Tools**, clique em **+ Add a
    tool** e depois em **+ New tool**.

![](./media/image18.png)

![](./media/image19.png)

2.  Selecione Prompt.

![](./media/image20.png)

3.  Renomeie o **nome do prompt** na parte superior para +++Show Account
    Details+++ .

Em seguida, nas **Instructions**, insira +++Find account which
contains+++ e clique em **+ Add content** para passar o nome da conta
que está sendo pesquisada. Selecione **Text** como entrada e nomeie como
+++**Account Name**+++. Clique em **Close**.

> ![](./media/image21.png)

![](./media/image22.png)

4.  Agora podemos capturar campos específicos do Dataverse para exibir
    aos usuários finais no chat. Clique novamente em Instructions,
    insira +++and find relevant details like:+++ e clique em **+ Add
    content**. Desta vez, selecione **Dataverse** e alguns dos campos da
    tabela **Account** que consideramos relevantes para os usuários
    finais visualizarem sobre a conta.

![](./media/image23.png)

5.  Selecione os seguintes itens clicando no menu suspenso: **Account
    Name**, **Account Number**, **Address 1**, **Annual Revenue**,
    **Email** e **Main Phone**. Clique em **Add** e, em seguida, em
    **Save**.

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

6.  Selecione **Add and configure**.

![](./media/image27.png)

7.  Agora podemos testar o prompt. Vamos voltar ao agente e testar
    novamente. Acesse o painel Test.

8.  Insira +++Show account Details for Fourth Coffee+++ e clique em
    **Send**. Você poderá observar que a resposta é apresentada de forma
    estruturada, utilizando o prompt personalizado criado.

![](./media/image28.png)

## Resumo

Neste laboratório, você construiu um Agente do Copilot no Microsoft
Copilot Studio integrado ao **Dataverse MCP Server**, permitindo acesso
seguro e gerenciamento de dados corporativos por meio de linguagem
natural. Você configurou o agente para ler, criar e atualizar registros
em tabelas do Dataverse, como **Accounts, Contacts** e
**Opportunities**, sem depender de conhecimento externo ou APIs
personalizadas.

Você também aprendeu a **estruturar respostas do agente** usando prompts
personalizados, garantindo saídas consistentes e orientadas ao negócio,
que destacam os campos de dados mais relevantes para os usuários finais.
Ao final do laboratório, você é capaz de projetar um agente que
simplifica fluxos de trabalho de vendas e gerenciamento de contas,
entrega insights claros e estruturados e demonstra como agentes
habilitados por MCP podem resolver desafios reais de negócio com dados
corporativos em tempo real.
