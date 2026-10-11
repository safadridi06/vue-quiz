# Quiz en images 

## 1. Présentation du projet

Ce projet est une application web interactive réalisée avec **Vue.js 3** et **JavaScript**.

Le quiz contient cinq questions illustrées. Pour chaque question, l'utilisateur doit identifier l'animal représenté en choisissant une réponse parmi trois propositions.

L'application calcule le score final et affiche la progression du joueur.

## 2. Technologies utilisées

- Vue.js 3
- JavaScript
- HTML5
- CSS3
- Vite

## 3. Fonctionnalités

- Affichage de cinq questions avec des images locales.
- Trois choix de réponse pour chaque question.
- Calcul automatique du score.
- Affichage d'un message après chaque réponse.
- Barre de progression indiquant le nombre de questions traitées.
- Désactivation des choix après la validation d'une réponse.
- Navigation entre les questions.
- Affichage du résultat final.
- Possibilité de recommencer le quiz.
- Interface adaptée aux ordinateurs et aux téléphones.

## 4. Installation et exécution

### Prérequis

Installer Node.js et npm.

### Installer les dépendances

```bash
npm install
```

### Lancer le projet

```bash
npm run dev
```

Ouvrir ensuite dans le navigateur l'adresse locale indiquée dans le terminal.

### Compiler le projet

```bash
npm run build
```

## 5. Structure du projet

```text
quiz-images/
├── public/
│   └── images/
│       ├── chat.jpg
│       ├── lion.jpg
│       ├── elephant.jpg
│       ├── papillon.jpg
│       └── dauphin.jpg
├── src/
│   └── App.vue
├── captures/
├── compte-rendu/
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

## 6. Tests réalisés

- Vérification des bonnes et des mauvaises réponses.
- Vérification du calcul du score.
- Vérification de la progression.
- Vérification de la désactivation des boutons après une réponse.
- Vérification de l'affichage du résultat final.
- Vérification de la réinitialisation du quiz avec le bouton « Rejouer ».
- Vérification de l'affichage sur petit écran.

## 7. Auteur

Étudiant(e) : À compléter

Module : Développement Web avec Vue.js