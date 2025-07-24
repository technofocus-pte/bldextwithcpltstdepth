# Laboratório 04 - Integrar um agente ao aplicativo Dynamics 365 Customer Service e implementar o escalonamento automático de casos para um agente humano

## Objetivo

Este laboratório detalha as etapas para escalonar uma conversa de um
agente virtual para um agente humano.

\[!Alerta\] **Importante:** Este laboratório só poderá ser executado se
a versão de avaliação do Dynamics 365 tiver sido habilitada conforme o
**Laboratório 02 - Configurar o Dynamics 365 Customer Service**

## Exercício 1: Configurar o espaço de trabalho do Dynamics 365 Customer Service

### Tarefa 1: Configurar a extensão do Omnichannel Power Virtual Agent

1.  Abra o link
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++>
    e clique em **Get it now** na página Extensão do Omnichannel Power
    Virtual Agent.

![](./media/image1.png)

2.  Entre com as credenciais do locatário na aba **Resources**.

![](./media/image2.png)

3.  Clique em **Get it now**.

![](./media/image3.png)

4.  Selecione o **CustomerService Trial** em **Select an environment**,
    marque as caixas de seleção e clique em **Install**.

![](./media/image4.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

## Tarefa 2: Configurar as definições de pesquisa no centro de administração do Power Platform

1.  Acesse +++<https://admin.powerplatform.microsoft.com/+++> usando as
    informações do seu locatário. Selecione **Manage** no painel
    esquerdo e, em seguida, selecione o E**nvironment** como
    **CustomerService Trial** na lista de ambientes.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  Selecione **Settings** no painel superior.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  Selecione **Product** -\> **Features**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  Altere para **On** as opções **Dataverse Search** e **Single table
    search** e selecione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

## Exercício 2: Criar um agente

1.  Na página inicial do Copilot Studio,
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/),
    selecione o Environment **CustomerService Trial** no canto superior
    direito.

![](./media/image10.png)

2.  Selecione **Agents**  no painel esquerdo. Clique em **+ New Agent**
    para criar um novo agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  Na área de texto Digite sua mensagem, digite +++**You are a customer
    service agent who helps in identifying stores nearby.**+++ E clique
    em **send**.

![](./media/image12.png)

4.  O agente pode sugerir um **name** para o Agente que está sendo
    criado. Aceite ou sugira um novo nome.

5.  Digite a mensagem +++**Maintain a polite tone**+++ e clique em
    **send**.

![](./media/image13.png)

6.  Clique em **create**.

![](./media/image14.png)

7.  O agente criado abre com uma mensagem: **Your agent is ready**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## Exercício 3: Conectar o copilot ao Dynamics 365 Customer Service e configure o tópico Escalar

### Tarefa 1: Configurar o tópico Escalar

Aqui, estamos focando em demonstrar o conceito de escalonamento para um
agente humano. Portanto, iremos direto ao ponto sem criar nenhum outro
tópico novo.

1.  Selecione a aba **Topics** e, em seguida, a aba **System**.
    Selecione o tópico **Escalate**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  Selecione o nó da mensagem do tópico e substitua o conteúdo
    existente por +++You will be transferred to a live agent shortly+++

![](./media/image17.png)

3.  Clique no símbolo + para adicionar um nó ao lado do nó Mensagem.

4.  Selecione **Topic management** -\> **Transfer conversation**.

![](./media/image18.png)

5.  Insira a mensagem +++The customer wants to talk to a live agent+++
    no nó **Transfer conversation**.

![ ](./media/image19.png)

6.  **Save** o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  **Publish**  o agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### Tarefa 2: Conectar o copilot ao Dynamics 365 Customer Service

1.  Após a publicação, no canto superior direito da página do copilot,
    clique em **Settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  Selecione **Security** e **Authentication** em **Security**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  Selecione a opção **No authentication** e clique em **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  Selecione **Save** na caixa de diálogo de confirmação.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  Feche o painel **Settings**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image26.png)

6.  Clique em **Channels** (se os Canais não estiverem visíveis, clique
    em +1 para visualizar a opção **Channels)**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  Selecione **Dynamics 365 Customer Service** no painel **Customer
    engagement hub**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  Na página **Dynamics 365 Customer Service**, clique em **Connect**.

