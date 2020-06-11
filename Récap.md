# Session Révisions

Différence Abstraite Interface 


Responsabilité unique s'appuie sur abstraction et encapuslation 

Encapsulation : Séparer comportement technique de la partie métier (le client a besoin de connaitre ça uniquement)


Héritage en 2 mots : géneralisation spécialisation


# DS 5 Mai

Concepts, pas de détails de programmation.

Voir carnets de bord pour préparer DS.

5 principes :

- Responsabilité unique : Fonctionnalités propres au concept, chaque fonctionnalité, comportement, service et méthode est au bon endroit, Pour une voiture, la méthode "Avancer" ne tourne pas, ne fait pas le café. Elle se contente d'avancer, Chaque package est différent, un package qui gère le métier, l'autre les éléments graphiques. Chaque classe fait son job.
3 niveaux de responsabilité : Package, Méthode et Classe
Abstraction (On sait le quoi, mais pas le comment) encapsulation (regrouper au même endroit ce qui est relatif au même sujet), héritage et polymorhpisme permettent d'assurer la responsabilité unique.

- Ouverture / Fermeture : Principe qui dit qu'une classe système méthode doit etre ouverte aux changements et fermée aux modifications. Objectif, réduire le couplage. Permettre d'ajout des sous-classes facilement, ouverte aux extensions, aux modifications mais pas d'impact sur le reste de l'application.
On s'appuie aussi sur abstraction, encapsulation, héritage et polymorhpisme

- Principe de substituion de dzndizqn : N'importe qu'elle sous-classe peut se substiuer à une autre
Piece, qui sont des Rois, Cavaliers, Schotrupmh on s'en fou, on a bien découplé, n'importe quel type est capable de se substiuer à son type mère. Le côté client a uniquement un objet abstrait 

- Principe de ségreagtion des interfaces : Une interface sert à définir un contrat, au niveau fonctionnel, il dépend uniquement de ce genre de chose, "programmer des interfaces et pas des implémentations", conséquence : sous classe qui implémente une interface doit implémenter toutes ses méthodes. "Ne parlez qu'à vos amis", avec le DP FACADE, le controller connaît que la classe View et Modele, mais pas le reste ! Transparent, boite noire, on ne connait pas l'existance. 


- Principe d'inversion des dépendances : "Nous ne appelez pas nous vous appelerons" on verra l'année pro

Faut mettre en place tous ces DP, tout ces bons principes, UNIQUEMENT dans le cas d'un système qui est amené à évoluer ! Car ça prend plus de temps de développer de cette façon... Est-ce bien raisonnable de faire tout ça ? 


# Piliers de la POO
## 1) Abstraction
• **Dans cette application, qu’elles sont les différentes abstractions (conceptuelles) manipulées ?**
Chaque besoin est spécifié dans sa propre partie, il n'y a pas de débordement, le besoin métier est dans le model, on a la vision uniquement sur ce qu'on manipule. Les différentes abstractions :
- ChessPieceModel
- ChessView
- Toutes les interfaces en fait...

Une abstraction c'est une généralisation d'un concept, ça n'existe pas vraiment. On décrit les comportements des objets avec l'abstraction.

• **Une classe abstraite ?** 
Classe abstraite  = Factoriser du code / attributs 
Les classes abstraites ne sont pas instantiables, elles partagent des méthodes et des attributs mais leur comportement n'est pas le même dans les classes dérivées qui spécialisent les méthodes.

• **Différence classe abstraite et interface ?** 
Avec interface on définit ce que l'objet est censé faire, ce qu'elle rend, son comportement. Une classe abstraite ne sert qu'à définir du code elle ne définit pas le rôle.

• **Quelles sont celles qui sont déclarées en tant qu’abstraction (Java) et celles qui sont déclarées directement par la classe concrète qui les implémente ?** 
On a des interfaces pour toutes les abstractions dans le projet, donc pas de classes concrètes qui implémente un concept. 

 
• **A quoi sert l’interface ChessPieceModel ? Quelles auraient été les conséquences si elle n’existait pas ?**
Elle sert de base commune pour toutes les pièces, on pourra donc les manipuler toutes de la même façon. Elle définit le comportement attendu des pièces du modèle. Permet d'abstraire le type de pièce vis-à-vis du client.

Si elle n'existait pas, l'implementor ne pourra pas gérer une liste de ChessPieceModel, il devra gérer des Objects ou plusieurs listes de chaque type concret. Il y aura donc un test de type à chaque fois à faire pour vérifier l'objet Pièce associé. De plus, on n'aurait pas garanti toutes les méthodes associées et implémentées. 
 
