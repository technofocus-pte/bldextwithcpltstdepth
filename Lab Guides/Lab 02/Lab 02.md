# Laboratório 2 - Criar e aprimorar um assistente empresarial baseado em modelo

**Objetivo**

Os **modelos de agente** são projetados para ajudar você a começar
rapidamente com um **agente personalizado**. Você é responsável por
avaliar todas as implicações de segurança e legais do uso de um modelo
de agente e por personalizá-lo conforme as necessidades do seu negócio.

Um agente criado a partir do **modelo de agente Safe Travels** é um
agente Business-to-Employee (B2E) projetado para fornecer **assistência
em viagens** aos colaboradores de uma empresa. Esse agente ajuda a
garantir que os colaboradores estejam bem preparados e informados para
sua próxima viagem a trabalho. Esse agente utiliza processamento de
linguagem natural para oferecer uma interface conversacional, tornando
fácil e intuitivo para os colaboradores acessarem as informações de que
precisam. No entanto, o site padrão usado pelo agente atualmente cobre
apenas destinos de viagem nos Estados Unidos. Você pode substituir o
site padrão por sua própria fonte de conhecimento.

Neste laboratório, você irá criar um agente a partir do **modelo de
agente Safe Travels** e aprimorá-lo no Laboratório 05.

## Exercício 0 – Criar um Grupo de urança no Entra ID e Configurar Autores do Copilot Studio

Esta é uma tarefa de pré-requisito para ajudar a publicar e trabalhar de
forma integrada com os agentes no Copilot Studio ao longo deste curso.

1.  Navegue até o portal do Azure em
    +++<https://portal.azure.com/+++> faça login com as credenciais do
    seu locatário presentes na guia **Resources**.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  Selecione **Next** na janela Keep your account secure e siga os
    **prompts.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Baixe o aplicativo Authenticator no seu telefone, caso ainda não o
    tenha.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  Siga os prompts e conclua a configuração.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  Na tela de boas-vindas do Azure, selecione **Get Started**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  Pesquise e selecione +++Microsoft EntraID+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  No painel esquerdo, selecione **Manage** -\> **Groups**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  Selecione **New group** para criar um novo grupo de segurança.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  Insira os seguintes detalhes:

    - Group type – Selecione **Security**

    - Group name – Insira +++**copilotagentsecurity**+++

    - Microsoft Entra roles can be assigned to the group – Selecione
      **Yes** (se essa opção não estiver visível, ignore esta etapa)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. Selecione **No owners selected**, escolha o **MOD Administrator** na
    página **Add owners** e clique em **Select**.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. Da mesma forma, selecione **No members selected**, adicione o **MOD
    Administrator** e clique em **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. Selecione **No roles selected**. Se essa **opção não estiver**
    visível, ignore esta e a próxima etapa.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. Pesquise e selecione +++**Global admin**+++ e clique em **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. Selecione **Create** após adicionar todos os detalhes e selecione
    **Yes** na caixa de confirmação.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. Certifique-se de que uma mensagem de **sucesso** seja exibida.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. Selecione Contoso | Groups no canto superior esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. Em **Manage**, selecione **Properties** no painel esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. Ative Yes na opção **can manage access to all Azure subscriptions
    and management groups in this tenant** e clique em **Save**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. Em **Manage**, selecione **Roles and administrators** no painel
    esquerdo.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. Pesquise por +++privileged role admin+++ e clique no papel
    **Privileged Role Administrator** (**não marque a caixa de
    seleção**; clique no nome).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

21. Selecione **+ Add assignments**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

22. Selecione **No members selected**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

23. Selecione o **MOD Admin id** e clique em **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

24. Selecione **Assign**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

25. Certifique-se de que a atribuição da função foi bem-sucedida.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

26. Em uma nova aba, navegue até
    +++<https://admin.powerplatform.microsoft.com/+++>. Selecione
    **Manage** no painel esquerdo e depois **Tenant Settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

27. Selecione **Copilot Studio Authors** na lista disponível.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

28. Clique no ícone **Edit** para editar as configurações.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

29. Pesquise e selecione o grupo **+++copilotagentsecurity+++** criado
    anteriormente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

30. Selecione **Save** para salvar as configurações.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

## Exercício 1: Criar um agente Safe Travel usando o modelo

Neste exercício, você criará o agente no Copilot Studio usando o modelo
de agente Safe Travels.

1.  Em um navegador, faça login em
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/).
    A página Start free trial será aberta. Selecione seu país e clique
    em **Start free trial**.

![](./media/image39.png)

2.  Selecione o ambiente **Dev One**.

> ![](./media/image40.png)
>
> \[!Alerta\] **Importante** Se o Copilot Studio não exibir a opção para
> selecionar **Environment**  conforme a captura de tela, siga os passos
> abaixo:
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image41.png)
>
> Abra +++<https://admin.powerplatform.microsoft.com/+++>.
> Selecione **Manage** -\> **Environments -\> Dev One** e selecione o
> valor do **Environment ID.**![A screenshot of a computer AI-generated
> content may be incorrect.](./media/image42.png)
>
> Volte para a aba do Copilot Studio e abra
> +++<https://copilotstudio.microsoft.com/environments/>**\<
> EnvironmentID \>**+++ (substituindo **\< EnvironmentID \>** com o
> valor obtido acima)

