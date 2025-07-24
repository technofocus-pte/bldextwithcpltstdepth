# Laboratório 07 – Crie um assistente de compras personalizado

## Objetivo

O objetivo deste laboratório é criar um agente de compras personalizado
para a Contoso Electronics. Isso usará as tabelas do Dataverse como a
fonte de conhecimento para o agente. Ele sugerirá categorias de produtos
ao cliente com base em suas últimas compras e o ajudará durante toda a
experiência de compra.

## Exercício 1 – Criar tabelas do Dataverse

Neste exercício, você criará tabelas no Dataverse para armazenar os
detalhes do **Cliente, Produto e Pedido.**

1.  Faça login em +++https://make.powerapps.com+++ usando suas
    credenciais de locatário de administrador e selecione Dev One como
    seu ambiente. Selecione **Tables** do painel de navegação esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  Selecione o menu suspenso ao lado de **+ New table** e selecione
    **Create new tables**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  Selecione **Import an Excel file or .CSV** para criar uma nova
    tabela.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Em **Export an Excel or .CSV file**, selecione a opção **Select from
    device**.

![A screenshot of a file AI-generated content may be
incorrect.](./media/image4.png)

5.  Em **C:\Labfiles**, selecione o Excel – **Customers.xlsx**.
    Selecione **Import** para importar os dados do rastreador e criar a
    tabela.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  A tabela é criada com os dados do rastreador.

7.  Aqui, o nome dessa tabela é **Customer Record**. O nome pode ser um
    pouco diferente no seu caso, pois é gerado automaticamente. Anote-o
    e use o nome da tabela apropriado durante a execução do laboratório.

8.  Clique na tabela e selecione **View data** para ver os dados
    adicionados à tabela.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  Selecione **Save and exit**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

10. Clique em **Save and exit** na caixa de diálogo de confirmação.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. Repita as etapas de 2 a 10 duas vezes, para criar tabelas uma vez
    usando o rastreador **Product Catalog.xlsx** e da próxima vez usando
    **Orders.xls**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

12. Agora, teremos 3 tabelas,

    - Customer Record

    - Product Record

    - Orders

## Exercício 2 – Criar um agente de compras

Neste exercício, você criará um agente de compras que ajudará os
clientes a fazer compras na Contoso Electronics.

### Tarefa 1 – Criar o agente

Crie o agente no Copilot Studio usando o Copilot. Converse com o
Copiloto e dê instruções sobre como o agente deve ser projetado e como
ele deve se comportar para que o Copiloto crie o agente para você.

1.  Faça login no Copilot Studio em
    +++https://copilotstudio.microsoft.com/+++ e selecione o o
    environment **Dev One**.

![](./media/image12.png)

2.  Selecione **Agents** e, em seguida, clique em **+ New agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  Digite o prompt abaixo no chat e envie.

+++**Create an agent that will assist the customers in shopping with
Contoso Electronics. Name it as "Shopping agent"**.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  Insira +++**Help the users in finding products and their prices,
    give personalized suggestions and track order delivery.**+++ e
    pressione **Enter**.

![](./media/image15.png)

5.  Insira instruções adicionais conforme abaixo.

+++**Maintain a polite tone**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  Clique em **Create** para criar o **Shopping agent**.

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image17.png)

7.  O agente é configurado. Isso pode levar alguns minutos. Quando o
    agente estiver pronto, ele será exibido no Copilot Studio como na
    captura de tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

### Tarefa 2 – Adicionar conhecimento

Adicionar conhecimento ao agente o torna fundamentado nesses recursos de
conhecimento, permitindo que ele responda às perguntas do usuário com
mais eficiência. Nesta tarefa, você adicionará a tabela do Dataverse
criada no exercício anterior como uma fonte de conhecimento a esse
agente.

1.  Insira +++**What is the status of the order o1001?**+++ no painel
    **Test** **your agent**.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image19.png)

2.  A resposta será semelhante à abaixo, pois o agente não tem nenhuma
    informação sobre isso.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image20.png)

3.  Agora, adicionaremos a fonte de conhecimento ao agente. Da página
    **Home** do agente, selecione **Add Knowledge** na seção
    **Knowledge**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

4.  Selecione **Dataverse** na lista de opções disponíveis.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

5.  Procure por +++**order**+++, selecione a tabela **Order Record** e
    clique em **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  Selecione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  Aguarde alguns minutos após a adição da fonte de conhecimento antes
    de testar o agente novamente.

8.  Once the **Order Record** se torna **Ready** na seção **Knowledge**,
    faça a mesma pergunta no painel **Test**.

Agora você pode ver que o agente recupera as informações do banco de
dados e as fornece ao usuário.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

### Tarefa 3 – Criar Entidades

1.  Selecione **Settings** na tela inicial do agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

2.  Selecione **Entities** no painel esquerdo. Selecione **Add an entity
    -\> + New entity**

