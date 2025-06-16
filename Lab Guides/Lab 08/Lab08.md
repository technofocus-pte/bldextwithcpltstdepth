**Laboratoire 08 - Création d'actions conversationnelles pour Microsoft
Copilot**

**Durée du laboratoire** – 20 minutes

**Objectif**

Microsoft Copilot offre des expériences prêtes à l'emploi pour interagir
avec le contenu et les ressources de l'ensemble de votre organisation.
Dans certaines situations, des réponses et une interaction avec des
systèmes externes sont nécessaires. Avec Microsoft Copilot Studio, vous
pouvez créer un sujet conversationnel qui peut être publié en tant que
plug-in Copilot. Une fois que votre administrateur de locataire a
approuvé le plug-in, il peut être ajouté aux expériences de chat M365 de
votre organisation.

Les actions seront disponibles dans Microsoft Copilot en production, si
l'organisation dispose d'une licence valide pour celles-ci.

Dans ce laboratoire, nous allons apprendre à créer une action
conversationnelle.

## **Exercice 1 : Créer une action conversationnelle**

1.  Connectez-vous à +++**https://copilotstudio.microsoft.com/**+++ à
    l'aide de vos informations d'identification de locataire si vous
    n'êtes pas déjà connecté.

2.  Sélectionnez l'environnement en tant que **Dev one** en haut à
    droite.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image1.png)

3.  Sélectionnez **Agents** dans le volet gauche.

4.  Sélectionnez **Copilot for Microsoft 365**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

5.  Sélectionnez **Actions**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

6.  Sélectionnez **Add an action**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image4.png)

7.  Sélectionnez **Conversational** dans le volet **New action**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image5.png)

8.  Indiquez le nom de l'action comme !! **Coversational action** !.
    Sélectionnez **Create**

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image6.png)

9.  Une fois prête, l'action créée s'ouvre dans le canevas de création.
    Sélectionnez **Topics**

10. S'il ne s'ouvre pas, actualisez la page et voyez si elle est
    répertoriée sous **Library -\> Coversational**

![Une capture d'écran d'une boîte de discussion Le contenu généré par
l'IA peut être incorrect.](./media/image7.png)

11. Ouvrez **Coversational action** **.**

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image8.png)

12. Nommez le sujet comme !! Holidaylist!!

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

13. Dans la description du nœud Trigger, fournissez une description
    claire de la façon dont le plug-in conversationnel peut aider
    l'utilisateur et de ce qu'il peut faire. Laissez ce sujet aider
    l'utilisateur à trouver la liste des jours fériés de l'année 2025.

Type +++ **This plugin helps to retrieve the list of holidays for the
year 2025.**+++ dans la description du nœud Trigger.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image10.png)

Cette description a un but fonctionnel et est utilisée par Microsoft
Copilot pour déterminer s'il faut appeler votre plugin ou non.

14. Ajoutez un nœud de message avec la liste des jours fériés.

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

- 

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image11.png)

15. Cliquez sur **Save** pour enregistrer le plugin.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

![Une capture d'écran d'une boîte de discussion Description générée
automatiquement](./media/image13.png)

## **Exercice 2 : Publication de votre action conversationnelle sur Microsoft Copilot**

1.  La publication de votre plug-in conversationnel crée un nouveau
    plug-in dans le registre Dataverse pour votre Tenant. Une fois
    disponible, l'administrateur de votre locataire doit approuver votre
    plug-in pour qu'il soit disponible pour les utilisateurs dans le
    catalogue de plug-ins Microsoft Copilot.

2.  Cliquez sur **Publish**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image14.png)

3.  Sélectionnez **Publish.**

![Une capture d'écran d'un programme informatique Description générée
automatiquement](./media/image15.png)

4.  Sélectionnez **Publish** dans la **Publish latest content** le
    contenu le plus récent.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image16.png)

5.  L'état de publication s'affiche à l'écran.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image17.png)

Remarque : La publication devrait se terminer rapidement. La
disponibilité réelle dans Microsoft Admin Center peut prendre jusqu'à 4
heures.

**Important :** Pour que l'administrateur puisse le référencer dans le
centre d'administration, l'entreprise devra détenir une licence Copilot
valide.

6.  Votre administrateur peut trouver l'application intégrée **Dataverse
    and Microsoft Copilot Studio** dans le Centre d'administration
    Microsoft sous **Paramètres**, puis **Intégrations à examiner et à
    approuver**.

7.  Une fois que votre administrateur de locataire a approuvé
    l'application intégrée Dataverse et Microsoft Copilot Studio,
    celle-ci doit apparaître dans la liste des plug-ins de l'utilisateur
    dans son interface utilisateur Microsoft Copilot.

**Résumé:**

Dans ce laboratoire, nous avons appris à créer une action
conversationnelle et à la publier.
