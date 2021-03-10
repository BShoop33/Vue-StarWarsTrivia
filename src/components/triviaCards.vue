<template>
  <div class="triviaCardsContainer">
    <div class="triviaCard">
      <div class="question">
        <h4>{{ question }}</h4>
        <div>
          <button
            v-if="card.answerShown == false"
            class="showAnswerButton"
            @click="handleClick"
          >
            Show Answer
          </button>
          <div class="difficulty">
            {{ difficulty }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["card"],

  methods: {
    handleClick() {
      this.$emit("toggle", this.card);
    },
  },

  computed: {
    question() {
      return this.card.answerShown == false
        ? this.card.question
        : this.card.answer;
    },
    difficulty() {
      return this.card.difficulty.toUpperCase();
    },
  },
};
</script>

<style scoped>
.card {
  background-color: transparent;
  border: 1px solid #f1f1f1;
  height: 200px;
  margin-top: 20px;
  perspective: 1000px;
  width: 300px;
}

.card-inner {
  height: 100%;
  position: relative;
  text-align: center;
  transform-style: preserve-3d;
  transition: transform 0.8s;
  width: 100%;
}

.difficulty {
  font-weight: 800;
  margin-top: 0.5em;
  text-align: center;
}

.flipped .card-inner {
  transform: rotateY(180deg);
}

.showAnswerButton {
  background-color: rgb(55, 243, 218);
  font-size: 18pt;
  margin-left: 1.25em;
  width: 8em;
}

.triviaCard {
  background-color: #ffde06;
  border: 5px;
  border-color: green;
  border-style: solid;
  font-size: 16pt;
  height: 11em;
  margin: 2em;
  overflow: auto;
  padding: 0.4em;
  width: 12em;
}

.triviaCardsContainer {
  display: flex;
  flex-flow: row;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>