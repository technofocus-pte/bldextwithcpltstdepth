# Laboratoire 5 - Intégrer un agent à l'application Dynamics 365 Customer Service et mettre en œuvre l'escalade automatisée des incidents vers l'agent en direct

## Exercice 1 : Configurer l'espace de travail Dynamics 365 Customer Service

### Tâche 1 : Configurer l'extension Omnichannel Power Virtual Agent

1.  Ouvrez le lien
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com>+++
    et cliquez sur Obtenir maintenant dans la page Extension Omnichannel
    Power Virtual Agent.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

2.  Sélectionnez la **CustomerService Trial** sous **Select an
    environment**, cochez les cases et cliquez sur **Install**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image4.png)

3.  Dans la page des applications Dynamics 365, cliquez sur les entrées
    qui indiquent **Update available**, **select** **cochez la case**
    pour accepter les conditions et cliquez sur **Update**

Assurez-vous de le faire pour **all** entrées avec **Update available**
comme Statut.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image5.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

### Tâche 2 : Configurer les paramètres de recherche dans le centre d'administration Power Platform

1.  Connectez-vous à +++<https://admin.powerplatform.microsoft.com/>+++
    en utilisant vos coordonnées de locataire. Sélectionnez
    **Environements** -\>**CustomerService Trial**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image7.png)

2.  Sélectionnez la liste déroulante en regard de **Resource** (dans le
    volet supérieur) et sélectionnez **Dynamics 365 apps**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image8.png)

3.  Assurez-vous qu'**Omnicanal for Customer Service** est
    **Installed.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

4.  Revenez à la page **Environements -\> CustomerService Trial** dans
    le centre d'administration. Sélectionnez **Settings** dans le volet
    supérieur.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image10.png)

5.  Sélectionnez **Product** -\> **Features**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image11.png)

6.  Basculez l'option **Dataverse Search** et **Single table search**
    sur **ON.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

Faites défiler vers le bas et cliquez sur le bouton **Save** en bas à
droite.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image13.png)

## Exercice 2 : Création d'un agent

1.  Depuis la page d'accueil de Copilot Studio, !!
    https://copilotstudio.microsoft.com!!, sélectionner l'environnement
    **CustomerService Trial** en haut à droite.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image14.png)

2.  Sélectionnez **Agents** dans le volet gauche. Cliquez sur le **+ New
    Agent** pour créer un nouvel agent.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image15.png)

3.  Dans la zone de texte Tapez votre message, tapez **!! You are a
    customer service agent who helps in identifying stores nearby.**!!
    Et appuyez sur **Send**.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image16.png)

4.  Tapez le message !! **Maintain a polite tone** !! Ensuite, appuyez
    sur **send.**

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image17.png)

5.  Cliquez sur **Create**.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image18.png)

6.  L'agent créé s'ouvre avec un message indiquant que **Your agent is
    ready.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image19.png)

## Exercice 3 : Connecter le copilote à Dynamics 365 Customer Service et configurer la rubrique Escalade

### Tâche 1 : Configurer la rubrique Escalade

Nous nous concentrons ici sur la présentation du concept d'escalade vers
l'agent en direct. Nous y travaillerons donc directement sans créer
d'autres sujets.

1.  Sélectionnez l'onglet **Topics**, puis l'onglet **System**.
    Sélectionnez la rubrique **Escalate.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image20.png)

2.  Sélectionnez le nœud de message du sujet et remplacez le contenu
    existant par !! **You will be transferred to a live agent
    shortly!!**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image21.png)

3.  Cliquez sur le symbole + pour ajouter un nœud à côté du nœud
    Message.

4.  Sélectionnez **Topic management** -\> **Transfer conversation**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image22.png)

5.  Donnez un message !! Le client veut parler à un agent en direct !!
    dans le nœud Transférer la conversation.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image23.png)

6.  **Save** le sujet.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image24.png)

7.  **Publish** l'agent.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image25.png)

### Tâche 2 : Connecter le copilote à Dynamics 365 Customer Service

1.  Une fois publié, depuis la page du copilote en haut à droite,
    cliquez sur **Settings**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image26.png)

2.  Sélectionnez **Security** et **Authentication** sous Security.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image27.png)

3.  Sélectionnez l'option **No authentication**, puis cliquez sur
    **Save**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image28.png)

4.  Sélectionnez **Save** dans la boîte de dialogue de confirmation.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement](./media/image29.png)

5.  Fermez le volet **Settings** .

