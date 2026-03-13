# Laboratório 10 - Criar um Agente assistente de Conhecimento para RH no Copilot Studio que aproveita o Azure AI Search

## Objetivo:

Uma grande empresa quer reduzir o tempo que os funcionários gastam
procurando informações relacionadas a RH (políticas, benefícios,
diretrizes de licença, etc.) espalhadas no SharePoint, PDFs, wikis
internos e documentos.

Para superar esse problema, neste laboratório, você criará um **Agente
assistente de conhecimento** no **Copilot Studio** que usa o **Azure AI
Search** para indexar e pesquisar semanticamente em documentos de RH
corporativos.

## Exercício 1: Criar um recurso do Azure AI Search

1.  Na página inicial do portal do Azure, selecione **Azure AI
    Foundry.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  Na **página AI Foundry**, selecione **AI Search** no painel esquerdo
    e depois selecione **+ Create**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image2.png)

3.  Insira os detalhes abaixo e selecione **Review + create**.

- Subscription – Selecione sua **assinatura atribuída**

- Resource group – Selecione o **grupo de recursos atribuído**
  (**ResourceGroup1**)

- Storage account name – +++**searchleaves**+++

- Location – Selecione a **região atribuída**

![A screenshot of a search service AI-generated content may be
incorrect.](./media/image3.png)

4.  Após a validação, selecione **Create**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image4.png)

5.  A implementação leva alguns minutos. Selecione **Go to resource**
    após a criação do serviço de pesquisa.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  Na página **Overview**, copie o valor da URL e salve-o em um bloco
    de notas para ser usado em um exercício futuro.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  Selecione **Key** em **Settings** no painel esquerdo. Copie a
    **Primary admin key** e salve-a em um bloco de notas para usá-la nos
    próximos exercícios.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  Selecione **Identity** em **Settings** no painel esquerdo.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image8.png)

9.  Alterne o Status para **On** em **System assigned** e clique em
    **Save**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image9.png)

10. Selecione **Yes** na caixa de diálogo **Enable system assigned
    managed identity**.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image10.png)

## Exercício 2: Criar uma conta de armazenamento

1.  Acesse o portal do Azure em +++https://portal.azure.com/+++ e use
    suas credenciais. Selecione **Storage accounts** na tela inicial.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  Selecione **+ Create** para criar uma nova conta de armazenamento.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

3.  Insira os detalhes abaixo, aceite os valores padrão nos outros
    campos e clique em **Review + create**.

- Subscription – Selecione sua **assinatura atribuída**

- Resource group – Selecione o **grupo de recursos atribuído**
  (**ResourceGroup1**)

- Region – Selecione a **região atribuída**

- Storage account name – +++**leavepolicystorage**+++

- Primary service – Selecione **Azure Blob Storage ou Azure Data Lake
  Storage Gen 2**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

4.  Após a validação, clique em **Create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  Após a criação do recurso ser bem-sucedida, clique em **Go to
    resource**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  Selecione **Containers** em **Data storage**. Selecione **+
    Container**, insira o nome +++ **document**+++ e clique em
    **Create** para criar o contêiner.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

7.  Selecione o contêiner **document** criado para carregar o documento
    de política de licença nele.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  Clique em **Upload** e depois selecione **Browse for files**.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image19.png)

9.  Selecione **LeavePolicy.docx** em **C:\Labfiles** e clique em
    **Upload**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

10. Navegue até a conta de armazenamento **leavepolicystorage**
    (Selecione **Storageaccounts** na **Home page** do portal do Azure e
    selecione **leavepolicystorage**) e selecione **Access Control
    (IAM)** no painel esquerdo. Selecione **Add -\> Add role
    assignment**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

11. Procure por +++**Storage Blob Data Reader**+++, selecione-o e clique
    em **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

12. Clique em **+ Select members**, pesquise e selecione seu **user
    id**, selecione o **user id** listado e clique em **Select**. Isso
    adiciona a função Storage Blob Data Reader ao seu ID de usuário.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

13. Selecione **Managed identity** e, em seguida, **+ Select members**.
    Selecione **Search service** em **Managed identity** e selecione o
    serviço de **searchleaves** que será listado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

14. Clique em **Select** para selecionar o serviço de pesquisa.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

15. De volta à tela **Add role assignment**, clique em **Review +
    assign**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

16. Selecione **Review + assign** novamente na próxima tela.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

17. Prossiga para a próxima etapa depois que as funções forem
    adicionadas.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

Neste exercício, criamos uma conta de armazenamento e adicionamos o
documento e as permissões de função necessárias.

## Exercício 3: Criar um Azure OpenAI Service e implementar um modelo

1.  Na página inicial do portal do Azure, pesquise por select +++Azure
    OpenAI++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

2.  Selecione **+ Create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

3.  Insira os detalhes abaixo e selecione **Next**.

- Subscription – Selecione sua **assinatura atribuída**

- Resource group – Selecione o **grupo de recursos atribuído**
  (ResourceGroup1)