![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  Após receber uma mensagem **successfully connected,** clique em
    **Close**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## Exercício 4: Criar fluxo de trabalho e canal no Dynamics 365 admin center

### Tarefa 1: Gerenciar um usuário no Omnichannel para Atendimento ao Cliente

1.  Efetue login em
    +++[https://admin.powerplatform.microsoft.com+++](https://admin.powerplatform.microsoft.com+++/)
    usando suas credenciais de locatário de administrador. Selecione
    **Manage** no painel esquerdo. Selecione Ambiente **CustomerService
    Trial** em **Environments**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  Clique no **valor da URL** em **Environment URL**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  Selecione **Customer Service workspace** na barra de cabeçalho.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  Isso abrirá a página **Apps**. Selecione **Customer Service admin
    center**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  Isso abre a página **Dynamics 365 Customer Service admin center**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

### Tarefa 2: Configurar fluxo de trabalho

1.  Na página do centro de administração, selecione **Workstreams** em
    **Customer support** no painel esquerdo e, em seguida, selecione a
    opção **+ New workstream**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

2.  Selecione **Inbound**

![](./media/image37.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

3.  Preencha os detalhes abaixo, role para baixo e clique em **Create**.

    - Name - +++**New Workstream**+++

    - Owner – **MOD Administrator** (Selecionado por padrão)

    - Type – **Messaging**

    - Channel – **Chat**

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image39.png)

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  Depois que o fluxo de trabalho for criado, clique em **Set up chat**
    para configurar o canal do chat.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  Na tela **Live chat setup – Channel details**, preencha os detalhes
    abaixo.

    - Name - +++**Chat Channel**+++

    - Language – **English - United States**

![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  Role para baixo e clique em **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  Aceite os padrões nas próximas 2 páginas até chegar à tela **Chat
    widget**. Na tela **Live chat setup – Chat widget**, informe o nome
    +++**Store Locator Assistant**+++, aceite os outros padrões e clique
    em **Next**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  Na tela **Live chat setup – Behaviors**, aceite os padrões e clique
    em **Next**.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  Na tela **Live chat setup – User features**, desative as opções
    **File attachment** e **Voice and video calls** e clique em
    **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. Aceite o valor padrão na tela de Notificação e clique em **Next**.

11. Na tela **Live chat setup – Review and finish**, selecione **Create
    channel**.

![](./media/image47.png)

12. **Copy** o valor do widget que aparece na tela **Live chat setup –
    Success** em um bloco de notas para adicioná-lo a uma página da web
    nos próximos exercícios. Em seguida, clique em **Done** para
    concluir a configuração.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### Tarefa 3: Adicionar o agente ao fluxo de trabalho

1.  De volta à página **New Workstream**, role para baixo e clique em
    **+ Add bot** na seção **Bot**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  Na lista de copilots na tela **Add bot**, selecione o agente **Store
    Locator Assistant** e clique em **Connect**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  Certifique-se de que o bot seja adicionado ao fluxo de trabalho,
    como na captura de tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  No painel esquerdo, selecione **AI Agents**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  Certifique-se de que o agente **Store locator** esteja conectado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## Exercício 5: Criar uma página da web e testar a escalonamento para o agente

1.  Efetue login em +++<https://make.powerpages.microsoft.com/+++>
    usando suas credenciais de administrador de locatário.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  Certifique-se de que você está no ambiente **CustomerService
    Trial**.

3.  Clique em **Get started**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  Clique em **Skip** na página **Tell us about yourself**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  Role para baixo na próxima página e clique na opção **Start with a
    template** para começar a criar o site com um modelo.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  Selecione um modelo e clique em **Choose this template**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  Na caixa de texto **Give your site a name**, insira o nome como
    +++**Contoso Store assistant**+++, aceite os outros padrões e clique
    em **Done**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  Depois que o site for criado, clique em **Edit**.

> ![](./media/image60.png)

9.  Clique em **Edit site header** no título **Company name**.

![](./media/image61.png)

10. No painel **Edit site header**, informe o **Site title** como
    +++**Contoso Store assistant**+++ e feche a caixa de diálogo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. Clique em **Edit code** no canto superior direito da página.

![](./media/image63.png)

12. Clique em **Open Visual Studio Code**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

13. Clique em **Allow**. **Efetue login** usando suas credenciais de
    locatário, se necessário.

![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

14. A página inicial do site é aberta no Visual Studio Code.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

15. Vá até o final do arquivo. Adicione o **script** copiado durante a
    criação do fluxo de trabalho, após a última linha deste arquivo.

![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

16. Salve o arquivo, feche a aba Visual Studio Code e retorne às páginas
    do Power. Clique em **Sync**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

17. Quando a sincronização estiver concluída, selecione
    **Preview** -\> **Desktop.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

18. Sua página da web será aberta em uma nova aba. Encontre o **Store
    Locator Assistant** integrado à página, no canto inferior direito.
    **Clique** nele.

![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

19. Digite +++Talk to agent+++.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

20. Na página de administração do Atendimento ao Cliente, clique em
    **Customer Service admin center** e selecione o aplicativo
    **Customer Service workspace**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

21. Na página **Customer Service workspace**, você receberá um **chat
    request**. Clique em **Accept**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

22. Após a aceitação, a tela do chat será aberta com a mensagem que
    havíamos informado no tópico Escalate. Também é possível adicionar
    ao agente humano qualquer outra informação fornecida pelo usuário.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

23. Simule o chat entre o agente humano e o cliente, se desejar ver como
    funciona, e então finalize.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image77.png)

## Resumo

Neste laboratório, aprendemos a:

- Criar um agente no Copilot Studio e configurar o tópico Escalate.

- Publicar o agente no espaço de trabalho do Dynamics 365 e integrar em
  uma página da Web.
