# Atelier 04 - Améliorer le Copilot immobilier avec les capacités de la génération IA

**Durée de l’atelier** – 80 minutes

**Objectif :**

Implémentez l'utilisation d'entités, d'emplacements et de variables dans
l'application Copilot for Real Estate. Améliorez le Copilot créé pour
l'application Real Estate afin d'améliorer l'expérience client en
mettant en œuvre l'IA générative.

## Exercice 1 : Utiliser des entités pour améliorer le Copilot

Microsoft Copilot Studio utilise des entités pour comprendre l'intention
de l'utilisateur. De nombreuses entités prédéfinies sont incluses pour
les informations couramment utilisées. Vous pouvez créer des entités
personnalisées pour votre objectif spécifique.

### Tâche 1 : Afficher les entités prédéfinies

1.  Ouvrez le Copilot Studio à
    !\![https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/) !!
    et ouvrez l'agent **Real Estate Booking Service.**

2.  Sélectionnez **Settings** en haut à droite de l'écran.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image1.png)

3.  Sélectionnez l'onglet **Entities**. Vous pouvez voir une liste
    d'entités prédéfinies.

![](./media/image2.png)

### Tâche 2 : Créer l'entité de type de propriété

1.  Sélectionnez **+ Add an entity**, puis sélectionnez **+ New
    entity**.

![](./media/image3.png)

2.  Sélectionnez la vignette **Closed list**.

![](./media/image4.png)

3.  Entrez les détails ci-dessous

    - Name - !!Property Type!!

    - Enter item under List items – !!Apartment!! - Select **Add**

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image5.png)

4.  Entrer!!**Condominium** !! dans le champ **Enter item** et
    sélectionnez **Add**.

5.  Entrer!!**Duplex** !! dans le champ **Enter item** et sélectionnez
    **Add**.

6.  Entrer!!**House** !! dans le champ **Enter item** et sélectionnez
    **Add**.

![](./media/image6.png)

7.  Sélectionnez **+ Synonyms** pour **Apartment**, entrez !!**Flat**!,
    puis sélectionnez l'icône **+** et sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image7.png)

8.  Sélectionnez **+ Synonyms** pour **House**, entrez !!
    **Single-family home**!, puis sélectionnez l'icône **+** et
    sélectionnez **Done**.

9.  Sélectionnez **+ Synonyms** pour **Condominium**, entrez
    !!**Townhouse **!!, puis sélectionnez l'icône **+** et sélectionnez
    **Done**.

10. Sélectionnez **Save**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image8.png)

11. Sélectionnez **Close**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image9.png)

### Tâche 3 : Créer l'entité du nombre de chambres

1.  Sélectionnez **+ Add an entity**, puis sélectionnez **+ New
    entity**.

![](./media/image10.png)

2.  Sélectionnez la vignette **Regular expression** (Regex).

![](./media/image11.png)

3.  Entrez les détails ci-dessous et cliquez sur **Save**.

    - Name - !!**Number of Bedrooms**!!

    - Pattern - !!**\[1-5\]**!!

![Une capture d'écran d'un téléphone portable Le contenu généré par l'IA
peut être incorrect.](./media/image12.png)

4.  Sélectionnez **Close**.

![Une capture d'écran d'un téléphone Le contenu généré par l'IA peut
être incorrect.](./media/image13.png)

5.  Fermez le volet **Settings**.

![](./media/image14.png)

### Tâche 4 : Utiliser des entités

1.  Sélectionnez l'onglet **Topics**. Sélectionnez topic **Book a Real
    Estate Showing**.

![](./media/image15.png)

2.  Sélectionnez l'icône **+** au-dessus du nœud de question de
    propriété, puis sélectionnez **Ask a question**.

![](./media/image16.png)

3.  Remplissez les détails ci-dessous.

    - **Enter a message** - !! Quel type de bien souhaitez-vous voir ?!!

    - **Identify** – Sélectionner **Property Type**

    - Sélectionnez **Select options for user** et Cochez l'option
      **Display** pour toutes les valeurs de la liste.