![](./media/image27.png)

3.  Selecione **Closed list**.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image28.png)

4.  Insira os detalhes abaixo.

**Name** - +++**Laptop**+++

**Description** - +++**Contains products under Laptop category**+++

Em **List items**, insira +++**Apple MacBook Air M3**+++ and click on
**Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

5.  Da mesma forma, adicione os itens abaixo e selecione **Save**.

+++Dell XPS 13 Plus+++

+++HP Spectre x360 14+++

+++Lenovo ThinkPad X1 Carbon Gen 12+++

+++Asus ROG Zephyrus G14+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

6.  Agora, repita as etapas 2 a 5 com os dados abaixo.

**Name** - +++Desktop+++

**Description** - +++Contains products under Desktop category+++

Em **List items**, insira +++Apple iMac+++ e clique em **Add**.

7.  Outros itens a serem adicionados à lista,

+++Microsoft Surface Studio 2+++

+++HP Envy Desktop+++

+++Dell Inspiron Desktop+++

+++Lenovo IdeaCentre AIO 5i+++

8.  Novamente, repita as etapas 2 a 5 com os dados abaixo.

**Name** - +++Tablet+++

**Description** - +++Contains products under Tablet category+++

Em **List items**, insira +++Apple iPad Pro+++ e clique em **Add**.

9.  Outros itens a serem adicionados à lista,

+++Samsung Galaxy Tab S9 Ultra+++

+++Microsoft Surface Pro 10+++

+++Lenovo Tab P12 Pro+++

+++Apple iPad Air+++

## Exercício 3 – Criar tópicos e fluxos de agentes e projetar o agente

Projetar tópicos é uma parte muito importante na criação de um agente,
pois lida com a lógica por trás de como as perguntas do usuário são
respondidas e como será o fluxo dos detalhes.

### Tarefa 1 – Editar o tópico Conversation Start 

O tópico **Conversation Start** é o primeiro tópico a ser chamado ao
testar o agente. É um tópico do sistema disponível por padrão em
qualquer agente que você criar no Copilot Studio. Agora, você editará
este tópico para continuar a conversa a partir da mensagem de saudação
do agente.

1.  Da página **Overview** do agente, selecione a guia **Topics** na
    barra de menu superior. Selecione **System** para visualizar a lista
    de tópicos do sistema. Selecione o tópico **Conversation Start** na
    lista.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

1.  Após o nódulo **Message** existente, adicione um **Question node**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

2.  Insira a mensagem abaixo,

+++Welcome to Contoso Electronics. Please enter your **Phone number** to
proceed.+++ na área de mensagem e selecione **User’s entire response**
em **Identity**. Clique em **Var1** no campo **Save user response as**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

3.  Renomeie **Var 1** como +++**MobileNumber**+++ e selecione
    **Global** para usá-lo em todos os tópicos e, em seguida, selecione
    **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

### Tarefa 2 – Criar um tópico para lidar com os detalhes do cliente

1.  Da página **Overview** do agente, selecione a guia **Topics** na
    barra de menu superior. Selecione o menu suspenso ao lado de **Add a
    topic -\> From blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  Nomeie o agente como +++**Customer Details**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  Selecione **Change trigger** e selecione **It’s redirected to** como
    o gatilho.

![Screens screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

4.  Selecione **Save** para salvar o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

### Tarefa 3 – Criar um fluxo de agente para obter os detalhes do cliente

Nesta tarefa, você criará um fluxo de Agente, para o qual passará o
número de telefone informado pelo cliente como entrada e projetará o
fluxo para verificar se o usuário existe ou não e recuperará as
informações e retornará os detalhes ao agente.

1.  Abaixo do nódulo **Trigger**, selecione **Add a tool** -\> **New
    Agent flow**.

![](./media/image39.png)

2.  O designer de fluxo do agente é aberto. Selecione **Save draft**
    para salvar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  Selecione **Overview** no menu superior, clique em **Edit** e insira
    o nome do fluxo como +++**GetCustomer**+++. Em seguida, selecione
    **Save**. ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image41.png)

4.  Navegue até a guia **Designer** novamente para projetar o fluxo.
    Selecione o nódulo **When an agent calls the flow** e, em seguida,
    selecione **+ Add an input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  Selecione **Text**.

![](./media/image43.png)

6.  Insira a entrada como +++**Phone number**+++ e, em seguida, feche a
    guia **Parameters**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  Clique em **Add an action** entre os dois nódulos no fluxo. Procure
    por +++**List rows**+++ e selecione a ação **List rows** em
    **Microsoft Dataverse**.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

