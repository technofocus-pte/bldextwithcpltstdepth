# Laboratoire 09 - Mise en œuvre d'une action d'invite pour le sujet d'un agent de génération de quiz

## Exercice 1 : Utiliser le langage naturel pour créer un agent

1.  Ouvrez un navigateur et connectez-vous à
    +++https://copilotstudio.microsoft.com/+++ et connectez-vous avec
    les informations d'identification de l'onglet Ressources si vous
    n'êtes pas déjà sur cette page.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

2.  Si vous êtes déjà sur la page Copilot Studio, cliquez sur **Home**
    pour accéder à la page d'accueil.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image2.png)

3.  Sur la page d'accueil, dans la zone de texte sous Décrivez votre
    agent pour le créer, entrez +++Je veux que vous soyez un assistant
    de questions et de réponses qui peut répondre aux questions
    courantes des utilisateurs en utilisant le contenu d'un site Web+++
    et cliquez sur **Send.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

4.  Il peut suggérer un nom pour l'agent. Acceptez-le ou indiquez votre
    propre nom.

5.  Donnez d'autres détails concernant les fonctions de l'agent comme
    ci-dessous.

+++help answer common product and support questions using the content of
a website, and help answer HR questions from an uploaded file+++

6.  Indiquez +++www.microsoft.com+++ pour le site Web qui sera utilisé
    comme source de connaissances.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image4.png)

7.  Une fois que vous avez terminé de donner des instructions, cliquez
    sur **Create** pour créer votre agent.

![Une capture d'écran d'un chat Le contenu généré par l'IA peut être
incorrect.](./media/image5.png)

8.  L'agent est créé et s'ouvre avec les détails. Faites défiler la page
    pour comprendre que l'agent a été créé avec les instructions que
    vous lui avez fournies.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image7.png)

9.  Cliquez sur l'icône Test pour tester l'agent. Entrez +++Qu'est-ce
    que Copilot Studio+++ et appuyez sur **Enter**.

![Une capture d'écran d'un téléphone Description générée
automatiquement](./media/image8.png)

10. Entrez +++What is the latest xbox model?+++

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image9.png)

Pour les deux étapes ci-dessus, vous obtiendrez une réponse de l'agent
qui sera générique puisque l'agent utilisera ses connaissances
générales.

## Exercice 2 : Créer une action d'invite pour un sujet de réponses génératives

Les actions peuvent être utilisées pour étendre les capacités des
agents. Vous pouvez ajouter plusieurs types d'actions à vos agents dans
Microsoft Copilot Studio :

- **Action de connecteur prédéfinie**, qui utilise les connecteurs Power
  Platform pour accéder aux données d'autres systèmes, tels que les
  produits d'entreprise populaires tels que Salesforce, Zendesk,
  MailChimp et GitHub.

- **Action de connecteur personnalisée**, où un connecteur peut être
  créé pour accéder aux données à partir d'API publiques ou privées.

- **Les flux de cloud Power Automate**, qui utilisent les flux de cloud
  Power Automate pour effectuer des actions, récupérer et utiliser des
  données.

- **Les invites AI Builder**, qui utilisent AI Builder et la
  compréhension du langage naturel pour cibler des scénarios et des flux
  de travail spécifiques au sein de votre entreprise.

- **Compétence Bot Framework**, qui utilise le manifeste de compétence
  qui décrit les actions que la compétence peut effectuer, y compris ses
  paramètres d'entrée et de sortie, les points de terminaison de la
  compétence et les modèles de distribution pour la compétence.

Dans cet exercice, vous allez apprendre à ajouter une invite à l'action
à un nœud de rubrique

1.  Dans votre agent, sélectionnez l'onglet **Topics**, sélectionnez **+
    Add a topic**, puis sélectionnez **From blank**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image10.png)

2.  Entrez le nom du sujet comme +++Générer des questions pour un
    quiz+++. Sélectionnez le lien hypertexte **Edit** sous Phrases dans
    le déclencheur. Un minimum de 5 phrases déclencheurs doit être saisi

Ajoutez les phrases ci-dessous une par une. Ajoutez chaque phrase et
sélectionnez l'option + pour ajouter le déclencheur.

> +++create a number of questions for a quiz based on a topic and format
> the quiz based on the instruction provided+++
>
> +++creates a quiz with a number of questions based on the topic
> provided and formats the quiz+++
>
> +++generate a quiz with a number of questions using the topic provide
> and format the questions+++
>
> +++creates questions for a quiz on a specific topic and format+++
>
> +++format a quiz by a number of questions based on the topic
> provided+++

Choisir **Save** en haut à droite pour enregistrer le sujet.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image11.png)

3.  Cliquez sur le symbole **+** sous le nœud Déclencheur. Sélectionnez
    l' option **Add an action**, puis sélectionnez l'option **New prompt
    (default AI model)** en dessous.

![Une capture d'écran d'un quiz Le contenu généré par l'IA peut être
incorrect.](./media/image12.png)

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image13.png)

4.  La boîte de dialogue Invite s'affiche et un menu volant s'affiche
    pour vous guider dans la création de votre invite. Sélectionnez
    **Next** pour parcourir le guide.

5.  Nous allons créer une invite qui générera des questions pour un
    quiz. Entrez le nom de l'invite comme +++Quiz Generator+++.

