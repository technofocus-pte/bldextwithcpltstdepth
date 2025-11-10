# Laboratório 02 - Configurar o Dynamics 365 Customer Service

## Objetivo

Neste laboratório, você criará um grupo de segurança no Azure para
atualizar as configurações no Copilot Studio e, em seguida, ativará a
avaliação do **Dynamics 365 Customer Service**.

## Tarefa 1: Criar grupo de segurança no Entra ID e configurar autores do Copilot Studio

1.  Navegue até o portal do Azure +++https://portal.azure.com/+++ e faça
    login com suas credenciais.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  Selecione **Next** na janela **Keep your account secure** e siga as
    **instruções**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Baixe o aplicativo Authenticator em seu telefone, caso ainda não o
    tenha.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  Siga as instruções e conclua a configuração.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

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

7.  No painel esquerdo, selecione **Manage** -\> **Groups**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  Selecione **New group** para criar um novo grupo de segurança.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  Insira os detalhes abaixo

- **Group type** – Selecione **Security**

- **Group name** – Insira +++**copilotagentsecurity**+++

- **Microsoft Entra roles can be assigned to the group** – Selecione
  **Yes**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. Selecione **No owners selected**, selecione **MOD Administrator** na
    página **Add owners** e clique em **Select**.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. Da mesma forma, selecione **No members selected**, e adicione **MOD
    Administrator** na lista e clique em **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. Selecione **No roles selected**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. Pesquise e selecione +++**Global Admin**+++ e selecione **Select**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. Selecione **Create** depois que todos os detalhes forem adicionados
    e selecione **Yes** na caixa de diálogo de confirmação.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. Certifique-se de receber uma mensagem de sucesso.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. Em uma nova guia, navegue até
    +++https://powerplatform.microsoft.com+++. Selecione **Manage** no
    painel esquerdo e selecione a opção **Tenant Settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. Selecione **Copilot Studio authors** na lista disponível.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. Clique no ícone **Edit** para editar as configurações.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. Pesquise e selecione o grupo **copilotagentsecurity** que você criou
    anteriormente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. Selecione **Save** para salvar as configurações.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

## Tarefa 2: Inscrever-se na avaliação do Dynamics 365 Customer Service

1.  Login em
    +++<https://dynamics.microsoft.com/en-us/customer-service/overview/+++>

2.  Faça login usando os **detalhes do locatário do Office 365** na guia
    **Home**, se solicitado.

3.  Clique em **Try for free**

![](./media/image28.png)

4.  Insira seu **nome de usuário administrativo do Office 365** na guia
    **Resources**, marque a caixa de seleção e clique em **Start your
    free trial**.

![](./media/image29.png)

5.  Insira a região como **United States**, digite seu número de
    telefone em **Phone number** e clique em **Submit**.

![](./media/image30.png)

6.  Se você vir uma opção **Launch Trial** em **Engage customers**,
    clique em **Launch Trial**.

![](./media/image31.png)

7.  Uma vez ativado, seu **Customer Service workspace** será aberto.

![](./media/image32.png)

## Resumo

Neste laboratório, ativamos o Dynamics 365 Customer Service, que será
usado no **Laboratório 04 - Integrar um agente ao aplicativo Dynamics
365 Customer Service e implementar o escalonamento automatizado de
ocorrências para o agente ao vivo**.
