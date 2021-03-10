<template>
  <div id="app">
    <div class="header-container">
      <div class="logo-container">
        <img class="triviaLogo" src="StarWarsTrivia.png" alt="starwars logo" />
        <button class="hideButton" @click="hideAll">Hide All</button>
      </div>

      <div class="difficultyFilterContainer">
        <button
          class="easyButton"
          @click="
            hideAll();
            easyDifficulty();
          "
        >
          Easy
        </button>
        <button
          class="mediumButton"
          @click="
            hideAll();
            mediumDifficulty();
          "
        >
          Medium
        </button>
        <button
          class="hardButton"
          @click="
            hideAll();
            hardDifficulty();
          "
        >
          Hard
        </button>
        <button
          class="showAllButton"
          @click="
            hideAll();
            showAll();
          "
        >
          Show All
        </button>
      </div>
    </div>

    <!-- Iterates over the triviaData array to create separate cards for each object id in that array -->
    <div class="triviaCards">
      <div v-for="card in displayedTrivia" :key="card.id">
        <triviaCards :card="card" @toggle="handleToggle" />
      </div>
    </div>
  </div>
</template>

<script>
import { triviaData } from "./components/trivia.js";
import triviaCards from "./components/triviaCards.vue";

export default {
  components: { triviaCards },

  data() {
    return {
      //creates a copy of the triviaData imported from trivia.js
      triviaData: [...triviaData],
      //initializes the difficulty variable with a blank value.
      difficulty: "",
    };
  },

  methods: {
    /*when invoked, switches the value of card.AnswerShown from true to false or false to true
    depending on the card.AnswerShown initial value.*/
    handleToggle(card) {
      card.answerShown = !card.answerShown;
    },
    /*when invoked, switches the value of card.AnswerShown from true to false or false to true
    depending on the card.AnswerShown initial value.*/
    hideAll() {
      this.triviaData.forEach((card) => (card.answerShown = false));
    },
    //changes state of the difficulty value to easy.
    easyDifficulty() {
      this.difficulty = "easy";
    },
    //changes state of the difficulty value to medium.
    mediumDifficulty() {
      this.difficulty = "medium";
    },
    //changes state of the difficulty value to hard.
    hardDifficulty() {
      this.difficulty = "hard";
    },
    //changes state of the difficulty value to blank.
    showAll() {
      this.difficulty = "";
    },
  },

  computed: {
    /*performs the card difficulty level evalutation. If no difficulty level is selected or if
    the Show All button is clicked, the difficulty filter is blank so all cards are rendered. If
    any difficulty button is clicked, only cards with that difficulty value are rendered.*/
    displayedTrivia() {
      if (this.difficulty === "") {
        return this.triviaData;
      } else {
        return this.triviaData.filter(
          (card) => card.difficulty === this.difficulty
        );
      }
    },
  },
};
</script>

<style>
body {
  background-image: url("https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.hdwallpaper.nu%2Fwp-content%2Fuploads%2F2017%2F04%2Fstar_wars-23.jpg&f=1&nofb=1");
}

.cardsContainer {
  display: flex;
  flex-flow: row;
  flex-wrap: wrap;
  justify-content: space-around;
}

.difficultyFilterContainer {
  display: flex;
  margin-left: 2em;
}

.easyButton {
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
  font-size: 16pt;
  height: 4em;
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
}

.hardButton {
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
  font-size: 16pt;
  height: 4em;
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
}

.header-container {
  display: flex;
  justify-content: center;
}

.hideButton {
  align-self: center;
  background-color: #ffde06;
  border: 5px;
  border-color: red;
  border-style: solid;
  font-size: 16pt;
  height: 3em;
  margin-left: 21.5em;
  width: 8em;
}

.logo-container {
  align-items: center;
  display: flex;
  flex-flow: column;
  justify-content: center;
}

.mediumButton {
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
  font-size: 16pt;
  height: 4em;
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
}

.showAllButton {
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
  font-size: 16pt;
  height: 4em;
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
}

.triviaCards {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-around;
}

.triviaLogo {
  margin-left: 30em;
  width: 35em;
}
</style>