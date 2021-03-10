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
      triviaData: [...triviaData],
      difficulty: "",
    };
  },

  methods: {
    handleToggle(card) {
      card.answerShown = !card.answerShown;
    },
    hideAll() {
      this.triviaData.forEach((card) => (card.answerShown = false));
    },
    easyDifficulty() {
      this.difficulty = "easy";
    },
    mediumDifficulty() {
      this.difficulty = "medium";
    },
    hardDifficulty() {
      this.difficulty = "hard";
    },
    showAll() {
      this.difficulty = "";
    },
  },

  computed: {
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
.triviaCards {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-around;
}

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
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
  height: 4em;
  font-size: 16pt;
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
}

.mediumButton {
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
  height: 4em;
  font-size: 16pt;
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
}

.hardButton {
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
  height: 4em;
  font-size: 16pt;
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
}

.showAllButton {
  margin-left: 1em;
  margin-top: 0.5em;
  width: 6em;
  height: 4em;
  font-size: 16pt;
  background-color: #ffde06;
  border: 5px;
  border-color: #4cade6;
  border-style: solid;
}

.header-container {
  display: flex;
  justify-content: center;
}

.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
}

.hideButton {
  width: 8em;
  align-self: center;
  margin-left: 21.5em;
  height: 3em;
  font-size: 16pt;
  background-color: #ffde06;
  border: 5px;
  border-color: red;
  border-style: solid;
}

.triviaLogo {
  width: 35em;
  margin-left: 30em;
}
</style>