![](./media/image17.png)

4.  Sélectionnez la variable dans **Save user response as** et entrez !!
    **PropertyType**!! pour **Variable name**

![](./media/image18.png)

5.  Sélectionnez l’icône **+** sous le nouveau nœud de question et
    sélectionnez **Ask a question**.

6.  Entrez les détails ci-dessous et cliquez sur **Save**.

    - **Enter a message** - !! De combien de chambres avez-vous besoin
      ?!!

    - **Identify -** Sélectionner **Number of Bedrooms**

    - **Save user response as -** Entrez !! Nombre de chambres !! pour
      **Variable name**

![](./media/image19.png)

## Exercice 2 : Créer des actions

Microsoft Copilot Studio peut accéder aux données dans Microsoft
Dataverse à l'aide des flux cloud Power Automate

### Tâche 1 : Créer un flux Power Automate pour récupérer une propriété

1.  Sélectionnez l'onglet **Actions** dans le menu supérieur.
    Sélectionnez **+ Add an action**.

![](./media/image20.png)

2.  Sélectionnez **+ New action** -\> **New Power Automate flow**.

![](./media/image21.png)

3.  Connectez-vous à Power Automate si vous y êtes invité.

4.  Dans le coin supérieur droit, activez l'option **New designer** si
    ce n'est pas déjà fait. Sélectionnez **Save and switch**.

![](./media/image22.png)

5.  Sélectionnez **Run a flow from Copilot** en haut à gauche de l'écran
    et entrez !!**Get property** !! comme nom de flux.

![](./media/image23.png)

6.  Sélectionnez l'étape de déclenchement, **Run a flow from Copilot**
    et sélectionnez **+ Add an input**.

![](./media/image24.png)

7.  Sélectionnez **Text**.

![](./media/image25.png)

8.  Entrez les détails ci-dessous

    - **Input** - !! Bedrooms!!

    - **Please enter your input** - !! Number of Bedrooms !!

![](./media/image26.png)

9.  Cliquez droit l sur l'icône **+** entre les deux étapes du flux et
    sélectionnez **Add an action**.

![](./media/image27.png)

10. Enter !!**Dataverse** !! dans le champ **Search** et sélectionnez
    **See more** pour **Microsoft Dataverse connector**.

! \[\](./media/image27.png)

11. Sélectionnez l'action **List rows**.

![](./media/image28.png)

12. Si vous êtes invité à vous authentifier, sélectionnez **OAuth** et
    sélectionnez **Sign in**. Connectez-vous à l'aide de votre ID de
    locataire si vous y êtes invité.

![](./media/image29.png)

13. Sélectionnez **Real Estate Properties** pour le nom de la table.

14. Sélectionnez **Show all** si toutes les options ne sont pas
    répertoriées automatiquement

15. Entrer !!contoso_bedrooms eq!! dans le champ **Filter Row**.

16. Utilisez **spacebar** à côté de **eq** pour vous assurer que vous
    ajoutez la valeur après un espace. Utilisez **Dynamic content** pour
    sélectionner le paramètre **Bedrooms** à coucher, puis **Add**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image30.png)

17. Sélectionnez **Respond to Copilot** et sélectionnez **+ Add an
    output**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image31.png)

18. Sélectionnez **Text**.

19. Entrez les détails ci-dessous

    - **Enter a name** - !!PropertyId!!

    - **Enter a value to respond with** - sélectionnez **Insert
      Expression** et entrez l'expression suivante :
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_realestatepropertyid'\]!!

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image32.png)

20. Sélectionnez **Add**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image33.png)