• **Pourquoi dans l’interface ChessPieceModel la méthode qui permet de changer les coordonnées d’une pièce s’appelle-t-elle doMove() et non pas setCoord() ?**
Détail d'implémentation pour donner un nom significatif au besoin métier.
 
• **Quelle définition donneriez-vous d’une abstraction ?** 
 
 
• **Dans notre application, pouvez-vous dire que l’utilisation d’abstractions favorise l’évolutivité du code ? justifiez.**
 Oui, car à tout moment il est possible de changer une classe si le comportement ne nous plait plus, on peut créer des nouveaux types sur la hiérarchie des pions, changer le type de la grille.
 
 
 
## 2)   Encapsulation  
• **La classe ModelCoord n’a que des accesseurs (getXxx()), pourquoi pas de mutateurs (setXxx()) ?**
 Il est interdit de modifier les lignes colonnes du coordonnée, donc pas de set !
 
• **Avez-vous déclaré certaines méthodes avec le qualificateur private ? Dans quel but ?** 
Découper une méthode publique trop grosse en plusieurs méthodes private. Le but est de ne pas donner accès à une ressource à une classe qui n'en a pas besoin, pour la robustesse et le côté sécurité. La méthode private permet de ne pas dupliquer le code. Private permet de déclarer des attributs et des méthodes qui ne seront visibles et accessibles directement que depuis l'intérieur même de la classe.
 
 
• **Les classes du package view sont-elles fortement couplées entre elles ? Est-ce un pb ? pourquoi ?** 
Gros couplage, on a des compositions des implémentations, des agrégations, il y a une dépendance forte entre les classes. (La View créée la GridView, qui créée les SquareGUI)
Cela peut être dur à maintenir, étendre et réutiliser mais dans notre cas c'est normal car les autres classes sont des substitutions de la view (on sépare les tâches en isolant les responsabilités, pour substitution et réutiliser plus facilement).
 
 
• **Toutes les classes du package view sont-elles fortement couplées avec celles des autres packages ? Estce un pb ? pourquoi ? Même question pour celles du package model ?** 
Non pas fortement couplé, justement c'est volontaire, on sépare les tâches pour ne pas lier des concepts qui n'ont rien à voir. Il faut séparer clairement les choses, par exemple le côté graphique n'a rien à voir avec la partie métier. Cela permet de développer séparément les couches, d'évoluer et de maintenir plus facilement. 
 

• **Aviez-vous déclaré toutes les classes avec le qualificateur public ? était-ce indispensable ? Quel intérêt y aurait-il eut à limiter la visibilité de certaines classes au package ? D’une manière générale, quel est l’intérêt du Design Pattern Facade ?** 
Ce design permet d'implémenter un objet qui va en cacher d'autres internes qui eux vont rendre un service.
 
 
• **Avons-nous jusqu’alors respecté la phrase « Encapsulez ce qui varie » ?** 
Plutôt respecté, côté modèle ce qui varie c'est les pièces, et chacun des types de pièces sont bien isolés. Au niveau de la vue, pareil, les concepts sont bien isolés pour permettre une meilleure réutilisabilité. On peut substituer ou ajouter du contenu facilement. 
 
 
• **Quelle définition donneriez-vous de l’encapsulation ?**
Regrouper un ensemble de données et des méthodes, pour limiter les accès et contrôler. Il s'agit de protéger des données qui sont susceptibles de varier et les traitements.
 
 
• **Dans notre application, pouvez-vous dire que l’encapsulation facilite le développement du code et favorise l’évolutivité de l’application ? justifiez.** 
Comme on a bien isolé, si il y a une modification à faire, c'est très localisé et ça n'a pas d'impact sur le reste du code. Donc le code est très évolutif. 
 
 

## 3)  Héritage  
• **Avez-vous créer une classe abstraite dont dérivent toutes les implémentations de ChessPieceModel ? Dans quel but ?** 
 Factoriser le code pour toutes les pièces...
 
 
