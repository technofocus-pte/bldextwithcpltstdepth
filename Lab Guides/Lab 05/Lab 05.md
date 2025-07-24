#  Laboratório 05 – Aprimorar o agente Safe Travels e implementar a orquestração de múltiplos agentes

## Objetivo

Você criou um agente chamado **Safe Travels** usando um modelo fornecido
no Copilot Studio em um laboratório anterior. Neste laboratório, você
entenderá como esse agente pode ser aprimorado para atender às
necessidades de clientes específicos.

No processo, você aprenderá os conceitos de criação de fluxo de agente e
orquestração de múltiplos agentes no Copilot Studio.

## Exercício 1 – Testar o agente Safe Travels existente

Neste exercício, testaremos o agente **Safe Travels** para ver como ele
responde quando questionado sobre a aprovação da viagem.

1.  Abra o **Copilot Studio** em
    +++https://copilotstudio.microsoft.com+++ em um navegador. Navegue
    até o ambiente **Dev One** e abra o agente **Safe Travels**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  Selecione o ícone **Test** para testar o agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  Digite +++Need travel approval+++ na janela Test e clique em
    **Enter**.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image3.png)

4.  Você pode ver que o agente responde com um conjunto de instruções
    generalizadas a serem seguidas para obter a aprovação da viagem.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image4.png)

## Exercício 2 – Aprimorar o agente com ativos de conhecimento específicos da empresa

Neste exercício, adicionaremos o ativo de conhecimento - **Política de
viagens** específica da Contoso.

1.  Na página Visão geral do agente, role para baixo e selecione **+ Add
    knowledge**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

2.  Clique na opção **select to browse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

3.  Na pasta **C:\Labfiles**, selecione **Travel Policy.docx** e clique
    em **Open**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

4.  Clique em **Add** para adicionar o arquivo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

> ![A screenshot of a computer error AI-generated content may be
> incorrect.](./media/image9.png)

5.  Certifique-se de que o arquivo foi adicionado. Aguarde até que o
    status mude de **In progress** para **Ready** antes de prosseguir
    para a próxima etapa.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

## Exercício 3 – Criar um Team e um canal no Microsoft Teams

Neste exercício, criaremos um Team e um canal no MS Teams para onde a
solicitação de aprovação de viagem será enviada.

1.  Abra o Microsoft Teams e selecione a opção **See all your teams** no
    painel esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

2.  Selecione **Create team** para criar uma nova equipe.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  Insira o nome da equipe como +++**HR Team**+++ e o nome do primeiro
    canal como +++**Travel Approval Channel**+++ e selecione **Create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  Selecione **Skip** na caixa de diálogo **Add members to HR Team**.

![A screenshot of a email AI-generated content may be
incorrect.](./media/image15.png)

Agora, a criação do Team e do canal está concluída.

## Exercício 4 – Criar um fluxo de agente

Neste exercício, criaremos um novo AgentFlow para postar a solicitação
de viagem no canal Teams

1.  Selecione **Flows** no painel esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  Selecione **New agent flow** para criar um novo fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

3.  Selecione **Add a trigger**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

4.  Selecione **When an agent calls the flow** em **AI capabilities**.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image19.png)

5.  Selecione **+ Add an input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

6.  Selecione **Number** e nomeie-o como +++**Employee ID**+++. Em
    seguida, selecione **+ Add an input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image22.png)

7.  Agora, selecione uma entrada **Text** e nomeie-a como
    +++**Purpose**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

8.  Selecione **Add an action** abaixo do nó do gatilho.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

9.  Pesquise por +++**Teams**+++ e clique em **See more** no grupo de
    ações **Teams**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

10. Selecione **Post message in a chat or channel**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image26.png)

11. Selecione **Sign in** e faça **login** usando suas credenciais.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

12. Selecione os detalhes abaixo

Post as – Selecionar **User**

Publicar – Selecionar **Channel**

Team – Selecione **HR Team**

Channel – Selecione **Travel Approval Channel**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image29.png)

13. No campo Mensagem, digite o seguinte

