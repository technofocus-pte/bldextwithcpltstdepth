# **Laboratoire 07\_ Envoi de messages à partir d'un Copilot (classique) vers un canal Teams**

**Durée du laboratoire** – 30 minutes

**Objectif:**

Dans ce laboratoire, nous allons envoyer un message d'un Copilot à un
canal Teams en appelant un flux.

## **Exercice 1 : Ajouter un canal et une équipe dans Microsoft Teams**

1.  Ouvrez **Microsoft Teams** à partir de la machine virtuelle et
    connectez-vous à l'aide de vos informations d'identification de
    locataire si vous l'avez déjà fermée. Sélectionnez **l**'option
    **Teams.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

2.  Dans Teams, sélectionnez **More options** et sélectionnez **+ -\>
    Create team**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

3.  Nommez l'équipe comme +++**HR Team**+++, le canal comme +++**HR**
    **Experts**+++ et sélectionnez **Create**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

4.  Sélectionnez **Skip** à la window « Add members to HR Team».

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image4.png)

5.  Sélectionnez **Skip** à la window « Add members to the HR Experts
    channel’ window ![Une capture d'écran d'un ordinateur Description
    générée automatiquement](./media/image5.png)

## **Exercice 2 : Améliorer le sujet pour traiter des requêtes complexes en les faisant remonter à des experts RH**

1.  Dans l'application Teams, sélectionnez l'application Copilot Studio
    (Power Virtual Agents), sélectionnez l'onglet **Copilots** et ouvrez
    le **HR Support Copilot**

> ![](./media/image6.png)
>
> **Remarque :** Si le raccourci Copilot Studio est introuvable,
> recherchez **Copilot Studio/Power Virtual Agents under Apps** et
> sélectionnez **Open**)
>
> ![](./media/image7.png)

2.  Sélectionnez **Topics** dans le volet gauche, revenez à la rubrique
    que vous avez créée précédemment (**Employee time off**) et accédez
    au canevas de création.

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image8.png)

3.  Dans le **Ask a question node** , ajoutez une option nommée
    **Extended leave**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image9.png)

4.  Sous le nœud Condition de Congé prolongé, ajoutez un nœud de
    question demandant une description du problème et ajoutez le texte
    +++**How would you describe the issue** **?***+++*

> ![](./media/image10.png)

5.  Sélectionnez **User’s entire response** sous Identité et enregistrez
    la description dans une variable nommée +++**Description**+++.

> ![Une capture d'écran d'un écran d'ordinateur Description générée
> automatiquement](./media/image11.png)

6.  Sélectionnez **Save**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

7.  Ajoutez un nœud sous la question et sélectionnez **Call an action**.
    Sélectionnez **Create a flow** qui lance Power Automate dans le
    Copilot Studio dans Teams.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image13.png)

8.  Choisissez l'option **Power Virtual Agents Flow Template**.

![](./media/image14.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image15.png)

9.  Ajoutez un champ de saisie de **Text** en cliquant sur **+ Add an
    input** dans la première étape. Remplacez l'entrée par
    **Description**.

![Une capture d'écran d'ordinateur d'une erreur d'ordinateur Description
générée automatiquement](./media/image16.png)

10. Insérez une **new step** et sélectionnez **Add an action**.

![](./media/image17.png)

11. Sélectionnez **Microsoft Teams** sous **Choose an operation**.

![](./media/image18.png)

12. Sélectionnez **Post message in a chat or channel**.

![](./media/image19.png)

13. Fournissez les détails ci-dessous :

- Post as – **User**

- Post in – **Channel**

- Team – **HR Team**

- Channel – **HR Experts**

- Message **– Description** from **Dynamic Content**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image20.png)

14. Renommez le flux en +++**Send a message to HR Team**+++ et cliquez
    sur **Save**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image21.png)

15. Cliquez sur **Close** pour fermer Power Automate et revenir au
    Authring canvas.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image22.png)

16. À partir du canevas de création, ajoutez un nœud – **call an
    action**\> **Send a message to HR team**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image23.png)

17. Ajoutez l'entrée en tant que **Description**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image24.png)

18. Ajoutez un nœud de message avec le message, +++**We notified the
    expert. They’ll reach out shortly**+++.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image25.png)

19. End the conversation \> End the survey.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image26.png)

20. Cliquez sur **Save** pour enregistrer le sujet.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image27.png)

21. Un message de réussite de **Topic saved** est obtenu.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image28.png)

## **Exercice 3 : Testez votre chatbot**

1.  Sélectionnez Test votre chatbot dans le volet gauche.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image29.png)

2.  Envoyer un message +++**I** **need help with time off** +++ et
    sélectionnez Extended leave pour répondre au chatbot.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image30.png)

3.  Décrivez la raison de votre prolongation de congé. Ici, nous l'avons
    donné comme +++ **I need extended leave of one month for
    travelling**+++.

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image31.png)

4.  Le bot répond par le message « Nous avons notifié un expert..... ».

![Une capture d'écran d'un chatbot Description générée
automatiquement](./media/image32.png)

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image33.png)

## **Exercice 4 : Vérifier le message dans Teams.**

1.  Cliquez sur Teams dans le menu de gauche de l'application MS Teams.

![](./media/image34.png)

2.  Sélectionnez le canal **HR Experts** sous **l'HR Team**. Notez que
    le message de l'utilisateur au bot a été envoyé ici.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image35.png)

## **Exercice 5 : Publier votre copilote – Teams**

1.  Revenez à l'application Microsoft Copilot Studio. Sélectionnez le
    chatbot **HR Support Copilot**

2.  Sélectionnez Publish dans le volet gauche.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image36.png)

3.  Cliquez sur **Publish**.

![](./media/image37.png)

4.  Sélectionnez Publish dans la section **Publish latest content?**

![Gros plan d'un écran d'ordinateur Description générée
automatiquement](./media/image38.png)

5.  Le message de réussite est obtenu comme dans la capture d'écran
    ci-dessous. Cliquez sur l’ **Availability options.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image39.png)

6.  L'option **Add to Contoso** ajoute le bot à l'équipe spécifique.

7.  **Show to my team mates and shared users** fait apparaître le bot
    dans la section **Built by colleagues**

8.  **Show to everyone in the org** soumet la demande à l'administrateur
    pour que le bot soit répertorié dans la section **Built by org**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image40.png)

**Résumé:**

Dans ce laboratoire, nous avons appris à publier un message sur le canal
Teams à partir du bot.
