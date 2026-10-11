<script setup>
import { ref } from "vue"

const indexQuestion = ref(0)
const score = ref(0)
const reponseChoisie = ref(null)
const termine = ref(false)
const progression = ref(0)

const questions = [
  {
    texte: "Quel animal voyez-vous sur cette image ?",
    image: "chat.jpg",
    choix: ["Chat", "Chien", "Lapin"],
    bonneReponse: 0,
    descriptionImage: "Un chat"
  },

  {
    texte: "Quel animal est représenté sur cette image ?",
    image: "lion.jpg",
    choix: ["Tigre", "Lion", "Loup"],
    bonneReponse: 1,
    descriptionImage: "Un lion"
  },

  {
    texte: "Quel animal voyez-vous ?",
    image: "elephant.jpg",
    choix: ["Girafe", "Éléphant", "Zèbre"],
    bonneReponse: 1,
    descriptionImage: "Un éléphant"
  },

  {
    texte: "Quel animal est représenté ?",
    image: "pappillon.jpg",
    choix: ["Pappillon", "Abeille", "Mouche"],
    bonneReponse: 0,
    descriptionImage: "Un papillon"
  },

  {
    texte: "Quel animal voyez-vous sur cette image ?",
    image: "dauphin.jpg",
    choix: ["Requin", "Baleine", "Dauphin"],
    bonneReponse: 2,
    descriptionImage: "Un dauphin"
  }
]
const nombreQuestions = questions.length

function repondre(index) {

  if (reponseChoisie.value !== null) {
    return
  }

  reponseChoisie.value = index

  if (index === questions[indexQuestion.value].bonneReponse) {
    score.value++
  }
  progression.value++
}

function questionSuivante() {
  indexQuestion.value++
  reponseChoisie.value = null
}

function afficherResultat() {
  termine.value = true
}

function rejouer() {
  indexQuestion.value = 0
  score.value = 0
  reponseChoisie.value = null
  progression.value = 0
  termine.value = false
}
</script>

<template>
  <div>

    <div v-if="!termine">

      <h1>Quiz en images</h1>

      <p>Score : {{ score }} / {{ nombreQuestions }}</p>

      <progress
        :value="progression"
        :max="nombreQuestions"
      ></progress>

      <p>{{ progression }} / {{ nombreQuestions }} réponses</p>

      <h2>
        Question {{ indexQuestion + 1 }} sur {{ nombreQuestions }}
      </h2>

      <img
        :src="questions[indexQuestion].image"
        :alt="questions[indexQuestion].descriptionImage"
      />

      <p>{{ questions[indexQuestion].texte }}</p>

      <button
        v-for="(choix, index) in questions[indexQuestion].choix"
        :key="index"
        @click="repondre(index)"
        :disabled="reponseChoisie !== null"
      >
        {{ choix }}
      </button>

      <p v-if="reponseChoisie !== null">
        <span v-if="reponseChoisie === questions[indexQuestion].bonneReponse">
          Bonne réponse !
        </span>

        <span v-else>
          Mauvaise réponse.
        </span>
      </p>

      <button
        v-if="indexQuestion < nombreQuestions - 1 && reponseChoisie !== null"
        @click="questionSuivante"
      >
        Question suivante
      </button>

      <button
        v-if="indexQuestion === nombreQuestions - 1 && reponseChoisie !== null"
        @click="afficherResultat"
      >
        Voir le résultat
      </button>

    </div>

    <div v-else>

      <h1>Quiz terminé !</h1>

      <h2>
        Votre score : {{ score }} / {{ nombreQuestions }}
      </h2>
      
  <button @click="rejouer">
    Rejouer
  </button>
    </div>

  </div>
</template>

<style scoped>
div {
  max-width: 700px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
  background: #fdf6e3; /* fond doux */
  border-radius: 15px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

h1 {
  margin-bottom: 10px;
  font-family: "Comic Sans MS", "Poppins", sans-serif;
  color: #ff6f61;
}

h2 {
  margin-bottom: 20px;
  font-family: "Comic Sans MS", "Poppins", sans-serif;
  color: #4caf50;
}

p {
  font-size: 18px;
  color: #333;
}

progress {
  width: 100%;
  height: 25px;
  margin-bottom: 10px;
  border-radius: 12px;
  overflow: hidden;
}

progress::-webkit-progress-bar {
  background-color: #eee;
  border-radius: 12px;
}

progress::-webkit-progress-value {
  background-color: #ffcc00;
  border-radius: 12px;
}

img {
  width: 100%;
  max-width: 400px;
  height: 250px;
  object-fit: contain;
  display: block;
  margin: 20px auto;
  border: 4px solid #ffcc00;
  border-radius: 12px;
  background: #fff;
}

button {
  padding: 12px 24px;
  margin: 8px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  border-radius: 25px;
  background: linear-gradient(135deg, #ff6f61, #ffcc00);
  color: white;
  font-weight: bold;
  transition: transform 0.2s, background 0.3s;
}

button:hover:not(:disabled) {
  transform: scale(1.05);
  background: linear-gradient(135deg, #ffcc00, #ff6f61);
}

button:disabled {
  cursor: not-allowed;
  opacity: 0.6;
}

</style>
