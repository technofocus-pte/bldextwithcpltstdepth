# Laboratório 3 - Arquitetando agentes inteligentes com base no conhecimento e conectores ativos

**Introdução**

Os usuários modernos esperam respostas inteligentes e contextuais que
vão além da simples correspondência de palavras-chave. Este laboratório
irá guiá-lo na criação de um agente inteligente capaz de raciocinar com
base em várias fontes de conhecimento e realizar ações em tempo real
para fornecer respostas abrangentes e precisas.

**Objetivo**

Neste laboratório, você criará um assistente inteligente que vai além de
simples perguntas e respostas para fornecer respostas contextuais e com
várias partes. Ao final do laboratório, você irá:

Criar um agente inteligente usando a experiência de criação de
conversas. Configurar o tom, o comportamento e as instruções do agente
para refletir sua marca. Adicionar sites públicos como a Wikipedia como
fontes de conhecimento para fundamentação factual. Desativar o
conhecimento geral para reduzir alucinações e garantir a precisão.

## Tarefa 1: Criar um novo agente e adicionar conhecimento

Crie a Nova AI com instruções personalizadas e integração de
conhecimento da Wikipedia usando a experiência de configuração
conversacional do Copilot Studio.

1.  Abra um navegador, acesse +++copilotstudio.microsoft.com+++ e faça
    login com suas credenciais.

2.  Selecione o ambiente **Dev One**.

3.  Na página inicial, selecione **Create agent**.

![](./media/image1.png)

4.  Depois que o agente for criado, selecione **Edit** na seção
    **Details**.

![](./media/image2.png)

5.  Insira os detalhes abaixo e selecione **Save**.

    - Name - +++Researcher agent+++.

    - Description - +++Answers multi-part questions by combining
      historical facts, biographical data, and real-time information
      like weather. Ideal for deep research, exploration, and knowledge
      synthesis+++

> ![](./media/image3.png)

6.  Insira o conteúdo abaixo em **Instructions** e selecione **Save**.

You should answer complex questions using verified public information
and real-time lookups like weather or conversions. You should give
clear, concise answers and handle multiple questions one at a time. You
must not speculate, share unverified or sensitive information, or
compare products or companies. You should communicate clearly and
professionally, using a friendly tone and light emojis when appropriate.

![](./media/image4.png)

7.  Role para baixo e selecione **+ Add knowledge** para adicionar uma
    fonte de conhecimento.

![](./media/image5.png)

8.  Selecione a opção **Public Website** na lista.

![](./media/image6.png)

9.  Na tela seguinte, selecione **Add** e, em seguida, **Add to agent**.

![](./media/image7.png)

![](./media/image8.png)

10. Em seguida, você irá desativar o conhecimento geral para reduzir
    alucinações. Selecione **Settings** no canto superior direito.

![](./media/image9.png)

11. Na seção Knowledge, alterne a opção **Use general knowledge** para
    **off**.

![](./media/image10.png)

12. Insira a mensagem abaixo no painel Test, clique em **Send** e
    observe a saída.

> Write a draft email to request refund from a toaster that is not
> working properly (bread keeps burning)

![](./media/image11.png)

![](./media/image12.png)

## Tarefa 2 – Adicionar o conector de clima

Nesta tarefa, você adicionará um conector de clima para habilitar a
recuperação de dados em tempo real e testar a orquestração generativa.
Certifique-se de que o agente forneça apenas respostas baseadas em fatos
e controladas, ao mesmo tempo em que esteja habilitado a executar ações
em tempo real, como consultas de clima, para respostas abrangentes e em
várias etapas.

1.  Selecione a guia **Tools** no menu superior.

![](./media/image13.png)

2.  Insira +++MSN Weather+++ na caixa de pesquisa e selecione **Get
    current weather**.

![](./media/image14.png)

3.  Selecione o menu suspenso ao lado da mensagem **Not connected** e
    escolha **Create new connection**. Em seguida, na tela seguinte,
    selecione **Create**.

![](./media/image15.png)

![](./media/image16.png)

4.  Selecione **Add and configure** para adicionar a ferramenta ao
    agente e configurá-la conforme necessário.

![](./media/image17.png)

5.  Após a adição, selecione **Additional details**.

![](./media/image18.png)

6.  Em Credentials to use, selecione **Maker-provided credentials**.

**Observação:** ao utilizar Maker-provided credentials, o usuário final
do agente não é solicitado a usar seu próprio contexto e conexão para se
conectar ao serviço. Em vez disso, são utilizados o contexto e a conexão
da pessoa que configurou o agente. Utilize a autenticação do autor
apenas para ações que não exigem dados específicos do usuário, pois o
uso das credenciais de outra pessoa pode expor riscos de exfiltração de
dados. Utilize a autenticação do usuário em cenários de acesso baseado
em funções. Sempre revise as implicações de segurança das escolhas de
autenticação.

![](./media/image19.png)

7.  Em **Inputs**, **Units** → **Fill using** → selecione **Custom
    value** e escolha **Metric**.

![](./media/image20.png)

8.  Em **Inputs**, para **Location**, mantenha **Fill using** **para**
    **Dynamically fill with AI** e selecione **Customize** para definir
    a descrição.

![](./media/image21.png)

9.  Defina a descrição conforme abaixo e, em seguida, selecione
    **Save**.

