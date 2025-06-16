# Laboratoire 02 – Création d'un agent autonome pour suivre les nouveaux fichiers créés dans OneDrive

**Introduction**

OneDrive For Business d'une organisation a été créé plusieurs fichiers
et il est devenu difficile pour l'administrateur de les suivre.

**Objectif**

Créez un agent autonome pour entrer les détails du fichier nouvellement
ajouté dans l'outil de suivi des détails du fichier. Cela résout le
problème du suivi des ajouts de fichiers et le suivi des détails du
fichier aura les détails de tous les fichiers nouvellement créés.

## Exercice 1 : Mettre en place l'environnement

1.  Connectez-vous à la machine virtuelle à l'aide du mot de passe de
    l'onglet Ressources.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image1.png)

### Tâche 1 : Configurer OneDrive

1.  Ouvrez un navigateur et accédez **à +++https://office.com+++.**
    **Sign in** à l'aide des informations d'identification de l'onglet
    **Resources**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

2.  Sélectionnez **OneDrive** dans le menu de gauche.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

3.  Cliquez sur le **+ symbol** en haut à gauche et sélectionnez **Files
    upload**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image4.png)

4.  Sélectionnez le **File details** du fichier **dans C :\LabFiles** et
    sélectionnez **Open.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image5.png)

5.  Une fois le fichier téléchargé, un message de réussite s'affiche
    dans la window .

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image6.png)

6.  Cliquez sur **My files** dans le menu de gauche et vous pouvez voir
    que le nouveau fichier y est disponible.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image7.png)

### Tâche 2 : Créer un environnement de développement

1.  Connectez-vous à +++<https://admin.powerplatform.microsoft.com/>+++
    à l'aide des détails de votre locataire dans l'onglet Ressources.

2.  Sélectionnez **Environements** dans le volet de navigation de gauche
    et cliquez sur **+ New.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image8.png)

3.  Dans la window Nouvel environnement qui s'ouvre, remplissez les
    détails ci-dessous et cliquez sur **Next.**

[TABLE]

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image9.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image10.png)

4.  Dans la window **Add Dataverse**, acceptez les valeurs par défaut et
    cliquez sur **Save**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image11.png)

5.  L'environnement nouvellement créé est répertorié dans le centre
    d'administration avec son état dans le volet Environnements.

6.  Une fois que l'**status** est **ready**, l'environnement est prêt à
    l'emploi. Nous utiliserons cet environnement dans les exercices à
    venir.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

### Tâche 3 : Activer l'essai de Copilot Studio

1.  Dans un nouvel onglet, ouvrez
    **+++https://copilotstudio.microsoft.com/+++.**

2.  Connectez-vous à l'aide des **Credentials** fournies sous l'onglet
    **Resources** de votre machine virtuelle Lab.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image13.png)

3.  Une fois connecté, rendez-vous sur la page **Welcome to Microsoft
    Copilot Studio**, quittez le pays en tant que **United States** et
    cliquez sur **Get Started**.

![Une personne assise devant un ordinateur Description générée
automatiquement](./media/image14.png)

4.  Sélectionnez **Skip** dans l'écran d **Welcome**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image15.png)

## Exercice 2 : Générer et tester un agent autonome

### Tâche 1 : Créer un agent à partir de Copilot Studio

1.  Cliquez sur l'option Skip to configure dans la page de création de
    l'Agent qui s'ouvre.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image16.png)

2.  Dans le volet de création de l'agent, entrez les détails ci-dessous
    et cliquez sur **Create**.

- **Name** - +++New file tracker agent+++

- **Description** - +++This agent will update the File details tracker
  placed in the OneDrive, each time a new file is created in the
  OneDrive

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image17.png)

### Tâche 2 : Ajouter un déclencheur à l'agent

1.  Une fois l'agent créé, faites défiler vers le bas pour trouver la
    section **Trigger**. Sélectionnez **+ Add trigger.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image18.png)

