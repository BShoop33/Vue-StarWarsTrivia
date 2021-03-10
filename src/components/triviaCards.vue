<template>
  <div class="triviaCardsContainer">
    <div class="triviaCard" :class="{ flipped: card.answerShown }">
      <div class="question">
        <h4>{{ card.answerShown == false ? card.question : card.answer }}</h4>
        <div>
          <button
            v-if="card.answerShown == false"
            class="showAnswerButton"
            @click="handleClick"
          >
            Show Answer
          </button>
          <div class="difficulty">Difficulty: {{ card.difficulty }}</div>
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
};
</script>

<style scoped>
.showAnswerButton {
  font-size: 18pt;
  margin-left: 1.25em;
  width: 8em;
  background-color: rgb(55, 243, 218);
}

.triviaCard {
  width: 12em;
  height: 9em;
  border: 5px;
  border-style: solid;
  border-color: green;
  background-color: #ffde06;
  font-size: 16pt;
  padding: 0.4em;
  margin: 2em;
  overflow: auto;
  height: 11em;
}

.triviaCardsContainer {
  display: flex;
  flex-flow: row;
  flex-wrap: wrap;
  justify-content: space-around;
}

.card {
  background-color: transparent;
  width: 300px;
  height: 200px;
  border: 1px solid #f1f1f1;
  perspective: 1000px;
  margin-top: 20px;
}
.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.difficulty {
  text-align: center;
  margin-top: 0.5em;
  font-weight: 800;
}

.flipped .card-inner {
  transform: rotateY(180deg);
}
</style>