6.  Cliquez sur **Channels** (si les chaînes ne sont pas visibles,
    cliquez sur le +1 pour afficher l'option **Channels**)

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image30.png)

7.  Sélectionnez **Dynamics 365 Customer Service** dans le volet Centre
    d'engagement client.

![](./media/image31.png)

8.  Sur la page Service clientèle Dynamics 365, cliquez sur **Connect**.

![Une capture d'écran d'un message Description générée
automatiquement](./media/image32.png)

9.  Une fois que vous obtenez un **successfully connected** message,
    cliquez sur **Close**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image33.png)

## Exercice 4 : Créer un flux de travail et un canal dans le centre d'administration Dynamics 365

### Tâche 1 : Gérer un utilisateur dans Omnicanal pour Customer Service

1.  Connectez-vous à !! https://admin.powerplatform.microsoft.com !! à
    l'aide de vos informations d'identification de locataire admin et
    sélectionnez **Environements** dans l'onglet de gauche.
    **L’CustomerService Trial** sera répertorié ici. **Select -**le.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image34.png)

2.  Cliquez sur l’ **url value** sous **Environment URL**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image35.png)

3.  La page **Applications** s'ouvre . Sélectionnez **Customer Service
    admin center** à partir de celui-ci.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image36.png)

4.  Cela ouvre la page du **Dynamics 365 Customer Service admin center**
    .

![Une capture d'écran d'un service client Description générée
automatiquement](./media/image37.png)

5.  Dans le **Dynamics 365 Customer Service admin center**, dans le plan
    du site, sélectionnez **User management** sous groupe de **Customer
    support** .

6.  Sur la page **User management**, sélectionnez **Manage** en regard
    de **Users**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image38.png)

7.  Cliquez sur le menu déroulant en regard de **Enabled Users** et
    sélectionnez **Omnichannel Users**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image39.png)

8.  Sur la page **Omnichannel Users**, sélectionnez un **MOD
    Administrator** d'utilisateur dans la liste.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image40.png)

9.  Sur la page **MOD Administrator**, sélectionnez l'onglet
    **Omnichannel**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image41.png)

10. Assurez-vous que les valeurs sont conformes au tableau ci-dessous

\- Capacity: 100

\- Default Presence: available

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image42.png)

11. Sélectionnez **Save and close.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image43.png)

### Tâche 2 : Configurer le flux de travail 

1.  Sur la page du centre d'administration, sélectionnez **Workstreams**
    sous **Customer support** dans le volet gauche, puis sélectionnez
    l'option **+ New workstream**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image44.png)

2.  Remplissez les détails ci-dessous, faites défiler vers le bas et
    cliquez sur **Create**

- Name - +++**New Workstream**+++

- Owner – **MOD Administrator** (Selected by default)

- Type – **Messaging**

- Channel – **Chat**

> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image45.png)
>
> ![Une capture d'écran d'un chat Description générée
> automatiquement](./media/image46.png)

3.  Une fois le flux de travail créé, cliquez sur **Set up chat** pour
    configurer le canal de chat.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image47.png)

4.  Dans l'écran **Live chat setup- Channel details** , remplissez les
    détails ci-dessous et cliquez sur **Next.**

- Name - +++**Chat Channel**+++

- Language – **English -** **United States**

![Une capture d'écran d'un canal de chat Description générée
automatiquement](./media/image48.png)

5.  Dans l'écran Configuration du chat en direct – Widget de chat,
    indiquez le nom **+++Store Locator Assistant+++,** acceptez les
    autres valeurs par défaut et cliquez sur **Next**

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image49.png)

6.  Dans l' écran **Live chat setup – Behaviors**, acceptez les valeurs
    par défaut et cliquez sur **Next.**

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement](./media/image50.png)

7.  Dans l'écran **Live chat setup – User features**, désactivez les
    options **File attachment** et **Voice and video calls** et cliquez
    sur **Next.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image51.png)

8.  Dans l' écran **Live chat setup- Review and finish**, sélectionnez
    **Create channel**.

![Une capture d'écran d'une configuration de chat Description générée
automatiquement](./media/image52.png)

9.  **Copy** le widget qui apparaît dans l'écran Configuration du **Lice
    chat setup - Success** et **save**-le dans un bloc-notes pour
    l'ajouter à une page Web dans les exercices à venir. Ensuite,
    cliquez sur **Done** pour terminer la configuration.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image53.png)

### Tâche 3 : Ajouter le copilote au flux de travail