21. De !\![https://make.powerapps.com](https://make.powerapps.com/)!,
    ouvrez la table **Real Estate Property**. Accédez à sa colonne, Nom
    de la propriété (il peut s'agir d'une propriété immobilière ou
    légèrement différent lorsqu'il est créé à l'aide de Copilot) -\>
    Edit Column -\> Advanced options. Recherchez la valeur du **Logical
    name**. Il devrait s'agir de quelque chose de similaire à
    **contoso_newcolumn**. Il se peut aussi qu'il soit légèrement
    différent. Enregistrez la partie qui s'y trouve après **contoso\_**
    localement. Si le nom logique est **contoso_newcolumn**, conservez
    une note de **newcolumn** pour l'utiliser à l'étape suivante.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image34.png)

22. De retour dans la page du flux Power Automate, sélectionnez **+ Add
    an output**.

23. Sélectionnez **Text**.

    - **Enter a name** - !!PropertyName!!

    - **Enter a value to respond with** - select **Insert
      Expression** and enter the following expression:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]!!

Remplacez **propertyname** dans **contoso_propertyname** dans
l'expression ci-dessus, par la valeur enregistrée à l'étape précédente
(**newcolumn**).

Ce remplacement de valeur doit être effectué car le nom logique de cette
colonne n'est pas une valeur standard et nous devrons vérifier et mettre
à jour en fonction de la valeur de la table. :::

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image35.png)

24. Sélectionnez **Settings**. Assurez-vous que **Asynchronous
    Response** est définie sur **Off**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image36.png)

25. Sélectionnez **Save draft**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image37.png)

26. Une fois enregistré, sélectionnez **Publish**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image38.png)

27. Fermez l'onglet Power Automate.

### Tâche 2 : Ajouter une action Copilot pour récupérer une propriété

1.  De retour sur la page Copilot Studio, sélectionnez **Refresh**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image39.png)

2.  Sélectionnez le flux **Get Property**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image40.png)

3.  Sélectionnez **Add action**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image41.png)

4.  Sélectionnez l'onglet **Topics**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image42.png)

5.  Sélectionnez la rubrique **Book a Real Estate Showing**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image43.png)

6.  Sélectionnez l’icône **+** sous la **question De combien de chambres
    avez-vous besoin ? (How many bedrooms do you need question?)** et
    sélectionnez **Add an action**. Sélectionnez le flux **Get
    Proprerty**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image44.png)

7.  Sélectionnez la **variable NumberofBedrooms** pour le paramètre
    **Bedrooms**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image45.png)

8.  Sélectionnez les **trois points** dans la section Which **property
    do you want to see ?** question et sélectionnez **Delete**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image46.png)

9.  Sélectionnez l’**icône +** sous le nœud d'action et sélectionnez
    **Send a message**.

10. Remplissez les détails ci-dessous

    - **Enter a message** - enter !!Property!!

    - Sélectionnez l’icône **Insert variable**, puis la variable
      **PropertyName**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image47.png)

11. Sélectionnez **Save**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image48.png)

12. Une fois enregistré, sélectionnez **Publish,** puis Publier.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image49.png)

13. Cliquez sur **Publish** dans la boîte de dialogue de confirmation de
    publication.

![Un gros plan d'un fond blanc Le contenu généré par l'IA peut être
incorrect.](./media/image50.png)

### Tâche 3 : Créer un flux Power Automate pour effectuer une réservation

1.  Sélectionnez l’onglet **Actions**, puis sélectionnez **+ Add an
    action**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image51.png)

2.  Sélectionnez **+ New action** -\> **New Power Automate flow**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image52.png)

3.  Sélectionnez **Run a flow from Copilot** en haut à gauche de l'écran
    et entrez !! **Booking Request**!! comme nom de flux.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image53.png)

4.  Sélectionnez l'étape de déclenchement **Run a flow from Copilot** et
    sélectionnez **+ Add an input -\> Text**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image54.png)

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image55.png)

5.  Entrez les détails ci-dessous

    - Input - !!**PropertyId**!!

    - Veuillez saisir votre Input **-** !!**Property**!!

    - 

6.  Sélectionnez **+ Add an input -\> Text**

    - Input-!!**Viewer Name**!!

    - Veuillez entrer votre Input **-** !!**Viewer Name**!!

