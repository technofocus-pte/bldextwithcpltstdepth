# **Laboratoire 06\_** **Création et déploiement d’un copilote Microsoft Copilot Studio à partir de Teams**

**Durée du laboratoire** – 30 minutes

**Objectif:**

Dans ce laboratoire vous allez installer l'application Copilot Studio
dans Microsoft Teams, créer un nouveau copilote dans une équipe et le
tester.

## **Exercice 1 : Installer l'application Copilot Studio dans Microsoft Teams**

1.  Sélectionnez le menu **Start** de la machine virtuelle, recherchez
    +++teams+++ et sélectionnez l' **application Microsoft Teams**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

2.  Connectez-vous à l'aide de vos informations d'identification à
    partir de l' onglet **Resources**.

![Capture d'écran d'une connexion Description générée
automatiquement](./media/image2.png)

3.  Cliquez sur **Appls**. Recherchez +++**Copilot Studio**+++ et
    sélectionnez **Microsoft Copilot Studio** et cliquez sur **Add**.

**Remarque :** Si vous ne parvenez pas à trouver Copilot Studio, vous
devrez rechercher et sélectionner le **Power Virtual agent** et
l'ajouter.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

![](./media/image4.png)

4.  Cliquez sur **Open**

![Une capture d'écran d'un téléphone Description générée
automatiquement](./media/image5.png)

5.  Cliquez sur **Start now**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

## **Exercice 2 : Créer un nouveau copilot dans Teams**

1.  **Sign in** à **Teams** à l'aide de vos **office 365 tenant
    credentials**

> ![Capture d'écran d'une connexion Description générée
> automatiquement](./media/image7.png)

2.  Cliquez sur **Apps**. Recherchez +++**Copilot Studio+++** et
    sélectionnez **Microsoft Copilot Studio** et cliquez sur **Add.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

![Une capture d'écran d'un téléphone Description générée
automatiquement](./media/image4.png)

**Important :** Si vous ne parvenez pas à trouver Copilot Studio, vous
devrez rechercher et sélectionner +++**Power Virtual agent**+++ et
l'ajouter.

![Une capture d'écran d'un moteur de recherche Description générée
automatiquement](./media/image8.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

3.  Cliquez sur **Start now**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

4.  Sélectionnez **Contoso** et cliquez sur **Continue**.

![Une capture d'écran d'un chatbot Description générée
automatiquement](./media/image10.png)

![Une capture d'écran d'un chatbot Description générée
automatiquement](./media/image11.png)

**Important :** Cette étape peut prendre environ 10 minutes. Si cela
prend trop de temps, fermez-le, sélectionnez Copilot Studio ou Power
Virtual Agents à partir d'Applications dans le volet gauche et refaites
l'étape 4.

5.  Dans le volet Creste un copilot, indiquez le nom du copilote sous la
    forme +++**HR** **Support Copilot**+++ et cliquez sur **Create**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

6.  Un message de réussite indiquant que **Your chatbot is provisioned**
    est obtenu.

![](./media/image13.png)

## **Exercice 3 : Créez un sujet de congés pour les employés pour les requêtes courantes sur les congés**

1.  Cliquez sur **Topics** dans le volet de gauche. Cliquez sur **+ New
    topic-\> From blank.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image14.png)

2.  **Close** le volet Phrases de déclenchement pour l'instant.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement](./media/image15.png)

3.  Cliquez sur l’icone **Details.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image16.png)

4.  Dans le volet Détails, indiquez le nom +++ **Employee time off +++**
    et la description +++ **Employee time off topic for common time-off
    queries**+++.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image17.png)

5.  **Close** le volet Détails.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image18.png)

6.  Cliquez sur **Save**.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image19.png)

7.  Cliquez sur les **Trigger phases.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image20.png)

8.  Ajoutez une phrase déclencheur, +++**I need help with time off**+++
    et cliquez sur **+.**

![](./media/image21.png)

9.  Ajoutez les phrases déclencheurs ci-dessous.

- +++**Need information on time off**+++

- +++**How many days of paid vacation do I have**+++

- +++**What are the national holidays**+++

- +++**I need extended leave**+++

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image22.png)

Fermez le volet Phrases de déclenchement.

10. Ajoutez un nœud Message et entrez le texte, +++I can help with
    questions related to time-off*+++*.

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image23.png)

11. En tant qu'employé des RH, vous savez que les questions les plus
    courantes sur les congés concernent les **paid vacation** et les
    **national holidays**. Lorsqu'un nœud de question avec des options
    de réponse utilisateur est ajouté, la rubrique obtient
    automatiquement une branche bifurquée pour chaque réponse.

12. Sélectionnez l'icône (**+**) sous le nœud de message, puis
    sélectionnez **Ask a question** pour ajouter un nœud de question à
    la rubrique. Entrez *Quelles informations recherchez-vous ?* dans la
    zone de texte **Ask a question**.

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image24.png)

13. Sous **Options for user**, ajoutez +++Paid vacation+++ et
    +++National Holidays+++ comme deux options.

> ![Capture d'écran d'un questionnaire Description générée
> automatiquement](./media/image25.png)

14. Les choix de l'utilisateur sont stockés dans une variable et la
    rubrique se divise en fonction de l'option choisie par
    l'utilisateur. Vous pouvez renommer la variable pour mieux la suivre
    dans la rubrique.

15. Sur la variable, sous **Save response as**, sélectionnez l'icône en
    forme de crayon pour modifier les propriétés de la variable.

16. Le **Variable properties** s'ouvre. Renommez la variable en
    +++TimeoffType*+++*. Fermez le volet **Variable properties** et vous
    verrez les modifications reflétées dans le canevas de création.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image26.png)

17. Ajoutez un nœud de message pour la branche Congés payés avec ce
    message à l'utilisateur : +++**For paid vacation time-off**, **go
    to** **www.contoso.com/HR/PaidTimeOff**+++ pour soumettre des
    demandes de congés.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image27.png)

18. Dans le chemin d'accès aux **National Holidays**, ajoutez un nœud de
    message avec le texte suivant :

National holidays for 2025:

- New Year’s Day: Jan 1

- Martin Luther King Jr. Day: Jan 20

- Washington’s Birthday (Presidents’ Day): Feb 17

- Memorial Day: May 26

- Juneteenth National Independence Day: June 19

- Independence Day: July 4

- Labor Day: Sep 1

- Columbus Day / Indigenous Peoples’ Day: Oct 13

- Veterans Day: Nov 11

- Thanksgiving Day: Nov 27

- Christmas Day: Dec 25

![](./media/image28.png)

19. Cliquez sur **Save**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image29.png)

![Une capture d'écran d'une fenêtre de chat Description générée
automatiquement](./media/image30.png)

## **Exercice 4 : Tester le comportement attendu du copilote**

1.  Sélectionnez l' icône **Copilot/Power Virtual Agent** en haut de
    l'écran pour lancer le canevas du copilote de test.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image31.png)

2.  Tapez **I need time off information** sur les congés dans le chat du
    copilot.

3.  Sélectionnez **Paid vacation**.

4.  Vous recevez la réponse selon notre configuration.

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image32.png)
>
> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image33.png)
>
> **Résumé:**
>
> Dans ce laboratoire, nous avons appris à ajouter l'application Copilot
> Studio à Teams et à créer un bot classique dans Teams.