2.  Dans la boîte de dialogue **Turn on generative orchestration to
    continue**, sélectionnez **Turn it on**. Nous devons avoir cette
    option définie sur on afin d'ajouter un déclencheur.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image19.png)

3.  Dans le menu Ajouter un déclencheur, sélectionnez **When a file is
    created**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image20.png)

4.  Dans l' écran **Add trigger**, sélectionnez Continue.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image21.png)

5.  Dans l'écran suivant, notez que le **Trigger name** est renseigné.
    Attendez que les **connections** à **Microsoft** **Copilot Studio**
    et **OneDrive for Entreprise** soient établies (vous obtenez une
    coche verte pour chacun de ces connecteurs).

Ensuite, cliquez sur **Next.**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image22.png)

6.  Sélectionnez les détails ci-dessous.

**Folder** – Root

**Include subfolders** – Yes

> Laissez les autres champs par défaut et sélectionnez **Create
> trigger**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image23.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image24.png)

7.  Une fois le déclencheur créé, **Time to test your trigger** message
    s'affiche . **Close**-le. Nous allons modifier un peu le flux de
    base du déclencheur pour obtenir la fonctionnalité implémentée, puis
    nous la testerons.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image25.png)

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image26.png)

### Tâche 3 : Ajouter une logique au déclencheur

1.  Sur la page **New file track agent**, faites défiler jusqu'à la
    section Déclencheur.

2.  Cliquez sur les 3 points en regard du déclencheur **When a file is
    created**, puis sélectionnez **Edit in Power Automate**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image27.png)

3.  Sélectionnez l’ icône **+** entre **When the file is created** et
    **Sends a prompt action,** puis sélectionnez **Add an action**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image28.png)

4.  Recherchez +++ajouter une ligne+++ et sélectionnez **Add a row into
    the table.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image29.png)

5.  Sélectionnez les valeurs ci-dessous pour chaque ligne et cliquez sur
    **Save**.

[TABLE]

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image30.png)

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image31.png)

6.  Le flux ressemblera maintenant à celui de la capture d'écran
    ci-dessous.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image32.png)

7.  Enregistrez le flux et **publish**

### Tâche 4 : Publier le déclencheur

1.  De retour dans Copilot Studio, sélectionnez **Settings.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image33.png)

2.  Sélectionnez **Security** -\> **Authentication** -\> **No
    authentication** puis cliquez sur **Save**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image34.png)

3.  Sélectionnez **Save** dans la boîte de dialogue de confirmation.

![Une capture d'écran d'une erreur informatique Description générée
automatiquement](./media/image35.png)

4.  Maintenant, sélectionnez **Publish** pour publier l'agent.

![](./media/image36.png)

5.  Sélectionnez **Publish** dans la boîte de dialogue de confirmation.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image37.png)

### Tâche 5 : Tester le déclencheur

1.  Revenez à **OneDrive** dans le navigateur. Cliquez sur **+** et
    sélectionnez **Word document.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image38.png)

2.  Donnez un **name** au document et sélectionnez **Create**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image39.png)

3.  Cliquez sur **Close** pour fermer l'option de confidentialité.

![Une capture d'écran d'un écran d'ordinateur Description générée
automatiquement](./media/image40.png)

4.  Ajoutez quelques fichiers supplémentaires de la même manière.

5.  Maintenant, ouvrez le details.xlsx de fichiers à partir de OneDrive
    et observez que les détails des fichiers créés sont ajoutés au
    traqueur.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image41.png)

6.  Lorsque le fichier est créé dans OneDrive, le déclencheur est appelé
    qui à son tour exécute le flux **When a file is added** et met à
    jour le suivi de l'utilisateur.

7.  Vous pouvez également vérifier les détails de l'agent autonome dans
    l'onglet Activité de Copilot Studio.

**Résumé**

Dans ce laboratoire, nous avons appris à créer, publier et tester un
agent autonome à partir de Copilot Studio.