7.  Sélectionnez **+ Add an input -\> Text**.

    - Input-!!**ViewerEmail**!!

    - Veuillez entrer votre Input **-** !!**ViewerEmail**!!

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image56.png)

8.  Sélectionnez l’icône **+** entre les deux étapes du flux, puis
    sélectionnez **Add an action**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image57.png)

9.  Entrer !!**Dataverse**!! dans le champ **Search** et sélectionnez
    **See more** pour le connecteur Dataverse.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image58.png)

10. Sélectionnez l'action **Add a new row**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image59.png)

11. Sélectionnez **Booking Requests** pour le nom de la table.

12. Entrer !!**Copilot booking**!! dans le champ **Booking Name**.

13. Sélectionnez **Show all**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image60.png)

14. Entrer !!contoso_bookingrequests() !! dans le champ **Property (Real
    Estate Properties),** placez le curseur entre crochets et utilisez
    Contenu **dynamique**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image61.png)

15. Sélectionnez le paramètre **PropertyId**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image62.png)

16. Utilisez **Dynamic content** pour sélectionner le paramètre
    **ViewerName** pour le champ **Viewer Name**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image63.png)

17. Utilisez **Dynamic content** pour sélectionner le paramètre
    **ViewerEmail** pour le champ **Viewer E-mail**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image64.png)

18. Les paramètres seront désormais similaires à ceux de la capture
    d'écran ci-dessous.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image65.png)

19. Sélectionnez l’action **Respond to Copilot**. Sélectionnez
    **Settings** et assurez-vous que **Asynchronous Response** est
    définie sur **Off**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image66.png)

20. Sélectionnez **Save draft**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image67.png)

21. Une fois enregistré, sélectionnez **Publish**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image68.png)

22. Fermez l'onglet Power Automate.

### Tâche 4 : Ajouter une action Copilot pour la création d'une demande de réservation

1.  De retour sur la page Copilot Studio, sélectionnez **Refresh**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image69.png)

2.  Sélectionnez le flux de **Booking Request**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image70.png)

3.  Sélectionnez **Add action**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image71.png)

4.  Sélectionnez **Next** dans la section Vérifier les Inputs et les
    sorties .

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image72.png)

5.  Sélectionnez **Finish** dans l’écran **Review and finish**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image73.png)

6.  Sélectionnez l'onglet **Topics**, puis la rubrique **Book a Real
    Estate Showing**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image74.png)

7.  Sélectionnez l'icône **+** sous la page À **quelle date et heure
    souhaitez-vous voir la propriété ? (What date and time do you want
    to see the property?)** et sélectionnez **Add an action**.

8.  Sélectionnez le flux **Booking Request**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image75.png)

9.  Sélectionnez la variable **PropertyId** pour le paramètre d'Input
    **PropertyId**.

Sélectionnez la variable **Name** pour le paramètre d'Input
**ViewerName**.

Sélectionnez la variable **EmailAddress** pour le paramètre d'Input
**ViewerEmail**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image76.png)

10. Sélectionnez l’icône **+** sous le nœud d'action. Sélectionnez
    **Topic management**, puis Accéder **Go to another topic,** puis
    Mettre **End of conversation**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image77.png)

11. Sélectionnez **Save**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image78.png)

12. Une fois enregistré, sélectionnez **Publish,** puis **Publish** à
    nouveau dans la boîte de dialogue de confirmation.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image79.png)

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image80.png)

## Exercice 3 : Tester l'agent

### Tâche 1 : Tester l'agent et faire une demande de réservation

1.  Sélectionnez le bouton **Test** en haut à droite de l'écran pour
    ouvrir le panneau de test. Sélectionnez les **trois points** en haut
    du panneau de test en haut à droite de l'écran. Sélectionnez **Track
    between topics**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image81.png)

2.  Lorsque le message **Conversation Start** s'affiche, votre agent
    démarre une conversation.

3.  En réponse, entrez une phrase de déclenchement pour la rubrique que
    vous avez créée :

!!I want to book a real estate showing!!

4.  Le Copilot répond par la question "**What is your name?**".

