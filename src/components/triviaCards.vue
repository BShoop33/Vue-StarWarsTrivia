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
  height: 8em;
  border: 5px;
  border-style: solid;
  border-color: green;
  background-color: #ffde06;
  margin: 2em;
  font-size: 16pt;
  padding: 0.4em;
  display: flex;
  flex-flow: column;
  justify-content: space-between;
  overflow: auto;
}

.triviaCardsContainer {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
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
.flipped .card-inner {
  transform: rotateY(180deg);
}
</style>