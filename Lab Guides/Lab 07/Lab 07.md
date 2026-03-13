# Laboratório 7 – Criar um agente autônomo de recuperação de dados financeiros com Computer-Using Agents (CUA)

**Introdução**

Sistemas legados sem APIs criam grandes obstáculos para a automação. O
RPA tradicional geralmente depende de screen scraping (extração de dados
da tela) frágil ou de soluções manuais, o que retarda a tomada de
decisão, aumenta erros e reduz a produtividade. Este laboratório
apresenta o Microsoft Copilot Studio e os Computer-Using Agents (CUA)
como uma solução mais inteligente. Ao simular a interação humana com
sistemas internos, os CUAs podem acessar e processar dados de forma
segura, sem a necessidade de integração via API. Você aprenderá a criar
um agente autônomo que oferece respostas mais rápidas, reduz o trabalho
manual e possibilita decisões informadas em tempo real.

Objetivo

Neste laboratório, você aprenderá a criar um agente autônomo usando o
Microsoft Copilot Studio. Esse agente irá simular a interação humana com
um sistema interno legado para recuperar dados de portfólio financeiro
sem exigir acesso direto por API.

## Tarefa 1 – Criar e configurar um agente autônomo

Nesta tarefa, você irá criar um novo agente autônomo no Microsoft
Copilot Studio, configurar sua identidade e configurar um gatilho de
e-mail usando o conector Microsoft 365 Outlook.

Para automatizar a consulta de portfólios, o agente deve ser capaz de
detectar solicitações de e-mail recebidas e iniciar o fluxo de automação
apropriado com base na filtragem da linha de assunto.

1.  Faça login no Copilot Studio em
    +++https://copilotstudio.microsoft.com+++ usando suas credenciais de
    acesso.

2.  Selecione o ambiente Dev One no canto superior direito.

![](./media/image1.png)

3.  Selecione **Create an agent**.

![](./media/image2.png)

4.  Depois que o agente for criado, selecione **Edit** em **Details**.

![](./media/image3.png)

5.  Insira o Name como +++Portfolio Lookup Agent+++ e selecione Save
    para renomear o nome padrão do agente.

![](./media/image4.png)

6.  Role a página até a seção Triggers e clique em **+ Add trigger**.

![](./media/image5.png)

7.  Pesquise e selecione **When a new email arrives (V3)** (**Office 365
    Outlook**) e clique em **Next**.

![](./media/image6.png)

8.  Renomeie o acionador para +++When a portfolio lookup email
    arrives+++, certifique-se de que a conexão esteja estabelecida para
    o **Copilot Studio** e o **Outlook** e, em seguida, clique em
    **Next**.

![](./media/image7.png)

9.  No campo **Subject Filter (Optional)**, insira +++Portfolio+++ na
    linha de assunto.

![](./media/image8.png)

10. Depois que o acionar for criado, você pode **fechar** a caixa de
    diálogo Time to test your trigger.

![](./media/image9.png)

## Tarefa 2: Adicionar a ferramenta Computer Use

Nesta tarefa, você irá configurar uma ferramenta Computer Use que faz
login em um computador, navega por um site, pesquisa e recupera dados de
portfólio financeiro. Em seguida, você usará o conector Office 365
Outlook para responder com os dados solicitados.

1.  Navegue até **Tools** no menu de nível superior.

![](./media/image10.png)

2.  Selecione **+ Add a tool.**

![](./media/image11.png)

3.  Selecione **+ New tool**.

![](./media/image12.png)

4.  Selecione **Computer use (preview)**.

![](./media/image13.png)

5.  Adicione as seguintes instruções e, em seguida, selecione **Add and
    configure**.

&nbsp;

1.  Acesse
    <https://computerusedemos.blob.core.windows.net/web/Portfolio/index.html>.

2.  Insira o Portfolio ID no campo de pesquisa "Enter Portfolio ID" e
    clique no botão "Search".

3.  Recupere os valores "Client Name", "Portfolio Value" e "Manager"
    exatamente como exibidos.

4.  Retorne esses três valores como resultado final. Se nenhum dado do
    portfólio for encontrado, responda que não foi possível encontrar um
    portfólio com o ID especificado.

![](./media/image14.png)

6.  Atualize o **Name** da ferramenta Computer use para +++Look up
    portfolio data+++.

7.  Atualize a **Description** para +++Search and retrieve financial
    portfolio data+++.

![](./media/image15.png)

8.  Na seção Inputs, selecione **+ Add input**.

![](./media/image16.png)

9.  Insira o name como +++Portfolio ID+++ e a description como +++The ID
    of the portfolio+++ e selecione **Done**.

![](./media/image17.png)

10. Selecione **Save**.

![](./media/image18.png)

## Tarefa 3: Testar a ferramenta Computer Use

1.  Na seção **Instructions**, selecione o botão **Test**, localizado à
    direita.

![](./media/image19.png)

2.  Adicione o valor de exemplo +++44123BCD+++ e selecione **Test now**.

![](./media/image20.png)