3.  Selecione Skip na tela de boas-vindas.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

4.  Selecione **Agents** no painel esquerdo e selecione o modelo **Safe
    Travels** em **Start with an agent template**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

5.  5\. O modelo Safe Travels cria um novo agente projetado para
    fornecer assistência em viagens aos funcionários de uma empresa. 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

6.  Navegue pela página de configuração. Em **Knowledge**, você pode ver
    que o **US Travel Website** já está adicionado como uma fonte de
    conhecimento. Ele pode ser editado, se necessário. Neste
    laboratório, utilizaremos o mesmo site.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

7.  Selecione **Create** para criar o agente Safe Travels. Não faremos
    nenhuma alteração neste momento e utilizaremos o modelo conforme
    está. O agente pode ser aprimorado a qualquer momento, de acordo com
    os requisitos do usuário.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

8.  O **agente** é **criado** e aberto automaticamente, exibindo a
    página **Overview**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

9.  No painel Test, insira +++How to apply for passport?+++ e pressione
    **Send**.

O painel Test é aberto por padrão. Caso não esteja visível, clique no
ícone Test no canto superior direito.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

10. Você pode observar que o agente fornece informações sobre como
    solicitar um passaporte a partir de sua fonte de conhecimento.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image50.png)

## Exercício 2: Publicar o agente no Teams e no Microsoft 365 Copilot

Neste exercício, você irá **publicar** o agente criado no Copilot Studio
para os canais **Microsoft Teams** e **Microsoft 365 Copilot**

1.  Abra o **MS Teams** +++<https://teams.microsoft.com/v2/+++> por meio
    de um navegador e faça **login** usando as credenciais do seu
    locatário disponíveis na guia **Resources**.

2.  De volta ao Copilot Studio, selecione **Publish** no canto superior
    direito da página do agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

3.  Marque a caixa de seleção **Force newest version** e, em seguida,
    selecione **Publish** na caixa de diálogo de confirmação.

![](./media/image52.png)

![](./media/image53.png)

4.  Selecione **Channels** na barra de navegação superior.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

5.  Selecione **Teams and Microsoft 365 Copilot** na lista de canais
    disponíveis.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

6.  Selecione **Add channel**.

![](./media/image56.png)

7.  Clique na opção **See agent in Teams** para adicionar o agente ao
    Teams.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

8.  Isso abrirá o agente no Microsoft Teams. Selecione **Cancel** na
    janela pop-up **This site is trying to open Microsoft Teams** e, em
    seguida, selecione a opção **Use the Web App instead**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  Selecione **Add** para adicionar o agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

10. Após a adição, você terá a opção de abrir o agente. Selecione
    **Open**.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image61.png)

11. Teste o agente a partir do Teams.

![](./media/image62.png)

12. De volta ao Copilot Studio, feche a janela do canal Teams and
    Microsoft 365 Copilot.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

## Exercício 3 – Testar o agente Safe Travels existente

Neste exercício, testaremos o agente **Safe Travels** para ver como ele
responde quando questionado sobre a aprovação de viagens.

1.  De volta ao Copilot Studio -\> Safe Travels agent, selecione o ícone
    **Test** para testar o agente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

2.  Insira +++Need travel approval+++ na janela Test e pressione
    **Enter**.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image65.png)

3.  Você pode observar que o agente responde com um conjunto de
    instruções gerais que devem ser seguidas para obter a aprovação de
    viagem.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image66.png)

## Exercício 4 – Aprimorar o agente com ativos de conhecimento específicos da empresa

Neste exercício, adicionaremos um ativo de conhecimento — a **Política
de Viagens** específica da Contoso.

1.  Na página Overview do agente, role para baixo e selecione **+ Add
    knowledge**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

2.  Clique na opção **select to browse**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

3.  Na pasta **C:\Labfiles\Lab Files**, selecione **Travel Policy.docx**
    e clique em **Open**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

4.  Clique em **Add to agent** para adicionar o arquivo.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image70.png)

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image71.png)

5.  Certifique-se de que o arquivo foi adicionado. Aguarde até que o
    status mude de **In progress** para **Ready**. Você pode continuar
    com a próxima etapa enquanto o status é alterado para Ready, caso
    esse processo leve mais do que alguns minutos.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image73.png)

6.  Agora, teste o agente com a mesma pergunta para verificar que ele
    responde utilizando as políticas específicas da empresa a partir do
    ativo de conhecimento adicionado.

## Resumo

Neste laboratório, você criou um agente de **assistência em viagens
Business-to-Employee (B2E)** usando o **modelo de agente Safe Travels**
no Microsoft Copilot Studio. Você explorou como os modelos de agente
fornecem um ponto de partida rápido, pré-configurando recursos de
conversação e fontes de conhecimento, ao mesmo tempo que permitem
personalizações futuras para atender aos requisitos organizacionais e
legais. Usando o **site de viagens dos EUA** integrado como **fonte de
conhecimento**, você testou a capacidade do agente de responder a
perguntas relacionadas a viagens de funcionários por meio de interações
em linguagem natural. Por fim, você **publicou** o agente no **Microsoft
Teams e no Microsoft 365 Copilot**, validou sua disponibilidade no Teams
e confirmou que os funcionários podem acessar e interagir com o agente
Safe Travels diretamente em suas ferramentas de colaboração diárias.

 