5.  Entrez votre nom.

![Une capture d'écran d'un chat Le contenu généré par l'IA peut être
incorrect.](./media/image82.png)

6.  Entrez ensuite votre adresse e-mail lorsqu'il vous invite à
    l'appeler. Une fois que vous avez entré les détails, une question
    demandant si les informations sont correctes et des options pour
    sélectionner **Yes** ou **No** est demandée. Sélectionnez **Yes**.

![Une capture d'écran d'un chat Le contenu généré par l'IA peut être
incorrect.](./media/image83.png)

7.  Sélectionnez **House** pour l'invite du type de propriété.

8.  Entrer !!**2** !! pour l’invite, nombre de chambres.

![Une capture d'écran d'un chat Le contenu généré par l'IA peut être
incorrect.](./media/image84.png)

9.  Entrer !! Tomorrow 2 :00 PM!! à l’invite What **date and time do you
    want to see the property?**.

10. Sélectionnez **Yes** à l'invite **Did that answer your question?**

11. Sélectionnez n'importe quelle note.

12. Sélectionnez **No** à l'invite **Can I help with anything else?**

![Une capture d'écran d'un chat Le contenu généré par l'IA peut être
incorrect.](./media/image85.png)

### Tâche 2 : Vérifier la demande de réservation

1.  Accédez au portail Power Apps à l'adresse
    !\![**https://make.powerapps.com**](https://make.powerapps.com/)!.

2.  Dans le volet de navigation de gauche, sélectionnez **Tables,** puis
    **Custom**.

3.  Sélectionnez le tableau **Booking Request**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image86.png)

4.  Sous **Booking Request columns and data**, vous devriez voir qu'une
    demande de réservation Copilot est maintenant créée.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image87.png)

## Exercice 4 : Configurer l'IA générative

Dans cet exercice, vous allez apprendre à utiliser la fonctionnalité de
réponses génératives pour améliorer les réponses de votre Copilot.

### Tâche 1 : Activer l'IA générative

1.  Connectez-vous au Copilot Studio en utilisant vos identifiants de
    locataire à l'adresse
    !\![https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/) !!
    si vous n'êtes pas déjà connecté.

2.  Sélectionnez l'agent **Real Estate Booking Service**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image88.png)

3.  Sélectionnez **Settings** en haut à droite de l'écran.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image89.png)

4.  Sélectionnez l'onglet **Generative AI**.

Sélectionnez **Generative(preview)** sous **How should your copilot
decide how to respond**.

Sélectionnez **Medium** pour **How strict should the content moderation
be?**.

Sélectionnez **Save**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image90.png)

5.  **Close** le volet Paramètres (Settings).

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image91.png)

### Tâche 2 : Activer les connaissances (Knowledge)

1.  Cliquez sur l'onglet **Overview**.

2.  Vérifiez que les connaissances (Knowledge) générales sont activées
    dans la section Connaissances (Knowledge).

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image92.png)

### Tâche 3 : Ajouter des connaissances (Add Knowledge) à partir d'un site Web

1.  Sélectionnez **+ Add knowledge**  dans la section **Knowledge**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image93.png)

2.  Sélectionnez la vignette **Public websites**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image94.png)

3.  Entrez le lien du site Web public
    !\!<https://create.microsoft.com/templates/real-estate>!.
    Sélectionnez **Add**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image95.png)

4.  Donnez le nom !!Real Estate Website!! dans le champ Nom, puis
    sélectionnez **Add**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image96.png)

### Tâche 4 : Ajouter des connaissances (Knowledge) à partir de Dataverse

1.  Sélectionnez l'onglet **Knowledge**. Sélectionnez **+ Add
    knowledge**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image97.png)

2.  Sélectionnez **Dataverse (preview).**

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image98.png)

3.  Sélectionnez la case **Real Estate Property** et sélectionnez
    **Next**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image99.png)

4.  Prévisualisez les données dans l'écran suivant, puis sélectionnez
    **Next**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image100.png)