3.  Observe a ferramenta Computer Use fazendo login no computador e
    executando as ações solicitadas:

    - O painel esquerdo mostra suas instruções e um log passo a passo do
      raciocínio e das ações da ferramenta.

    - O painel direito exibe uma visualização das ações na máquina que
      você configurou para uso do computador.

![](./media/image21.png)

> ![](./media/image22.png)

![](./media/image23.png)

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

4.  Selecione **Finish testing**.

![](./media/image27.png)

## Tarefa 4: Configurar recursos de resposta por e-mail

Nesta tarefa, você configurará o recurso de e-mail.

1.  Retorne à guia **Tools** e selecione **+ Add a tool**.

![](./media/image28.png)

2.  Pesquise por +++**Send an email (V2) (Office 365 Outlook)**+++ e
    selecione essa opção.

![](./media/image29.png)

3.  Selecione **Add and configure**.

![](./media/image30.png)

4.  Atualize o **Name** para +++Reply to email+++ e a **Description**
    para +++Use this operation to reply to the email received+++ e, em
    seguida, selecione **Additional details**.

![](./media/image31.png)

5.  Em **Additional details**, defina **Credentials to use** como
    **Maker-provided credentials.**

![](./media/image32.png)

6.  Na seção **Inputs**, clique em **customize** ao lado da entrada
    **To** e defina a **Description** como +++Use the "from" email of
    the triggering received email+++.

![](./media/image33.png)

![](./media/image34.png)

7.  **Personalize** a entrada **Subject** e defina a **Description**
    como +++Write the email subject+++.

![](./media/image35.png)

8.  Personalize a entrada **Body** e defina a **Description** como
    +++Write the email body using HTML and highlight the requested
    data+++.

![](./media/image36.png)

9.  Clique em **Save** para finalizar a configuração da ferramenta.

![](./media/image37.png)

10. Navegue até a guia **Overview** e, em seguida, **Edit** as
    instruções.

![](./media/image38.png)

11. Cole a seguinte instrução.

When a financial portfolio related request is received, identify the
Portfolio ID and search for the requested data using \< Look up
portfolio data \>. Once you have gathered the financial portfolio
information, use the \< Reply to email \> tool to reply to the original
email you received. Do not respond with data beyond what was requested.

![](./media/image39.png)

12. Selecione \< Look up portfolio data \>, digite / e selecione a
    ferramenta Look up portfolio data.

![](./media/image40.png)

![](./media/image41.png)

13. Da mesma forma, substitua \< Reply to email \> pela ferramenta
    **Reply to email**.

14. Depois que as substituições forem concluídas, conforme mostrado na
    captura de tela abaixo, selecione **Save**.

![](./media/image42.png)

15. Selecione **Settings** no canto superior direito.

![](./media/image43.png)

16. Na seção **Knowledge**, desative a opção **Use general knowledge** e
    selecione **Save**.

![](./media/image44.png)

17. Feche o painel **Settings**.

![](./media/image45.png)

## Tarefa 5: Testar o agente completo

Nesta tarefa, você irá testar o funcionamento completo do agente que foi
criado.

1.  Envie um e-mail de teste a partir de um endereço de e-mail de sua
    preferência para a conta de e-mail do seu usuário de treinamento
    com:

Subject: +++Portfolio data request+++

Body:

Hi!

I hope you're doing well!

I'm looking for the portfolio manager and value of portfolio \#44123BCD.
Much appreciated.

Thanks!

![](./media/image46.png)

2.  Certifique-se de que o e-mail seja recebido na caixa de entrada do
    usuário de treinamento.

3.  Na guia **Overview**, vá até a seção **Triggers** e selecione **Test
    trigger**.

![](./media/image47.png)

4.  Selecione a **instância trigger** e, em seguida, selecione **Start
    testing.**

![](./media/image48.png)

5.  A execução é realizada e você pode acompanhar as atualizações e o
    fluxo no painel Test.

![](./media/image49.png)

![](./media/image50.png)

6.  Após a execução ser concluída, verifique seu e-mail para conferir a
    resposta do agente.

![](./media/image51.png)

## Resumo

Neste laboratório, você criou um agente autônomo de recuperação de dados
financeiros usando o Microsoft Copilot Studio e Computer-Using Agents
(CUA). Você configurou um agente orientado a eventos que responde
automaticamente a solicitações por e-mail, simula a interação humana com
um sistema legado para recuperar dados de portfólio e retorna resultados
precisos sem depender de APIs.

Você aprendeu como:

- Projetar um agente autônomo que opera sem interação direta do usuário

- Usar acionadores baseados em e-mail para iniciar fluxos de trabalho
  automatizados

- Configurar Computer-Using Agents para navegar com segurança e extrair
  dados de aplicações web legadas

- Integrar ferramentas de ação para retornar resultados por e-mail

- Reduzir a dependência de padrões frágeis de RPA, utilizando interação
  com computador orientada por AI

Este laboratório demonstra como agentes autônomos com CUA podem
modernizar o acesso a sistemas legados, otimizar fluxos de trabalho
operacionais e possibilitar tomadas de decisão mais rápidas e confiáveis
em ambientes onde APIs não estão disponíveis.