The location for the weather query. Valid inputs are City, State,
Country. Always include city and country, and state only for locations
where appropriate (e.g., in the US)

![](./media/image22.png)

![](./media/image23.png)

10. Teste seu agente aprimorado com a seguinte pergunta complexa:

> Who is the current CEO of the company that owns GitHub? Where did they
> earn their MBA? What's the average rent for a one-bedroom apartment
> near that campus? What's the air quality index in that area today?

![](./media/image24.png)

11. Observe como a orquestração generativa realiza múltiplas pesquisas e
    aciona o conector de clima para fornecer uma resposta abrangente.

![](./media/image25.png)

## Tarefa 3 – Ajustar seu assistente de AI para conversas mais fluidas

Personalize os tópicos do sistema para aprimorar as interações e
oferecer uma experiência de usuário mais fluida.

Nesta seção, você irá personalizar os tópicos de sistema integrados para
melhorar as interações com o usuário e criar uma experiência mais
contínua, indo além do uso apenas de fontes de conhecimento.

Personalize a mensagem de boas-vindas do seu assistente para torná-la
mais envolvente, adicione sugestões de prompts iniciais para orientar os
usuários de forma eficaz e refine tópicos do sistema, como Escalate,
para garantir que eles estejam alinhados com as necessidades da sua
organização.

1.  No menu superior, selecione **Topics**.

![](./media/image26.png)

2.  Em **System**, selecione o tópico **Conversation Start**.

![](./media/image27.png)

3.  No nó **Message** do tópico, insira a mensagem abaixo.

> Hi there! I'm Researcher agent, your intelligent assistant for deep
> research and discovery. I can break down complex questions and combine
> insights from historical facts, biographies, and real-time data like
> the weather. What are you curious about today?
>
> ![](./media/image28.png)

4.  Ainda no mesmo nó, selecione **+ Add → Quick reply**.

![](./media/image29.png)

5.  Adicione a pergunta abaixo.

+++What caused the fall of the Roman Empire?+++

![](./media/image30.png)

6.  Da mesma forma, adicione mais 2.

> +++Who is the current CEO of the company that owns GitHub? Where did
> they earn their MBA? What's the average rent for a one-bedroom
> apartment near that campus? What's the air quality index in that area
> today?+++
>
> +++What's the temperature in the city that hosted the last Olympic
> Games?+++

![](./media/image31.png)

7.  Após adicionar, selecione **Save** para salvar o tópico.

![](./media/image32.png)

8.  Personalize a experiência de escalonamento. Selecione **Topics →
    System → Escalate**.

![](./media/image33.png)

9.  Atualize o texto conforme abaixo, de modo que ele ajude de forma
    mais significativa a desbloquear o usuário final, e selecione
    **Save**.

> I'm sorry, but I can't seem to be able to help you. I recommend
> reaching out to our \[Microsoft Copilot Studio community\]
> (https://aka.ms/CopilotStudioCommunity) or submitting a \[support
> request\]
> (<https://learn.microsoft.com/en-us/power-platform/admin/get-help-support>).

![](./media/image34.png)

## Tarefa 4 – Tornar seu agente público e publicá-lo no site de demonstração

Nesta seção, você irá remover a autenticação para tornar o agente
publicamente acessível e, em seguida, publicá-lo no site de demonstração
para testes e compartilhamento. Como o agente Researcher fornece
informações gerais e não lida com dados privados, você desativará a
autenticação para oferecer uma experiência de usuário fluida e publicará
o agente no site de demonstração para coletar feedback antes de
implementá-lo em seu site real.

1.  Vá para **Settings**.

![](./media/image35.png)

2.  Selecione **Security → Authentication**. Selecione **No
    authentication** e, em seguida, **Save**.

![](./media/image36.png)

3.  Selecione **Save** no prompt de confirmação.

![](./media/image37.png)

4.  Agora você pode fechar o painel Settings.

![](./media/image38.png)

5.  Selecione **Publish** para tornar suas alterações ativas.

![](./media/image39.png)

6.  Selecione **Publish** na caixa de diálogo de confirmação.

![](./media/image40.png)

7.  Você receberá uma mensagem de sucesso assim que a publicação for
    concluída.

![](./media/image41.png)

8.  Agora, selecione **Channels** no menu superior.

![](./media/image42.png)

9.  Selecione **Demo website** na lista de canais disponíveis.

![](./media/image43.png)

10. Insira a mensagem de boas-vindas como +++Welcome to your demo
    website+++ e selecione **Save**.

![](./media/image44.png)

11. Clique em **Open demo website** para abrir o seu site.

![](./media/image45.png)

12. Agora você pode interagir com seu agente.

![](./media/image46.png)

## Summary

Neste laboratório, você entregou com sucesso um agente inteligente de
acesso público que:

- Responde a perguntas de pesquisa complexas e com múltiplas partes

- Utiliza conhecimento público verificado e conectores em tempo real

- Minimiza alucinações por meio de fontes de conhecimento controladas

- Fornece uma experiência conversacional refinada e amigável ao usuário

- Está implementado e acessível por meio de um site de demonstração
  ativo

Este laboratório demonstra como projetar, aprimorar e publicar um
**agente inteligente pronto para produção**, que vai além de simples
perguntas e respostas para fornecer insights confiáveis, em tempo real e
sensíveis ao contexto.