• **Vous avez créé des classes dérivées de classes concrètes (BorderPane, ImageView). Dans ce contexte, était-ce une bonne pratique ? Dans l’absolu, dans quel contexte est-ce une mauvaise pratique ?** 
Cela a un sens dans notre usage, car on s'appuie sur un comportement initial pour le compléter. Cependant, étendre une classe de cette façon pour ajouter ou changer du comportement est interdit, car le comportement spécialisé ne peut pas être toujours généralisé. (ex : chien "ramener la balle" par généralisable à tous les "animaux")
 
 
• **Dans notre application, pouvez-vous dire que l’héritage accélère le développement du code, garanti la maintenabilité du programme et favorise l’évolutivité de l’application ? justifiez.**
Très maintenable car on a juste a changer la classe mère pour appliquer les modifications partout, 
 

## 4) Polymorphisme
• **Dans la classe GridView pourquoi utiliser 1 fabrique (square = GuiFactory.createSquare(col, ligne)) ? Quelles conséquences si on avait écrit square = new BorderPane() ?** 
Si plusieurs classes ont besoin de créer un square, on aurait eu une duplication de code, avec une factory une seule modification. De plus, on peut traiter n'importe quel type facilement, cela permet de **découpler** le client des classes d'implémentation. "Programmer des abstractions et non pas des implémentations"
 
 
• **Relevez toutes les utilisations du polymorphisme dans l’ensemble de l’application.** 
On va pouvoir traiter des pions de manière générique, on déclare en tant que ChessPieceModel, toutes les méthodes sont vraies sur les pièces, donc chaque type pourra gérer son implémentation. 
 Egalement, des pane pour les cases, qui pourraient être des SquareGUI ou des cases 3D, alvéolées, etc..
 Pareil pour les imagesView...
 
• **Voyez-vous une corrélation entre abstraction et polymorphisme ? justifiez.** 
 Indissociable 
 
 
• **Dans notre application, pouvez-vous dire que l’usage du polymorphisme favorise l’évolutivité de l’application ? justifiez.** 
Pour ajouter de nouveaux types de pièces c'est facile, juste à implémenter l'interface. 
 

# Principes de la POO
## 1) Principe de responsabilité unique (SRP)
**Définition**
« A class should have one reason to change. » Une classe ne doit posséder qu’une et une seule responsabilité, et réciproquement, une responsabilité ne doit pas être partagée par plusieurs classes. 
**En quoi notre application respecte-t-elle le Principe SRP ?**  

• **Pourquoi la méthode isAlgoMoveOk() du ChessImplementor ne vérifie-elle pas directement que le déplacement est légal en testant par exemple le type de PieceModel  et demande à l’instance de PieceModel qui se trouve aux coordonnées « initCoord » de lui donner la réponse ? En d’autres termes, qu’est-ce qui justifie l’existence des classes qui implémentent PieceModel ?** 
Justement, partage des responsabilités et délégation. Il faut éviter les objets "dieu", il faut séparer les tâches. 
 
• **Pourquoi l’objet ChessModel utilise-il un objet ChessImplementor pour discuter avec les PieceModel au lieu de le faire elle-même ?**
 
 
• **L’encapsulation garantit-elle le principe SRP ? Illustrez.** 
 Evidemment car la responsabilité est partagée
 
• **L’architecture MVC garantit-elle ce principe ? Illustrez.** 
Oui car tout est bien séparé 
 
• **Existe-il des classes dans l’application qui semblent avoir plusieurs responsabilités ? Illustrez.**
Au niveau du contrôleur, il a un peu un double rôle. 

## 2) Principe d’ouverture fermeture (OCP)

**Définition** 
« Classes, methods should be open for extension, but closed for modifications. » Une classe, une méthode, un module, un système doivent pouvoir être étendus, supporter différentes implémentations (Open for extension) sans pour cela devoir être modifiés (closed for modification). 
**En quoi notre application respecte-t-elle le Principe OCP ?**

• **L’encapsulation garantit-elle ce principe ? Illustrez.** 
 Comme chaque module est isolé, grâce à l’encapsulation, les modifs sont très isolées.
 
 
• **L’architecture MVC garantit-elle ce principe ? Illustrez.**
 Pareil
 
 
• **Le polymorphisme garantit-il ce principe ? Illustrez.** 
Oui car ajouter de nouvelles classes n'a pas d'impact sur le client. 
 
 
• **Pouvons-nous dire que notre application est « Ouverte aux changements et Fermée aux modification » ?** 
Oui, car encapsulation, héritage et polymorphisme ont bien été mis en place. 
 
 

## 3) Principe de Substitution de Liskov (LSP) ?

