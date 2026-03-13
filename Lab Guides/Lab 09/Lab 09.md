# Laboratório 9 – Testar, medir e aprimorar agentes de AI

À medida que os agentes de AI assumem papéis críticos nos processos de
negócio, a necessidade de testes confiáveis e repetíveis torna-se
essencial. A avaliação de agentes permite gerar testes que simulam
cenários do mundo real para o seu agente. Esses testes abrangem mais
perguntas em menos tempo do que testes manuais, caso a caso. Em seguida,
é possível medir a precisão, a relevância e a qualidade das respostas às
perguntas feitas ao agente, com base nas informações às quais o agente
tem acesso. Ao utilizar os resultados do conjunto de testes, você pode
otimizar o comportamento do agente e validar se ele atende aos
requisitos de negócio e de qualidade.

**Objetivo**

Neste laboratório, você aprenderá a testar e avaliar sistematicamente um
agente de AI utilizando os recursos integrados de avaliação e análises
do Copilot Studio. Você criará um conjunto de testes automatizado que
simula cenários reais de usuários, medirá a qualidade e a precisão das
respostas do agente e analisará dados de desempenho para identificar
lacunas e oportunidades de melhoria. Ao final do laboratório, você será
capaz de validar que o agente atende aos padrões de negócio,
confiabilidade e qualidade antes do uso em produção.

## Tarefa 1 – Criar um conjunto de testes para avaliar seu agente

Antes de implementar um agente de AI em fluxos de trabalho reais, é
fundamental validar sua capacidade de responder a perguntas realistas
dos usuários. Os testes manuais são demorados e muitas vezes deixam
passar casos extremos. Nesta tarefa, você usará os recursos de avaliação
de agentes do Copilot Studio para gerar automaticamente um conjunto de
testes que simula cenários do mundo real. Você executará esses testes em
seu agente, analisará os resultados de aprovação e reprovação e
identificará lacunas em termos de precisão, relevância ou comportamento
que precisam ser melhoradas.

1.  No Copilot Studio, selecione o **Hiring Agent**.

![](./media/image1.png)

2.  Na barra de menu superior, selecione **Evaluation**. Em seguida,
    selecione **Create a test set**.

![](./media/image2.png)

3.  Existem algumas opções para criar o conjunto de testes. Neste caso,
    selecione **Generate 10 questions**.

![](./media/image3.png)

4.  **Revise** o conjunto de testes e, em seguida, selecione **Save**
    para salvá-lo.

![](./media/image4.png)

5.  Agora, clique em **Evaluate** para avaliar o agente.

![](./media/image5.png)

6.  Selecione o ID do seu locatário e clique em **Run**.

![](./media/image6.png)

7.  Aguarde até que a execução seja concluída.

![](./media/image7.png)

8.  Após a conclusão da avaliação, clique nela para visualizar os
    detalhes.

![](./media/image8.png)

9.  Analise cada pergunta e veja por que ela falhou e quais foram
    aprovadas. Isso ajudará você a aprimorar seu agente conforme
    necessário.

![](./media/image9.png)

## Tarefa 2: Obtenha insights com a análise de agentes

Depois que um agente é avaliado e usado ativamente, o monitoramento
contínuo é essencial para garantir desempenho consistente e
confiabilidade em escala. Nesta tarefa, você explorará os recursos de
análise do Copilot Studio para obter insights sobre o uso do agente, as
tendências de execução e a utilização dos componentes. Você aprenderá
como os dados analíticos ajudam a identificar gargalos de desempenho,
compreender os padrões de interação do usuário e orientar a otimização
contínua do seu agente ao longo do tempo.

1.  Na barra de menu superior, selecione **Analytics.**

> ![](./media/image10.png)

2.  À medida que houver um maior número de execuções e o agente passar a
    ser usado com mais frequência, o tráfego aumentará, e você poderá
    visualizar o AI Summary na guia Analytics.

> ![](./media/image11.png)

3.  A seção **Overview** fornece uma visão geral das execuções e dos
    créditos.

> ![](./media/image12.png)

4.  A seção Run outcomes apresenta as tendências de duração média das
    execuções.

> ![](./media/image13.png)

5.  Role para baixo e, na seção Use, você poderá ver o uso de
    acionadores, ferramentas e fontes de conhecimento.

> ![](./media/image14.png)

6.  Cada uma dessas informações ajuda a avaliar o uso de cada componente
    do agente e a atualizar, aprimorar ou corrigir suas funcionalidades
    de forma adequada.

## Resumo

Neste laboratório, você implementou avaliações e análises automatizadas
para avaliar a qualidade e a confiabilidade de um agente de AI. Você
gerou um conjunto de testes para simular interações realistas com
usuários, executou avaliações para medir a precisão e a relevância das
respostas e analisou os resultados de aprovação/reprovação para
identificar áreas que precisam ser melhoradas.

Você também explorou a análise do agente para entender os padrões de
uso, as tendências de execução e a utilização de componentes entre
acionadores, ferramentas e fontes de conhecimento. Em conjunto, esses
recursos permitem ir além dos testes manuais e adotar uma abordagem
escalável e orientada por dados para validação de agentes. Este
laboratório demonstra como os testes e análises automatizados ajudam a
garantir que seus agentes sejam confiáveis, tenham bom desempenho e
estejam prontos para cenários de negócios do mundo real.

.