6.  Collez le contenu ci-dessous dans le champ Invite.

+++Generate a quiz with \[number\] questions to cover this \[topic\].
Decide on the format, such as multiple-choice questions or true/false
statements. Use this \[format\]. Designate the correct answer within
parentheses.+++

Développez la section **Input** et sélectionnez **+ Add input**.

**Remarque :** Faites défiler vers le bas pour voir la section Inputnsi
elle n'est pas visible.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image14.png)

7.  Sélectionnez **Text** sous l'option **Add input**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image15.png)

8.  Entrez le nom sous la forme +++number+++ et entrez des exemples de
    données tels que +++5+++. Sélectionnez **+ Add input** \> **Text**
    pour ajouter l'entrée suivante.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image16.png)

9.  Entrez le nom sous la forme +++topic+++ et entrez des exemples de
    données tels que +++Science+++, puis sélectionnez **+ Add input**
    -\> **Text** pour ajouter l'entrée suivante.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image17.png)

10. Entrez le nom sous la forme +++format+++ et entrez des exemples de
    données tels que +++bullet points+++

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image18.png)

11. Maintenant que nous avons ajouté les noms d'entrée et les données
    d'exemple. Ensuite, les entrées doivent être insérées dans l'invite.
    Dans l'invite, mettez en surbrillance **\[number\]** et sélectionnez
    **+ Add,** puis sélectionnez **number** sous In your prompt.
    L'entrée du nombre a maintenant été ajoutée à l'invite en tant
    qu'entrée.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image19.png)

> ![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
> être incorrect.](./media/image20.png)

12. Répétez les mêmes étapes pour les autres entrées.

13. Une fois que toutes les entrées sont ajoutées à l'invite, cliquez
    sur **Test prompt** et observez la réponse de l'invite.

![Une capture d'écran d'un générateur de quiz Description générée
automatiquement](./media/image21.png)

14. Sélectionnez **Save** pour enregistrer l'invite.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image22.png)

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image23.png)

15. Le nœud d'action d'invite apparaît désormais dans le canevas de
    création de la rubrique. Ensuite, les valeurs du paramètre d'entrée
    doivent être définies pour que l'agent puisse les remplir.
    Sélectionnez l' icône \>

![Une capture d'écran d'un quiz Description générée
automatiquement](./media/image24.png)

16. Sélectionnez l'onglet **System**et sélectionnez **Acivity.Text**
    comme valeur d'entrée pour l'action afin d'utiliser l'intégralité de
    la réponse de l'utilisateur et d'identifier la valeur de format.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image25.png)

17. Répétez la même opération pour les autres paramètres d'entrée de
    l'action d'invite.

![Une capture d'écran d'un quiz Description générée
automatiquement](./media/image26.png)

18. Ensuite, nous devons définir la variable de sortie de l'action
    d'invite. Cela permet de référencer la réponse en aval dans la
    rubrique. Sélectionnez l' **icône \>** et, dans l'onglet **Custom**
    , sélectionnez **Create new** nommez la variable
    +++**VarQuizQuestionsResponse+++.**

![Une capture d'écran d'un quiz Le contenu généré par l'IA peut être
incorrect.](./media/image27.png)

> ![Capture d'écran d'une fenêtre de navigateur Description générée
> automatiquement](./media/image28.png)

19. Sous l'action Inviter, sélectionnez l' **icône +** pour ajouter un
    nouveau nœud et sélectionnez **Send a message**. Sélectionnez
    l'icône de la variable **{x}**.

![Une capture d'écran d'un quiz Description générée
automatiquement](./media/image29.png)

20. Sélectionnez la variable **VarQuizQuestionsResponse.text**. Cela
    ajoutera la propriété text de la réponse à l'action d'invite au nœud
    Envoyer un message. Sélectionnez **Save** pour enregistrer votre
    sujet.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image30.png)

21. Les détails du sujet doivent ensuite être mis à jour et seront
    utilisés par votre agent pour associer le sujet à l'intention de
    l'utilisateur lorsque le mode génératif est activé. Sélectionnez
    **Details** et entrez les détails suivants.

- Display name - +++ generate questions for a quiz+++

- Description - +++ This topic creates questions for a quiz based on the
  number of questions, the topic and format provided by the user+++

Sélectionnez **Save** pour enregistrer votre sujet.

> ![Une capture d'écran d'un quiz Description générée
> automatiquement](./media/image31.png)

22. Maintenant, le paramètre du **Generative mode** doit être activé
    pour que l'agent puisse appeler la rubrique avec l'action d'invite.
    Sélectionnez **Settings** de votre agent.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image32.png)

23. Sélectionnez le paramètre **Generative AI,** puis **Generate
    (preview)** puis **Save.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image33.png)

24. Nous sommes maintenant prêts à tester l'agent.**Close** le volet
    **Settings**. Dans le volet de test, sélectionnez l'icône
    d'**refresh** . Entrez ensuite la question suivante et observez le
    résultat.

+++Create 5 questions for a quiz based on geography and format the quiz
as multi choice+++

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image34.png)

> ![Une capture d'écran d'un téléphone portable Description générée
> automatiquement](./media/image35.png)

Résumé

Dans ce laboratoire, nous avons appris à créer une action d'invite pour
un sujet en créant une invite personnalisée et en la testant.
