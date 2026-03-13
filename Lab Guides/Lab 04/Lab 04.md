# Laboratório 4 – Criar um agente inteligente de recrutamento para aquisição de talentos

Neste laboratório, você estabelecerá a base do seu sistema de automação
de recrutamento. Você começará importando uma solução pré-configurada
que contém todas as tabelas do Dataverse e a estrutura de dados
necessária para gerenciar candidatos, vagas e fluxos de trabalho de
recrutamento. Em seguida, você preencherá essas tabelas com dados de
exemplo, que darão suporte ao seu aprendizado ao longo deste módulo e
fornecerão cenários realistas para testes. Por fim, você criará o Hiring
Agent no Copilot Studio, configurando a interface conversacional básica
que servirá como base para todos os outros recursos que você adicionará
em missões futuras.

## Exercício 1 – Importar solução

Neste exercício, você irá importar uma solução existente.

1.  Acesse o Copilot Studio em +++https://copilotstudio.microsoft.com+++

2.  Selecione o ícone ... na navegação à esquerda e selecione
    **Solutions.**

![](./media/image1.png)

3.  Selecione **Import solution**. Clique em **Browse**, selecione o
    arquivo **.zip** que começa com **Operative** na pasta
    **C:\LabFiles** e, em seguida, selecione **Open**.

![](./media/image2.png)

![](./media/image3.png)

![](./media/image4.png)

4.  Após selecionar o arquivo, selecione **Next** e, em seguida,
    selecione **Import**.

![](./media/image5.png)

![](./media/image6.png)

5.  Esse processo levará algum tempo, cerca de 3 a 5 minutos. Quando for
    concluído com sucesso, você verá uma barra de notificação verde com
    a seguinte mensagem: "Solution "Operative" imported successfully".

![](./media/image7.png)

6.  Quando você vir a mensagem "imported successfully", examine o que
    foi importado selecionando o nome de exibição da solução
    **(Operative)** na lista de soluções.

![](./media/image8.png)

7.  Revise a solução e verifique se os seguintes componentes foram
    importados.

![](./media/image9.png)

8.  Selecione o botão Publish all customizations na parte superior da
    página.

![](./media/image10.png)

## Exercício 2 - Importar dados de amostra

Neste exercício, você adicionará dados de amostra a algumas das tabelas
importadas no exercício anterior.

1.  A partir da solução que você importou no exercício anterior,
    selecione o aplicativo baseado no modelo **Hiring Hub** marcando a
    caixa de seleção à frente da linha e, em seguida, selecione o botão
    **Play** na parte superior.

> ![](./media/image11.png)

2.  Selecione **Job Roles** na navegação à esquerda. Na barra de
    comandos, selecione o ícone **More** (três pontos verticais) e, em
    seguida, selecione a **seta para a direita** ao lado de **Import
    from Excel.**

![](./media/image12.png)

3.  Selecione **Import from CSV**.

![](./media/image13.png)

4.  Selecione o botão **Choose File**, escolha o arquivo
    **job-roles.csv** na pasta **C:\LabFiles** e, em seguida, selecione
    **Open**.

![](./media/image14.png)

5.  Selecione **Next**. Mantenha a próxima etapa como está e selecione
    **Review Mapping.**

![](./media/image15.png)

![](./media/image16.png)

6.  Certifique-se de que o mapeamento esteja correto e selecione
    **Finish Import**.

![](./media/image17.png)

7.  Selecione **Done**. Esse processo pode levar um pouco de tempo, mas
    você pode clicar no botão **Refresh** para verificar se a importação
    foi concluída com sucesso.

![](./media/image18.png)

![](./media/image19.png)

8.  Agora, você irá importar os **dados de exemplo de Evaluation
    Criteria.**

9.  Selecione **Evaluation Criteria** na navegação à esquerda.

10. Selecione **Import from CSV**, como feito anteriormente. Selecione o
    botão **Choose File** e escolha o arquivo
    **evaluation-criteria.csv** na pasta **C:\LabFiles**.

![](./media/image20.png)

11. Selecione **Next**. Mantenha a próxima etapa como está e selecione
    **Review Mapping**.

![](./media/image21.png)

![](./media/image22.png)

12. Agora precisamos realizar um pouco mais de trabalho no mapeamento.
    Selecione o **ícone de** **lupa** ao lado do campo **Job Role**.

![](./media/image23.png)

13. Certifique-se de que **Job Title** esteja selecionado e, caso não
    esteja, adicione-o e selecione **OK.**

![](./media/image24.png)

14. Certifique-se de que o restante do mapeamento também esteja correto,
    selecione **Finish Import** e, em seguida, selecione **Done**.

![](./media/image25.png)

15. Esse processo pode levar um pouco de tempo, mas você pode clicar no
    botão **Refresh** para verificar se a importação foi concluída com
    sucesso.

![](./media/image26.png)

## Exercício 3 – Criar o hiring agent

Agora que você concluiu a configuração dos pré-requisitos, é hora do
trabalho principal! Vamos adicionar primeiro o Hiring Agent!

1.  No Copilot Studio, selecione Agents no painel esquerdo. Selecione o
    menu suspenso ao lado de + Create blank agent e, em seguida,
    selecione Advanced create.

![](./media/image27.png)

2.  Em Agent settings, selecione Solution como **Operative** e, em
    seguida, selecione **Confirm and create**.

![](./media/image28.png)

3.  Selecione **Edit** na seção Details do agente criado.

![](./media/image29.png)

4.  Insira o Name como +++**Hiring Agent**+++ e a Description como +++
    **Central orchestrator for all hiring activities** +++ e selecione
    **Save**.

> ![](./media/image30.png)

## Resumo

> Neste laboratório, você concluiu com sucesso as seguintes etapas:

- **Compreensão do cenário**: conhecimento abrangente dos desafios da
  automação de recrutamento e da solução que será construída.

- **Implementação da solução**: importação e configuração bem-sucedidas
  dos blocos fundamentais do sistema de gerenciamento de recrutamento.

- **Criação do agente**: construção de um Hiring Agent que representa o
  início do cenário que você irá desenvolver como um Agent Academy
  Operative.