**Définition** 
« Subtypes must be substituable for their base types. » Les sous classes doivent pouvoir être substituées à leur classe de base sans altérer le comportement de ses clients. Dit autrement, un client de la classe de base doit pouvoir continuer de fonctionner correctement si une instance de classe dérivée de la classe de base lui est fournie à la place. 
**En quoi notre application respecte-t-elle le Principe LSP ?**  
Polymorphisme

## **4) Principe de Ségrégation des Interfaces (SIP) ?**

Définition 
« Clients should not be forced to depend on methods that they do not use. » Le but de ce principe est d’utiliser les interfaces pour définir des contrats, des ensembles de fonctionnalités répondant à un besoin fonctionnel. Il en découle une réduction du couplage, les clients dépendant uniquement des services qu’ils utilisent. En conséquence, toute classe implémentant une interface doit implémenter chacune de ses fonctionnalités.  
  **En quoi notre application respecte-t-elle le Principe SIP ?**  
Interfaces pour définir les contrats, peu de couplage, que des objets polymorphes, façades sur model et view pour découper des sous-système. 
 

## **5) Principe d’Inversion de Dépendances (DIP) ?**
**Définition** 
« High level modules should not depend on low level modules. Both should depend on abstractions. » « Abstractions should not depend on details. Details should depend on abstractions. » Les entités logicielles de haut niveau ne doivent pas dépendre des entités logicielles de bas niveau. Chacune doit dépendre d’abstractions. Ce principe est illustré par le principe dit d’Hollywood « Ne nous appelez pas, nous vous appellerons ». Mais pourquoi ? En règle générale les modules de haut niveau contiennent le cœur – business – des applications. Lorsque ces modules dépendent de modules de plus bas niveau, les modifications effectuées dans les modules « bas niveau » peuvent avoir des répercussions sur les modules « haut niveau » et les « forcer » à appliquer des changements, ce qui les rendrait incompatibles avec toute velléité de réutilisation. Donc pour découpler les dépendances entre objets/systèmes (les rendre indépendant), il faut toujours travailler avec des abstractions. 
**En quoi notre application respecte-t-elle le Principe DIP ?**  
 
 
 
 
 

## 6) Bonnes pratiques

• **A quoi servent les commentaires ?**   

# Et pour finir, tout cela était-il bien raisonnable ?

## 1) Conclusion

• **Avez-vous dû faire des tests de non-régression lors du développement de la 3ème itération ? si oui pourquoi, si non pourquoi ?** 
 
 
 
• **Pouvons-nous dire de notre application que c’est un logiciel de qualité ?** 
 
 
 
 

## 2) Tolérance au changement et productivité

**Principe YAGNI** 
Nous l’avons vu, la conception objet et le respect de principes simples permettent de rendre un logiciel plus souple, plus évolutif, avec des composants réutilisables.  Néanmoins, cela nécessite un niveau d’abstraction élevé qui n’est pas toujours utile. En effet, un autre principe tend à s’opposer à l’application systématique des principes SOLID : le YAGNI (« You Ain’t Gonna Need It »). Pourquoi mettre en place tout un système de tolérance au changement dans un système statique, avec peu de dépendances externes ? Le logiciel sera effectivement extrêmement robuste envers des événements qui finalement n’auront pas lieu, ou avec un impact minime. L’investissement effectué s’avère peu productif, avec un retour sur investissement négatif. La raison, le pragmatisme et l’expérience vont vous permettre d’arbitrer sur une conception plus ou moins abstraite, plus ou moins tolérante au changement. Un module commun à plusieurs applications sera nécessairement plus abstrait afin de réduire le couplage. Des composants internes à une application ne nécessiteront pas le même effort. Inutile de rendre toutes les créations d’objets indépendantes des implémentations sous peine d’avoir plus d’interfaces et de factories que de classes concrètes.  Sauf à savoir dès le départ que votre application va évoluer, vous pouvez envisager de commencer une implémentation sans mettre en œuvre l’ensemble des principes SOLID et d’y avoir recours quand la nécessité s’en fait sentir (ajout d’un cas particulier, d’une condition, d’une nouvelle implémentation, etc.). Vous gagnerez ainsi en productivité sans pour autant sacrifier la qualité de l’application 
 
**Indicateur pour le refactoring** 
L’apparition de conditions sur le type d’une classe doivent vous alerter et nécessitent de réfléchir à un éventuel refactoring. Un module majoritairement utilisé par d’autres devra avoir un niveau d’abstraction important. Inversement, un module qui n’est utilisé par aucun autre, n’aura aucun intérêt à être abstrait.