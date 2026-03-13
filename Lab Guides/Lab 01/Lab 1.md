# Laboratório 1 – Projetando um assistente de AI com o Copilot Studio Agent Builder

**Objetivo**

Neste laboratório, você aprenderá a criar um agente conversacional
personalizado usando o **Copilot Studio Agent Builder**, descrevendo o
propósito, o comportamento e o tom do agente em linguagem natural. Você
irá projetar um **Gardening Assistant agent** (**Assistente de
Jardinagem)** que fornece orientações especializadas sobre jardinagem
doméstica, com foco no cuidado com as plantas, nas melhores práticas e
na importância da natureza no dia a dia. Ao final do laboratório, você
compreenderá como refinar iterativamente as instruções do agente e dar
vida a um assistente funcional e específico de domínio.

## Exercício 1: Criando o agente

1.  Abra o link +++<https://m365.cloud.microsoft/chat+++> em um
    navegador e faça login com suas credenciais.

    - Nome do usuário
      - <+++@lab.CloudPortalCredential>(User1).Username+++

    - Senha - <+++@lab.CloudPortalCredential>(User1).Password+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image1.png)

2.  Selecione **New agent** no painel **esquerdo**. Se você **não**
    conseguir visualizar a opção **New agent**, **atualize** o
    **navegador** e tente novamente após alguns minutos. Em alguns
    casos, pode levar alguns minutos para que a página seja carregada
    completamente.

![](./media/image2.png)

3.  Selecione a guia **Describe**.

![](./media/image3.png)

4.  Você pode começar a definir o agente personalizado. É possível
    escolher um modelo para iniciar ou simplesmente *descrever* o agente
    fornecendo uma descrição em linguagem natural. Vamos inserir a
    seguinte descrição inicial:

> +++You are an expert gardener, and you help users to maintain and
> improve their home garden providing detailed instructions and advice
> about the best practices for home gardening.+++

![](./media/image4.png)

5.  Após fornecer as instruções, os detalhes iniciais são preenchidos
    automaticamente.

6.  Você pode renomear o agente, se necessário. Para isso, forneça o
    seguinte prompt:

> +++Name it as “Gardening assistant”+++.

![](./media/image5.png)

7.  Se for solicitado que você refine ainda mais as instruções, forneça
    a seguinte frase:

+++Focus on suggesting ways to keep plants and flowers shining and
gorgeous+++

![](./media/image6.png)

8.  Continue interagindo com o Agent Builder até que ele tenha todas as
    informações necessárias para criar o agente. Forneça a seguinte
    frase:

> +++Focus on highlighting the importance of nature and plants/flowers
> to be present in every house!+++
>
> ![](./media/image7.png)
>
> ![](./media/image8.png)

9.  Em seguida, forneça uma instrução sobre o tom do agente, conforme
    abaixo:

+++Use a professional, yet friendly, tone.+++

> ![](./media/image9.png)

11. Clique em **Create**, no canto superior direito, para criar o
    agente.

![](./media/image10.png)

![](./media/image11.png)

12. Selecione **Go to agent** assim que o agente for criado.

![](./media/image12.png)

13. Isso abre o agente criado.

![](./media/image13.png)

> \[!Alerta\] **Alerta:** Se o agente não abrir automaticamente,
> **atualize** a página e selecione o **gardening agent criado** no
> painel esquerdo.
>
> ![](./media/image14.png)

14. Exemplo de prompt para conversar com o agente.

> +++Give me tips to keep Rose plants fresh+++

![](./media/image15.png)

## Resumo:

Neste laboratório, você criou um agente **Gardening Assistant agent**
(**Assistente de Jardinagem)** usando a experiência Agent Builder do
Copilot Studio. A partir de uma descrição simples em linguagem natural,
você definiu a função do agente como um especialista em jardinagem e, de
forma progressiva, refinou seu foco, tom e personalidade por meio de
prompts interativos. Você personalizou o agente para fornecer
orientações profissionais e amigáveis sobre jardinagem, com ênfase em
manter as plantas saudáveis, vibrantes e visualmente atraentes, além de
destacar o valor das plantas e flores em todos os lares. Após criar e
publicar o agente, você validou seu comportamento interagindo com ele
por meio de prompts reais de usuários, como a solicitação de dicas para
manter roseiras sempre viçosas.

Este laboratório demonstrou como é possível criar de forma rápida e
intuitiva um agente com propósito específico usando o Copilot Studio —
sem escrever código — aproveitando o design conversacional e o
refinamento iterativo das instruções.

.