\`\`\`

> Travel Request from
>
> Employee ID - \<Employee ID\>
>
> Purpose - \<Purpose\>
>
> \`\`\`
>
> Substitua **\<Employee ID\>** e **\<Purpose\>** pelas variáveis de
> conteúdo dinâmico, **Employee ID** e **Purpose,** como nas capturas de
> tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

14. A aba **Parameters** agora terá a aparência abaixo.

![](./media/image32.png)

15. Feche a aba **Parameters**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

16. Adicione outra ação após o nó Post message.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image34.png)

17. Selecione **Respond to the agent** em **Skills**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image35.png)

18. Selecione Add an output. Nomeie-a como +++Output+++ e insira o valor
    como +++Request submitted+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

19. Clique em **Save draft** para salvar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

20. Depois que o fluxo for salvo, selecione **Publish**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

21. Certifique-se de que o fluxo foi publicado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

22. Clique na aba **Overview** do fluxo do agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

23. Selecione **Edit** e nomeie o fluxo como +++Request Travel Approval
    Flow+++ no painel **Details**. Selecione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

## Exercício 5 – Adicionar o fluxo do agente como uma ferramenta ao agente

Neste exercício, adicionaremos o fluxo de criação de agente ao agente
Safe Travels para aproveitar a funcionalidade do fluxo.

1.  No painel esquerdo, selecione **Agents**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

2.  Selecione o agente **Safe Travels.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

3.  Role para baixo na página **Overview** e selecione **Add tool**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

4.  Selecione o **Request Travel Approval Flow** criado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

5.  Selecione **Add to agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

6.  Depois de adicionado, o fluxo será listado na seção **Tools** da
    página **Overview** do **agente**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

## Exercício 6 – Criar Tópico

Neste exercício, criaremos um Tópico para usar o fluxo de aprovação de
viagem criado.

1.  Selecione **Topics** no menu superior. Selecione **+ Add a topic**
    -\> **Add from description with Copilot**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

2.  Insira os detalhes abaixo e selecione **Create**.

**Name** - +++Travel Approval+++

**Create a topic to** - +++This topic should get the Employee ID
(Number) and Purpose of travel (Text) details from the user and invoke
the Tool "Request Travel Approval Flow"+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

3.  O **Topic** é criado conforme abaixo.

![](./media/image50.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image51.png)

4.  Veja se o fluxo foi realmente acionado. Nesse caso, apenas um nó de
    mensagem informando que o fluxo foi acionado é adicionado. Nesse
    caso, exclua esse nó de mensagem e clique no ícone Adicionar um nó
    após o nó onde o **Propósito** é solicitado ao usuário.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

5.  Selecione **Add a tool** -\> **Request Travel Approval Flow**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  Adicione a variável **EmployeeID** para a variável de fluxo
    **Employee ID.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  Da mesma forma, adicione a entrada **Purpose of travel**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  Adicione um nó **Send a message** e adicione a Variável **Output**,
    como nas capturas de tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  Selecione **Save** e depois **Publish** para publicar o agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image60.png)

10. Selecione **Publish** na caixa de diálogo de confirmação.

![A close-up of a white background AI-generated content may be
incorrect.](./media/image61.png)

11. Selecione o ícone Teste e insira +++Travel Approval+++ e envie no
    painel de teste.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

12. Converse fornecendo os detalhes abaixo ao agente

> Employee ID – +++1234+++
>
> Purpose of travel - +++Client meeting for finalizing proposal of XYZ
> project+++

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image63.png)

13. Você receberá uma mensagem **Request submitted** do agente.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image64.png)

14. Abra o Canal de Teams e você verá os detalhes publicados lá para
    aprovação de Viagem.

![](./media/image65.png)

## Exercício 7 – Criar agente de gerenciamento de licenças

Neste exercício, criaremos um agente de gerenciamento de licenças que
pode ser usado para aprender sobre licenças, saldo de licenças de
funcionários e assim por diante.

1.  Na página inicial do Copilot Studio, selecione **Agents** -\> **+
    New agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

2.  Selecione **Skip to configure**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  Na página de configuração, insira os detalhes abaixo e selecione
    **Create**.

    - Name - +++Leave Manager Agent+++

    - Description - +++This agent is to track the leaves of all the
      employees, their leave balance and leave history to approve or
      reject any new leave requests.+++

    - Instructions - +++Track the leaves of employees. Track their leave
      balance. Apply/Reject leaves based on their balance.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  Depois que o agente for criado, role para baixo na página Visão
    geral e selecione **Add knowledge** na seção **Knowledge**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  Clique em **select to browse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  Selecione o arquivo **Leave balance Tracker** em C:\Labfiles e
    clique em **Open**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  Selecione **Add** para adicionar o rastreador ao agente.

![](./media/image72.png)

8.  O arquivo será adicionado. Aguarde até que o status seja **Ready**
    antes de prosseguir para a próxima etapa.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

9.  Selecione **+ Add a topic** -\> **Add from description with
    Copilot** na aba **Topics**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

10. Insira os detalhes abaixo e clique em **Create**.

- Name - +++Leave Balance Checker+++

- Create a topic to - +++Get the Employee ID from the user and check and
  reply with the leave balance based on the tracker added as knowledge
  source+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

11. Verifique se o tópico possui o nó para obter o ID do Funcionário, e
    clique em **Save**. Aqui, temos um nó para obter o ID do Funcionário
    e um nó de Mensagem informando que o saldo está sendo recuperado.

> Verifique o tópico uma vez e remova outros nós que foram criados além
> dos acima.

Então **Save** o tópico.

![](./media/image76.png)

12. Enviar uma mensagem +++Check Leave balance+++ no painel Teste.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image77.png)

13. Digite +++1234+++ para o ID do funcionário.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image78.png)

14. Verifique a resposta do agente. Ela é recuperada do ativo de
    conhecimento adicionado ao agente.

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image79.png)

15. Selecione **Publish** e aguarde até que o agente seja publicado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## Exercício 8 - Implementar orquestração multiagente no Copilot Studio

Em vez de depender de um único agente para fazer tudo ou gerenciar
agentes desconectados em silos, as organizações agora podem criar
sistemas multiagentes no Copilot Studio (preview), onde os agentes
delegam tarefas uns aos outros Isso inclui agentes criados com o
Microsoft 365 agent builder, Microsoft Azure AI Agents Service e
Microsoft Fabric. Agora, todos esses agentes podem trabalhar juntos para
atingir um objetivo comum: concluir tarefas complexas e críticas aos
negócios que abrangem sistemas, equipes e fluxos de trabalho.

Neste exercício, adicionaremos o agente de gerenciamento de licenças ao
agente Safe Travels, que pode ser usado para aprender sobre licenças ao
planejar uma viagem.

1.  Selecione o agente **Safe Travels** no Copilot Studio.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  Primeiro, testaremos este agente para ver quais informações pode
    fornecer sobre as licenças. No painel de teste, digite +++Check
    Leave balance+++ e pressione Enter.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

3.  Você pode ver que o agente responde com uma informação generalizada
    sobre como verificar o saldo de licenças. Ele também faz referência
    ao documento de Política de Viagem ao fornecer essa informação.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image83.png)

4.  Selecione a aba **Agents** no menu superior e selecione **+ Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

5.  Em **Choose how do you want to extend your agent**, selecione
    **Copilot Studio**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

6.  Na lista, selecione **Leave Manager Agent**. Ele só poderá ser
    adicionado se estiver publicado. Aguarde se estiver em processo de
    publicação.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

7.  Selecione **Add agent** para adicionar este agente ao **Safe
    Travels**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

8.  Aguarde alguns minutos após o agente ser adicionado e clique em
    **Publish**.

![](./media/image89.png)

9.  Aguarde mais alguns minutos após a publicação do agente e insira
    +++Check Leave balance+++ no painel Teste do **Safe Travels agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

10. Você pode ver que o agente **Leave Manager** é acessado
    automaticamente e o agente responde com a pergunta **Enter Employee
    ID** do **Leave Manager agent’s topic**.

11. Insira o ID do funcionário como +++1234+++ e você poderá ver que o
    agente responde com base no ativo de conhecimento do agente do Leave
    Manager.

![](./media/image91.png)

## Resumo

Neste laboratório, aprendemos como aprimorar um agente criado a partir
de um modelo para atender às necessidades individuais. Também aprendemos
a implementar a orquestração multiagente no Copilot Studio.