5.  Vérifiez les détails et cliquez sur **Add** dans l'écran Vérifier et
    terminer.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image101.png)

### Tâche 5 : Ajouter des connaissances (Knowledge) à partir de fichiers

1.  Dans l’onglet **Knowledge**, sélectionnez **+ Add knowledge**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image102.png)

2.  Sous la section **Upload files**, sélectionnez **click to browse**
    et recherchez le fichier **SummitRealtyCaseStudy.docx** dans
    **C :\LabFiles** et sélectionnez-le.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image103.png)

3.  Sélectionnez **Add**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image104.png)

:::danger Important : Le téléchargement du fichier sera terminé et
l'indexation prendra un certain temps. Vérifiez l'état dans l'onglet
Knowledge pour vous assurer que le fichier est disponible. :::

### Tâche 6 : Utiliser les réponses génératives dans la rubrique de secours du système

1.  Sélectionnez l’onglet **Topics**, puis **System**. Sélectionnez la
    rubrique **Fallback**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image105.png)

2.  Sélectionnez les **trois points** dans le nœud de message et
    sélectionnez **Delete**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image106.png)

3.  Sélectionnez l’icône **+** sous le nœud Condition, sélectionnez
    **Advanced**, puis **Generative answers**.

![Une capture d'écran d'un écran d'ordinateur Le contenu généré par l'IA
peut être incorrect.](./media/image107.png)

4.  Sélectionnez le champ **Input**, sélectionnez **System** dans le
    volet **Select a variable**. Sélectionnez **Activity.Text** à partir
    de celui-ci.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image108.png)

5.  Sélectionnez **Edit** sous **Data sources**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image109.png)

6.  Sélectionnez **Search only selected sources**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image110.png)

7.  Sélectionnez le document **SummitRealtyCaseStudy**. Désélectionnez
    **Allow the AI to use its own general knowledge**. Sélectionnez
    **Medium** pour **Content moderation**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image111.png)

8.  Sélectionnez **Save**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image112.png)

### Tâche 7 : Configurer la sécurité

1.  Sélectionnez l'onglet **Overview**.

2.  Sélectionnez **Settings** en haut à droite de l'écran.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image113.png)

3.  Sélectionnez l’onglet **Security**, puis la vignette
    **Authentification**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image114.png)

4.  Sélectionnez S'authentifier auprès de Microsoft **(Entra ID
    authentication in Teams and Power App).**

5.  Sélectionnez **Save**

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image115.png)

6.  Sélectionnez **Save**

![Une capture d'écran d'une erreur informatique Le contenu généré par
l'IA peut être incorrect.](./media/image116.png)

7.  Sélectionnez **Close**.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image117.png)

8.  Sélectionnez l’onglet **Overview**.

9.  Sélectionnez **Publish**, puis **Publish** à nouveau dans la boîte
    de dialogue.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image118.png)

### Tâche 8 : Tester les connaissances (Knowledge) de l'agent

1.  Sélectionnez le bouton **Test** en haut à droite de l'écran pour
    ouvrir le panneau de test.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image119.png)

2.  Sélectionnez **Activity map** si ce n'est pas déjà fait.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image120.png)

3.  Sélectionnez le **bouton Actualiser** dans le panneau de test pour
    **démarrer une nouvelle conversation**.

4.  Tapez !! Qu'est-ce que le groupe Summit Realty ?!! et appuyez sur
    **envoyer**.

5.  Vous obtiendrez une réponse du fichier téléchargé comme dans la
    capture d'écran ci-dessous, car il a été ajouté en tant que source
    de connaissances (Knowledge) à rechercher dans la rubrique de
    secours.

![Une capture d'écran d'un ordinateur Le contenu généré par l'IA peut
être incorrect.](./media/image121.png)

**Résumé:**

Dans ce laboratoire, nous avons appris à

- Utiliser des entités et remplir des emplacements

- Mettre en œuvre des actions de flux

- Ajouter des connaissances (Knowledge) à l'agent

- Activer l'IA générative

 
