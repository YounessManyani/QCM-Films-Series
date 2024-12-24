
# Quiz App

Ce projet est une application web de quiz sous forme de QCM, où l'utilisateur peut répondre à chaque question et obtenir son score à la fin.

## Fonctionnalités

- **Interface utilisateur responsive** : Adaptée à tous les types d'appareils.
- **Questions dynamiques** : Les questions sont chargées à partir d'un fichier JSON et présentées une à une.
- **Score en temps réel** : Le score est calculé et affiché à la fin du quiz.

## Technologies Utilisées

- **Vue.js 3**
- **TypeScript**
- **CSS pur**

## Structure du Projet

```
/my-quiz-app
|-- /src
|   |-- /components
|   |   |-- Answer.vue
|   |   |-- Progress.vue
|   |   |-- Question.vue
|   |   |-- Quiz.vue
|   |   |-- Recap.vue
|   |-- /assets
|   |-- App.vue
|   |-- main.ts
|-- quiz.json
|-- index.html
|-- package.json
|-- tsconfig.json
```

## Installation

Pour lancer ce projet localement, suivez les étapes suivantes :

```bash
git clone https://yourrepository.com/my-quiz-app.git
cd my-quiz-app
npm install
npm run dev
```