- Region – Selecione a **região atribuída**

- Name – +++**openaiservice52374668**+++

- Pricing tier – Selecione **Standard**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  Selecione **Next** nas próximas 2 telas e selecione **Create** na
    tela **Review + submit**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  Clique em **Go to resource** quando o serviço for criado.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

6.  Selecione **Access Control (IAM)** no painel esquerdo, selecione
    **Add -\> Add role assignment**.

![](./media/image36.png)

7.  Pesquise por +++**Cognitive Services OpenAI User**+++, selecione a
    função e clique em **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

8.  Selecione **+ Select members**, procure seu **user id**, selecione-o
    e clique em **Select**.

![](./media/image38.png)

9.  De volta à tela **Add role assignment**, selecione **Managed
    identity**. Em seguida, selecione **+ Select members**. Na tela
    **Select managed identities**, selecione **Search service** em
    **Managed identity** e selecione o serviço **seachleaves**.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image39.png)

10. Uma vez selecionado, clique em **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

11. Selecione **Review + assign** nas próximas 2 telas.

![](./media/image41.png)

12. Aguarde a mensagem **success** sobre as adições de funções antes de
    prosseguir com as próximas tarefas.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

13. Na página **Overview** de recurso do Azure OpenAI Service, selecione
    **Ir para o portal do Azure AI Foundry** para abrir o Azure OpenAI
    Service e implementar um modelo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

14. Selecione **Deployments** no painel esquerdo.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

15. Selecione **+ Deploy model** -\> **From base models**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

16. Pesquise por +++ **text-embedding**+++, selecione
    **text-embedding-3-large** e então selecione **Confirm**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

17. Selecione **Deploy** em **Deploy text-embedding-3-large**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

18. O modelo é implementado e a tela é carregada com os detalhes da
    implementação.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

## Exercício 4: Criar um índice vetorial

1.  Acesse o recurso do serviço de pesquisa de AI da **searchleaves.**
    Selecione **Import and vectorize data**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  Selecione a opção **Azure Blob Storage**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  Selecione a opção **RAG** na tela **What scenarios are you
    targeting?.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  Insira os detalhes abaixo, aceite os outros valores como padrão e
    clique em **Next**.

- Subscription – Selecione sua **assinatura atribuída**

- Storage account - Selecione **leavepolicystorage**

- Blob-container – Selecione **document**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  Na tela **Vectorize your text**, a assinatura e os detalhes do
    recurso do Azure OpenAI são preenchidos previamente. Insira os
    detalhes abaixo e clique em **Next**.

- Model deployment – Selecione **text-embedding-3-large**

- Authentication type – Selecione **System assigned identity**

- Marque a caixa de seleção para confirmar o alerta de custo do Azure
  OpenAI.

1.  Selecione **Next** na tela **Vectorize and enrich your images,** já
    que não estamos lidando com imagens aqui, e selecione **Next**
    também na tela **Advanced settings.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  Selecione **Create** na tela **Review + create**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

3.  Clique em **Close** na caixa de diálogo de sucesso.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

## Exercício 5: Criar um Agente assistente de conhecimento

1.  Faça login em +++https://copilotstudio.microsoft.com+++ usando suas
    credenciais de login.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

2.  Selecione **Create** no painel esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

3.  Selecione **+ New agent** para criar um novo agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

4.  Digite +++You are a Knowledge assistant agent for HR who will answer
    questions related to leaves and leave policies to the employees.+++
    e selecione **Send**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

5.  O copilot sugere um nome ao agente. Clique em **Create** para criar
    o agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

6.  Depois que o agente for criado, no painel Test, insira +++How many
    days can I avail Maternity leaves?+++ e clique em **Send.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

7.  Fornece uma resposta generalizada como na captura de tela abaixo.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image64.png)

## Exercício 6: Adicione o Azure AI Search como fonte de conhecimento

1.  Na página **Overview** do agente, selecione **Add knowledge**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

2.  Selecione Azure AI Search na lista de fontes de conhecimento
    disponíveis.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

3.  Clique no **menu suspenso** ao lado de **Not connected** na próxima
    tela e selecione **Create new connection**.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image67.png)

4.  Insira a **Endpoint url** e os valores **Admin key** que salvamos em
    um bloco de notas em um exercício anterior e clique em **Create**
    para criar a conexão.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

5.  Após o estabelecimento da conexão, o índice disponível será listado
    e selecionado. Clique em **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

6.  O serviço AI Search é adicionado como fonte de conhecimento ao
    agente e agora está no estado **Ready.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

7.  Agora, vamos testar o agente com a mesma pergunta que tentamos
    antes.

8.  No painel **Test**, insira +++How many days can I avail Maternity
    leaves?+++ e clique em **Send.**

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

9.  Você pode ver que a resposta do agente agora vem do documento
    carregado no serviço **AI Search**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image72.png)

Resumo:

Neste laboratório, aprendemos a conectar o agente a um serviço Azure AI
Search como fonte de conhecimento. Também testamos o agente com base
nessa fonte.