8.  Insira o nome da conexão como +++**Dataverse**+++ e clique em **Sign
    in**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  **Sign in** usando suas credenciais de locatário de administrador e
    clique em **Allow access** se solicitado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. Navegue até o PowerApps em +++https://make.powerapps.com/+++ e abra
    a tabela **Customer Record**. Clique no menu suspenso ao lado do
    campo **Mobile number** e selecione **Edit column**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. Role para baixo e em **Advanced options**, há um campo chamado
    **Logical name**. Anote seu valor em um bloco de notas.

**Importante:** Cada arquivo terá um nome lógico associado a ele no
Dataverse. E ao usá-lo no fluxo do Agente, você terá que especificar
apenas os nomes lógicos para todos os campos.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. Nesse caso, para Número de telefone, é **cr6dd_mobilecontact**.
    Anote isso.

13. Navegue de volta para o Copilot Studio, na guia **Agent flow**. Abra
    o fluxo **Getcustomer** e selecione a ação **List rows**.

14. Em **Filter rows**, insira **\<Logical name of Mobile number\> eq '
    '**. Substitua **\<Logical name\>** pelo valor obtido na etapa
    anterior. Mantenha o cursor dentro das aspas e adicione o **Phone
    number – dynamic variable**.

Neste caso, será **cr6dd_mobilecontact eq 'Phone number'**

![](./media/image50.png)

![](./media/image51.png)

15. Abaixo do nódulo **List rows**, adicione um nódulo **Condition**.

![](./media/image52.png)

