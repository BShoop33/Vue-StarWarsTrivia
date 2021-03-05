<template>
  <div class="triviaCardsContainer">
    <div class="triviaCard">
      {{ cardInfo.question }}
      <button class="showAnswerButton">Show Answer</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["cardInfo"],
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
</style>