1.  De retour dans la page **New Workstream**, faites défiler vers le
    bas et cliquez sur **+ Add bot** dans la section Bot.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image54.png)

2.  Dans la liste des copilotes de l'écran Ajouter un bot, sélectionnez
    le copilote de **Store Locator Assistant** et cliquez sur
    **Connect**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image55.png)

3.  Assurez-vous que le bot est ajouté au flux de travail comme dans la
    capture d'écran ci-dessous.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image56.png)

4.  Dans le volet gauche, sélectionnez **Bots**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image57.png)

5.  Assurez-vous que le Real Estate Booking Service copilot est
    connecté.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image58.png)

## Exercice 5 : Créer une page Web et tester l'escalade vers l'agent

1.  Connectez-vous à +++https://make.powerpages.microsoft.com/+++ à
    l'aide de vos informations d'identification d'administrateur de
    locataire.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image59.png)

2.  Assurez-vous que vous êtes dans l'environement **CustomerService
    Trial**.

3.  Cliquez sur **Get started**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image60.png)

4.  Cliquez sur Skip dans la **page tell us about yourself**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image61.png)

5.  Faites défiler la page suivante vers le bas et cliquez sur l'**Start
    with a tempelate** pour commencer à créer le site avec un modèle.

![Une capture d'écran d'une page web Description générée
automatiquement](./media/image62.png)

6.  Sélectionnez un modèle et cliquez sur **Choose this template**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image63.png)

7.  Dans la zone de texte Donnez un nom à votre site, entrez le nom +++
    **Contoso Store assistant** **+++,** acceptez les autres valeurs par
    défaut et cliquez sur **Done.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image64.png)

8.  Une fois le site créé, cliquez sur **Edit site header** dans le
    titre **Company name.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image65.png)

9.  Dans le volet **Edit site header** , indiquez le titre du **Site
    title** sous la forme !! **Contoso Store assistant !**!.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image66.png)

10. Cliquez sur **Edit code** dans le coin supérieur droit de la page.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image67.png)

11. Cliquez sur **Open Visual Studio Code**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image68.png)

12. Cliquez sur **Allow**

![Un écran noir avec du texte blanc Description générée
automatiquement](./media/image69.png)

13. La page d'accueil de la page web s'ouvre dans Visual Studio Code.

![Une capture d'écran d'un programme informatique Description générée
automatiquement](./media/image70.png)

14. Faites défiler jusqu'à la fin du fichier. Ajoutez le **script**
    copié lors de la création du flux de travail, après la dernière
    ligne de ce fichier.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement](./media/image71.png)

15. Enregistrez le fichier, fermez l'onglet Visual Studio Code et
    revenez aux pages Alimentation. Cliquez sur **Sync**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image72.png)

16. Une fois la synchronisation terminée, sélectionnez **Preview-\>
    Desktop**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image73.png)

17. Votre page Web s'ouvre dans un nouvel onglet. Recherchez le **Store
    Locator Assistant** intégré à la page en bas à droite de la page
    Web. **Click** dessus.

![Une capture d'écran d'un site web Description générée
automatiquement](./media/image74.png)

18. Entrez +++talk to agent+++.

![Une capture d'écran d'un téléphone Description générée
automatiquement](./media/image75.png)

19. Sur la page d'administration du service clientèle, cliquez sur
    **Customer Service admin center** et sélectionnez l’application
    **Customer Service workspace** ![Une capture d'écran d'un ordinateur
    Description générée automatiquement](./media/image76.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image77.png)

20. Sur la page de l'espace de travail du service clientèle, vous
    recevrez une chat request. **Accept**-le.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image78.png)

21. Une fois accepté, l'écran de chat s'ouvre avec le message que nous
    avions donné dans le sujet Escalader. Nous pouvons également ajouter
    toute autre information fournie par l'utilisateur ici à l'agent en
    direct.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image79.png)

22. Simulez le chat entre l'agent en direct et le client si vous
    souhaitez voir comment il fonctionne et se termine ensuite.

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image80.png)

![Une capture d'écran d'un chat Description générée
automatiquement](./media/image81.png)

**Résumé**

Dans ce laboratoire, nous avons appris à

- Créez un agent à partir du Copilot Studio et configurez la rubrique
  Escalader.

- Publiez l'agent dans l'espace de travail Dynamics 365 et intégrez-le
  dans une page Web.

- Configurez et testez l'escalade vers un agent en direct.