16. Insira **/** e selecione **Insert expression**.

![](./media/image53.png)

17. Insira +++**length(outputs('List_rows')?\['body'\]?\['value'\])**+++
    na função e selecione **Add**. Isso verificará se o List rows
    fornece um valor ou não.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

18. Clique em **Add an action** sob o **True** da condição adicionada e
    adicione um novo nódulo **Condition**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

19. Insira
    +++**not(empty(first(outputs('List_rows')?\['body/value'\])?\[
    cr6dd_lastpurchasedproduct '\]))**+++ na área de função da condição.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

> **Importante** – Certifique-se de substituir o
> **cr6dd_lastpurchasedproduct** pelo **logical name** do campo **Recent
> Products Purchased** da tabela **Customer Record**
>
> ![](./media/image58.png)

20. Defina a condição como **is equal to true**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

21. Adicione uma nova ação abaixo do caminho **True** da **Condition1**
    e selecione o nódulo **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

22. Selecione o **Respond to the agent node** e renomeie-o como +++**If
    the customer has made a previous purchase**+++ e selecione **+ Add
    an output**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

23. Selecione **Text**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

24. Insira +++**Customer ID**+++ como o nome e clique em **Insert
    expression**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

25. Insira
    +++**first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]**
    +++ **cr6dd_customeridentifier** é o nome lógico da ID do cliente da
    tabela Customer Record. Substitua-o pelo seu valor.

26. Selecione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

27. Da mesma forma, adicione as variáveis e expressões de saída abaixo a
    cada uma delas. Para cada variável, certifique-se de substituir o
    nome lógico pelo seu.

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_lastpurchasedproduct'\]+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

28. O nódulo **Respond to the agent** terá 3 variáveis de saída como na
    captura de tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

29. Adicione um nódulo **Respond to the agent** sob o caminho **False**
    do nódulo **Condition1**. Renomeie-o para +++If the customer has not
    made a previous purchase+++. Clique em **+ Add an output**.

![](./media/image68.png)

30. Insira as variáveis de saída abaixo, substituindo os nomes lógicos
    das colunas pelos nomes lógicos das colunas correspondentes.

- +++Customer ID+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
  +++

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ - +++’1’+++

31. O nódulo **Respond to the agent** sob o caminho **False** será
    parecido com o da captura de tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

32. Agora, adicione um nódulo **Respond to the agent** sob o caminho
    **False** do nódulo **Condition**, renomeie-o para +++If the
    customer does not exist+++ e adicione saídas a ele como abaixo.

- +++Customer ID+++ - +++’1’+++

- +++Customer Name+++ - +++’1’+++

- +++Product Category+++ - +++’1’+++

![](./media/image70.png)

33. O fluxo **GetCustomer** será parecido com o da captura de tela
    abaixo.

![](./media/image71.png)

34. Clique com o botão direito do mouse no **Respond to the agent** que
    está lá como um comum no final do fluxo e selecione **Delete** para
    excluí-lo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

35. Selecione **Save Draft** para salvar o laboratório. Uma vez salvo,
    clique em **Publish** para publicar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

### Tarefa 4 – Criar fluxo de agente para adicionar cliente

Nesta tarefa, você criará um fluxo de agente para adicionar um novo
cliente ao Dataverse quando o cliente for um novo cliente.

1.  Na guia **Agent flows**, selecione **+ New agent flow.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  Selecione o nódulo **Add a trigger** e substitua-o pelo nódulo
    **When an agent calls the flow**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

3.  Selecione **+ Add an input** e adicione uma entrada **Text**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

4.  Insira +++Name+++ como o nome da entrada.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

5.  Da mesma forma, adicione os seguintes valores de entrada.

+++Phone Number+++

+++Email ID+++

+++Address+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image79.png)

6.  Adicione uma ação abaixo do nódulo e selecione **Add a new row**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

7.  Selecione o Table Name como **Customer Record** e, em seguida,
    selecione **Show all** em **Advanced parameters**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

8.  Clique no campo **Address**, selecione **Dynamic value** e, em
    seguida, selecione ícone **Address**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image83.png)

9.  Da mesma forma, adicione os valores dinâmicos para

- Customer Name – Nome

- Email ID – ID de e-mail

- Mobile Number - Número de telefone

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

10. Abra a expressão de inserção para **Customer ID**, insira
    +++guid()+++ e selecione **Add**. Isso é para adicionar um valor
    exclusivo como o ID do cliente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

11. Adicione uma nova ação e selecione **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

12. Adicione um valor de saída chamado +++Customer ID+++ e insira uma
    expressão e digite
    +++string(outputs('Add_a_new_row')?\['body/cr6dd_customeridentifier'\])+++
    como o valor.

Substitua **cr6dd_customeridentifier** pelo nome lógico da coluna
**Customer ID**.

Selecione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

13. Selecione **Save draft** para salvar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

14. Depois que o fluxo for salvo, selecione **Publish** Para publicar o
    fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

15. Selecione a guia **Overview**. Clique em **Edit.** Insira o nome do
    fluxo como +++Add Customer+++ e, em seguida, selecione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

### Tarefa 5 – Adicionar o fluxo e projetar o tópico detalhes do cliente

Nesta tarefa, você criará o tópico Detalhes do Cliente que obterá o
número de telefone do cliente, verificará se o detalhe já está presente
no Dataverse e o adicionará se ainda não estiver presente.

1.  Navegue de volta ao tópico **Customer Details**.

2.  Adicionar um nódulo sob o nódulo **Trigger**, selecione **Add a tool
    -\> GetCustomer**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

3.  Em **Inputs**, selecione a variável **MobileNumber**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

4.  Selecione as variáveis **output** e marque o **Customer ID** e
    **ProductCategory** como **Global** como na captura de tela abaixo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

5.  Abaixo do nódulo **Action**, adicione um nódulo **condition**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

6.  Selecione **CustomerID** em **Select a variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

7.  Selecione a condição como **is not equal to** e digite +++ '1'+++ no
    campo **Value**. Isso verifica se os detalhes do cliente já existem
    no banco de dados.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

8.  No nó de condição, adicione um nódulo **Set a variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

9.  Clique em **Select a variable** e selecione **Create a new
    variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

10. Nomeie a variável como +++IsNewCustomer+++ e marque-a como
    **Global**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

11. Defina o valor como +++‘No’+++. Isso significa que o cliente é um
    cliente antigo cujos dados já estão presentes no Dataverse.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

12. Você adicionará um novo nódulo ao lado do nódulo variável e enviará
    uma mensagem de boas-vindas ao cliente.

13. Selecione **Add a node** e selecione Nó **Send a message**. Na área
    de mensagem, digite +++Welcome+++ e, em seguida, clique no ícone {x}
    para selecionar a variável. Selecione a variável **Customer Name**.

![](./media/image101.png)

Agora, invocamos o fluxo do Agente **GetCustomer**, verificado se o
registro do cliente já existe e, em caso afirmativo, adicionou uma
mensagem de boas-vindas ao cliente.

Agora, vamos projetar a parte do tópico se o registro do cliente ainda
não existir.

13. Sob o nódulo **All other conditions**, adicione um nódulo **Set a
    variable** e defina o valor para a variável **isNewCustomer** como
    +++’Yes’+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

14. Ao lado do nódulo variável, adicione um nódulo **Message** e digite
    +++We do not have your details in our system. Please fill in your
    details below to help us serve you better.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

15. Ao lado do nódulo **Message**, adicionar um nódulo **Ask with
    adaptive card**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

16. Clique nos 3 pontos no canto superior direito da tela e selecione
    **Properties**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

17. Selecione **Edit adaptive card**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

18. Digite os dados abaixo **JSON** na área **Card payload editor**.
    Selecione **Save**.

> {
>
> "type": "AdaptiveCard",
>
> "body": \[
>
> {
>
> "type": "TextBlock",
>
> "size": "Medium",
>
> "weight": "Bolder",
>
> "text": "Please enter your details"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Name",
>
> "label": "Name"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Mobile Number",
>
> "label": "Mobile Number"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Email ID",
>
> "label": "Email ID"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Address",
>
> "label": "Address"
>
> }
>
> \],
>
> "actions": \[
>
> {
>
> "type": "Action.Submit",
>
> "title": "Submit"
>
> }
>
> \],
>
> "version": "1.5",
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json"
>
> }
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image107.png)

19. Selecione **Close** para fechar o editor.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

20. Expanda a seção **Outputs** do nódulo do cartão adaptável criado,
    selecione o valor **Mobile Number** e selecione a variável
    **Global.MobileNumber** para salvar o valor do número de telefone
    inserido pelo usuário nele.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

21. Deixe os outros valores como os padrões.

22. O cartão adaptável está pronto com o formulário para obter os
    detalhes do cliente.

23. Ao lado do nódulo do cartão adaptável, invoque o fluxo **Add
    Customer.**

![](./media/image110.png)

24. Clique nos **três pontos** em **Enter or select a value** e
    selecione a variável **CustomerName**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

25. Da mesma forma, adicione as variáveis de entrada para os outros
    campos a serem passados para o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

26. Selecione **Global.CustomerID** como a variável de saída na qual a
    saída do fluxo será salva.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

27. Após o nódulo de ação, adicione um nódulo **Message** e insira o
    valor, +++Thank You! Customer detail has been added to the database.
    Please select a product type to shop.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

28. Clique em **Save** para salvar o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

29. Abra o tópico Início da Conversa e chame o tópico Detalhes do
    Cliente a partir daí.

30. Adicione um nódulo após o nódulo **Question** no tópico. Selecione
    **Topic management -\> Go to another topic**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

31. Selecione o tópico **Customer Details**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

32. Clique em **Save** para salvar o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### Tarefa 6 – Criar um fluxo de agente para obter os detalhes do produto

Nesta tarefa, você criará um fluxo de agente que buscará os detalhes do
produto no Dataverse com base no produto selecionado.

1.  Selecione a guia **Flows** no Copilot Studio e selecione **+ New
    agent flow**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  Selecione o nódulo **Add a trigger** e selecione ação **When an
    agent calls the flow**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  Adicione uma entrada de texto e nomeie-a como +++Product Name+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

4.  Selecione **Save draft** para salvar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

5.  Selecione a guia **Overview** e clique em **Edit**. Digite o nome
    como +++GetProductDetails+++ e selecione **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

6.  Navegue de volta para a guia **Designer** e selecione **Add an
    action** abaixo do nódulo **When an agent calls the flow**. Procurar
    +++list rows+++ e selecione a ação **List rows** em **Microsoft
    Dataverse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

7.  Insira os valores abaixo

- **Table name –** Select **Product Record**

- Filter rows – +++cr6dd_producttitle eq '**\<Product Name\>**'+++
  Replacing \<Product Name\> com o valor dinâmico ProductName.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image125.png)

8.  Adicione um nódulo **Respond to the agent** sob o nódulo **List
    rows**. Selecione **+ Add an output** e adicione uma variável de
    saída de texto. Insira os valores abaixo e clique em **Add** em
    **insert expression.**

    - Enter a name – Enter +++Product Name+++

    - Expression -
      +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_producttitle'\]+++
      (Substitua **cr6dd_producttitle** com o nome lógico da coluna
      **Product Name** na sua tabela.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image126.png)

9.  Da mesma forma, adicione outro nódulo de saída com os detalhes
    abaixo

- Enter a name – Enter +++Price+++

- Expression -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_productprice'\]+++
  Substitua **cr6dd_productprice** com o nome lógico da coluna **Price**
  na sua tabela

> O nódulo agora deve ficar assim.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image127.png)

10. Selecione **Save draft** para salvar o tópico e, em seguida,
    **Publish** para publicar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

### Tarefa 7 – Criar um tópico para recuperar a categoria Produto do cliente

1.  Na guia Copilot Studio Topics, selecione **+ Add a topic -\> From
    blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

2.  Renomeie o tópico para +++Place Order+++. **Change the trigger** do
    nódulo de gatilho para **It’s redirected to**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

3.  Clique em **Save** para salvar o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image131.png)

4.  Na guia Copilot Studio Topics, selecione **+ Add a topic -\> From
    blank**.

![](./media/image129.png)

5.  Renomeie o tópico como +++Get Product Categories+++. Selecione a
    opção **Change trigger** no nódulo **Trigger** e selecione a opção
    **It’s redirect to**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

6.  Abaixo do nódulo **Trigger**, adicione um nódulo **Condition**.

Selecione a variável Global **IsNewCustomer** e adicione a condição,
**IsNewCustomer** **is equal to** +++**'Yes'**+++.

Selecione **+ New condition.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

7.  Selecione **Or**.

Sob a condição **Or**, selecione a variável Global **ProductCategory**
adicione a condição, é igual a +++'1'+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

![](./media/image136.png)

8.  Sob o nódulo Condition, adicione um nódulo de pergunta e insira
    +++Select a category+++ e selecione **+ New option**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

9.  Digite a opção +++Laptop+++ e selecione + New option again.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

10. Da mesma forma, adicione duas outras opções +++**Desktop**+++ e
    +++**Tablet**+++. Selecione a variável em **Save user response as**,
    e nomeie a variável como +++**ProdCatchoice**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

11. No nódulo da pergunta, adicione um nódulo **Set a variable value**
    para converter a opção recebida do nó da pergunta em String.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

12. Selecione a variável Global **ProductCategory** em Set variable. No
    campo **To value**, Clique nos 3 pontos, selecione a guia
    **Formula**. Insira a expressão +++Text(Topic.ProdCatchoice)+++ e
    selecione **Insert**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

13. Abaixo do nódulo Set variable value, adicione um novo nódulo,
    **Topic management** -\> **Go to another topic** -\> **Place
    Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

14. Agora, um caminho está completo. Ele obterá a categoria do usuário e
    invocará o tópico Place Order.

15. Volte ao início deste tópico. Em todas as outras condições, adicione
    um nódulo **Question**. Adicionar a mensagem +++Based on your recent
    purchase we suggest you products in \<Product Category\> category.
    Would you like to continue?+++

Na mensagem, substitua **\<Product Category\>** pela variável
**Global.ProductCategory**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image143.png)

16. Adicione duas opções, +++Yes+++ e +++No+++. Clique na variável em
    **Save user response as** e renomeie-a para
    +++Userschoiceofcategory+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

17. Sob o nódulo **question**, adicione um nódulo **condition**.

Defina a primeira condição como **Userschoiceofcategory is equal to
Yes**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

36. Nesse nódulo, adicione um **Topic management node** e invoque o
    tópico **Place Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

18. No nódulo de condição, selecione os três pontos no canto superior e
    selecione **Insert new condition**.

![](./media/image147.png)

19. Adicione uma condição, **Userschoiceofcategory is equal to No**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

20. Sob o nódulo **Condition**, adicione um nódulo **Question** e digite
    +++Select a category+++ e selecione **+ New option**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

21. Digite a opção +++Laptop+++ e selecione **+ New option** outra vez.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

22. Da mesma forma, adicione duas outras opções +++**Desktop**+++ e
    +++**Tablet**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

23. No nódulo da pergunta, adicione um nódulo **Set a variable value**
    para converter a opção recebida do nó da pergunta em String.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

24. Selecione a variável Global **ProductCategory** em Set variable. No
    campo **To value**, clique nos três pontos, selecione a guia
    **Formula**. Insira a expressão +++Text(Topic.Var1)+++ e selecione
    **Insert**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

25. Abaixo do nódulo Set variable value, adicione um novo nódulo,
    **Topic management** -\> **Go to another topic** -\> **Place
    Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

26. Selecione **Save** para salvar o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image151.png)

27. Abra o tópico **Customer Details** e vá para o último nódulo.

28. **Add a new node** para invocar o tópico **Get Product Categories**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image152.png)

29. Selecione **Save** para salvar o tópico.

![](./media/image153.png)

### Tarefa 8 – Criar fluxo de agente para fazer o pedido

Nesta tarefa, você criará um fluxo de Agente para fazer o pedido com
base no produto escolhido pelo cliente.

1.  Na guia **Agent flows**, selecione **+ New agent flow.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image154.png)

2.  Clique no nódulo **Add a trigger** e selecione o nódulo **When an
    agent calls the flow**.

![](./media/image155.png)

3.  Adicione duas **variáveis** de texto+++Product Name+++ e +++Customer
    ID+++ como **Input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image156.png)

4.  Clique em **Save Draft** para salvar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image157.png)

5.  Selecione **Overview** no menu superior, clique em **Edit** e insira
    o nome do fluxo como +++PlaceOrder+++. Em seguida, selecione
    **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image158.png)

6.  Navegue de volta para a guia **Designer**. Selecione **Add a new
    action** e selecione **Add a new row** em **Dataverse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image159.png)

7.  Selecione o Nome da tabela como **Order Record** and then click on
    **Show all**, em seguida, clique em Advanced parameters.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image160.png)

8.  Enter the below values.

Customer Identifier - **Customer ID** (Dynamic value)

Order identifier – Enter guid() in Insert expression

Order Status - +++**Order Placed**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image161.png)

9.  Adicione um nódulo, **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image162.png)

10. Adicione uma variável de texto de saída e nomeie-a como +++Order
    ID+++.

Insira seu valor como +++
string(outputs('Add_a_new_row')?\['body/cr6dd_orderidentifier'\])+++
(Substitua **cr6dd_orderidentifier** com o valor do nome lógico da
coluna ID do pedido da tabela Order Record.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image163.png)

11. Clique em **Save draft** para salvar o fluxo e clique em **Publish**
    para publicar o fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image164.png)

### Tarefa 9 – Projetar o tópico Fazer pedido 

Nesta tarefa, você criará o tópico para fazer o pedido e atualizar a
tabela do Dataverse.

1.  Abra o tópico **Place Order** na guia **Topic** do Agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image165.png)

2.  Adicione um nódulo de mensagem com a mensagem +++Options based on
    the category will be listed below.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image166.png)

3.  Adicione um nó de condição. Insira a condição como
    ProductCategory(Global variable) is equal to +++Laptop+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image167.png)

4.  No nódulo, adicione um nódulo de pergunta e insira a mensagem
    +++Select a Laptop product+++. Selecione **Laptop** em **Identity**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image168.png)

5.  Clique nas opções **Select** para o usuário e selecione todas as
    cinco opções disponíveis.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image169.png)

6.  Insira o nome da variável como +++ProdNameLapChoice+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image170.png)

7.  Agora, siga o mesmo procedimento e adicione nós de condição para
    ProductCategory é igual a +++Desktop+++ e +++Tablet+++.

8.  Salve os valores em nomes de variáveis.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image171.png)

9.  Selecione um nódulo **Set variable value** sob o nódulo de pergunta
    **Select a Laptop product**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image172.png)

10. Renomeie a variável criada para +++ProdNameSelected+++ e a defina
    como **Global**.![A screenshot of a computer AI-generated content
    may be incorrect.](./media/image173.png)

11. Defina o valor no campo **Formula** como
    +++Text(Topic.ProdNameLapChoice)+++ (Substitua o nome da variável,
    se você tiver usado um diferente)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image174.png)

12. Da mesma forma, adicione um nódulo **Set variable value** em
    **Desktop** e **Tablet**. Selecione o valor **Set variable** como
    **ProdNameSelected** e insira a expressão para o campo **To**
    **value** com o nome da variável de acordo com o que você usou.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image175.png)

13. Adicione um nódulo Action em todos esses nódulos em comum e invoque
    o fluxo GetProductDetails.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image176.png)

1.  Selecione **ProdNameSelected** variável de entrada a ser passada
    para o fluxo. Deixe os outros valores como padrão.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image177.png)

14. Adicione um nódulo Message sob Action e digite a mensagem abaixo.
    Substitua \<roductName\> e \<Price\> pelos nomes de variáveis
    correspondentes

Product Details

- Product Name - \<ProductName\>

> ​

- Price - \<Price\>

​

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image178.png)

15. Abaixo do nódulo da mensagem, adicione um **Question node** com a
    mensagem, +++Would you like to place order for this item?+++.
    Adicione as opções **Yes** e **No** a ele e nomeie a variável como
    +++PlaceOrder+++.

![](./media/image179.png)

16. Sob o nódulo Question, adicionar um nó de condição e, em uma
    ramificação, adicionar uma condição **PlaceOrder isequal to Yes** e
    **all other conditions** serão **second branch**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image180.png)

17. Invoque o fluxo **PlaceOrder** como o próximo passo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image181.png)

18. Selecione **ProductName** e **CustomerID** como a entrada para o
    fluxo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image182.png)

19. Agora, adicione um nó de mensagem abaixo disso com a mensagem,
    +++Your order is placed. This is your Order ID for reference
    -\<OrderID\>+++ (Substituir **\<OrderID\>** com a variável
    **OrderID** (a variável de saída do fluxo).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image183.png)

20. Com isso, o ramo **PlaceOrder isequal to Yes** está **completo**.
    Agora, navegue até o ramo **All other conditions**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image184.png)

21. Abaixo disso, adicione um nódulo Question com a mensagem, +++Do you
    want to go to the main menu?+++ com opções **Yes** e **No**. Nomeie
    a variável como +++**GoToMainMenu**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image185.png)

22. Nesse nódulo, adicione um nódulo de condição e, em uma ramificação,
    adicione uma condição com **GoToMainMenu is equal to Yes**. O outro
    ramo desta condição será **All other conditions**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image186.png)

23. Nesse nó de condição, adicione um nódulo de pergunta com a mensagem
    +++**Select Product Category**+++ e adicione três opções,
    +++**Laptop**+++, +++**Desktop**+++ e +++**Tablet**+++.

Anote o nome da variável na qual o resultado é salvo. Vamos convertê-lo
em texto na próxima etapa.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image187.png)

24. Adicione um nódulo **Set variable value** e selecione a variável
    **ProductCategory** em **set variable** e insira o valor como
    +++**Text(Topic.Var1)**+++ sob a guia **Formula**.

Substitua **Var1** com o nome da sua variável, se for diferente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image188.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image189.png)

25. Sob o nódulo Set variable value, adicione um nódulo **Go to step**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image190.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image191.png)

26. Depois de adicionar o nódulo, você terá que selecionar o **step**,
    para o qual o **control should pass** neste momento. **Scroll up** e
    selecione o **Message node at the starting of this topic** uma vez
    que, você tem o **ProductCategory** do cliente agora e precisa
    executar desde o início.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image192.png)

1.  Adicione um nódulo de mensagem comum no final com a mensagem
    +++Thank you for shopping with us! Please visit again!+++ Em
    seguida, selecione **Save** para salvar o tópico.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image193.png)

## Exercício 4 – Adicionar um gatilho 

Neste exercício, você adicionará um gatilho para ser iniciado quando a
tabela Order for adicionada com uma nova linha ou uma linha existente
for modificada e enviará um email para o cliente automaticamente. Isso
define a capacidade autônoma do agente neste cenário.

1.  Selecione a guia Overview do agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image194.png)

2.  Role a página para baixo e selecione **Add trigger.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image195.png)

3.  Selecione a opção **When a row is added, modified or deleted** e, em
    seguida, selecione **Next**.

![](./media/image196.png)

4.  Uma vez que o **Microsoft Copilot Studio** e o **Dataverse** estejam
    conectados, clique em **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image196.png)

5.  Selecione as opções abaixo, deixe o restante como padrão e selecione
    **Create trigger**.

- Change Type – Added or Modified or Deleted

- Table name – Order Record

- Scope - Organization

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image197.png)

6.  Isso pode levar alguns minutos para ser concluído. Uma vez feito
    isso, selecione **Close** na caixa de diálogo Add trigger.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image198.png)

7.  Da seção Trigger na página **Overview** do agente, Clique nos **três
    pontos** ao lado do gatilho adicionado e selecione **Edit in Power
    Automate**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image199.png)

8.  Selecione o primeiro nó no fluxo e adicione os nomes das colunas,
    +++cr6dd_orderidentifier, cr6dd_customeridentifier+++ under **Select
    columns**. ( **Substitua-os pelos** nomes lógicos das colunas
    **Order ID** e **Customer ID** da tabela **Order Record**).

![](./media/image200.png)

9.  Adicione um novo nódulo e selecione a ação **List rows**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image201.png)

10. Na ação List rows, selecione **Table name** as **Customer Record**.

Em **Filter rows**, insira +++**cr6dd_customeridentifier eq ''**+++,
substituindo o nome da coluna pelo seu **Customer ID’s logical name**.
Mantenha o **cursor dentro** das aspas **simples**.

![A screenshot of a list AI-generated content may be
incorrect.](./media/image202.png)

11. Selecione Inserir expressão, insira
    +++String(triggerOutputs()?\['body/cr6dd_customeridentifier'\])+++,
    Substitua **cr6dd_customeridentifier** pelo nome lógico do seu
    CustomerID e selecione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image203.png)

12. Ao lado de **List rows**, adicione uma ação **Send an email (V2).**

![A screenshot of a mail box AI-generated content may be
incorrect.](./media/image204.png)

13. Clique em **Sign in** e faça login com suas credenciais.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image205.png)

14. No campo **To**, inserir expressão e digite
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_emailaddress'\]+++,
    Substitua **cr6dd_emailaddress** com o nome lógico do campo de ID de
    e-mail da tabela Customer Record e, em seguida, selecione **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image206.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image207.png)

15. Insira os detalhes abaixo,

Subject - +++Order Placement+++

Body –

Hi,

This is to update you that your order has been placed. Thank you for
shopping with us.

Thank You.

16. Salve o fluxo e publique-o.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image208.png)

17. De volta à página do agente do Copilot Studio, selecione **Publish**
    para publicar o agente.

![](./media/image209.png)

18. Selecione **Publish** na caixa de diálogo de confirmação.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image210.png)

## Exercise 5 – Testar o agente

Neste exercício, você testará como o agente funciona.

1.  Na página do agente, selecione **Test** para abrir o painel Teste.

2.  Insira +++3148987666+++. Este é o número de telefone de um cliente
    existente.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image211.png)

3.  Selecione **Yes** das opções fornecidas.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image212.png)

4.  Selecione um **product** das opções fornecidas.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image213.png)

5.  Selecione **Yes** das opções fornecidas.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image214.png)

6.  O pedido é feito e o ID de referência é fornecido ao cliente.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image215.png)

7\. Você também pode fazer outras perguntas, como rastrear a entrega do
pedido para o ID que você recebeu. Embora não tenhamos configurado os
tópicos para isso, ele lhe dará uma resposta com base na fonte de
conhecimento.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image216.png)

Teste os outros cenários selecionando opções diferentes. Adicione um
novo cliente e verifique se você recebeu um e-mail em seu ID de e-mail
que foi adicionado à tabela Customer Record.

## Resumo:

Neste laboratório, você aprendeu a projetar um agente de compras
autônomo. Os tópicos abordados incluem,

- Variáveis

- Entidades

- Tópicos

- Fluxos de agentes

- Gatilho

- Fontes de conhecimento
