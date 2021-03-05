<template>
  <div class="triviaCardsContainer">
    <div class="triviaCard"></div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.triviaCard {
  width: 12em;
  height: 12em;
  border: 5px;
  border-style: solid;
  border-color: green;
  background-color: #ffde06;
  margin: 2em;
  font-size: 16pt;
  padding: 0.4em;
}

.triviaCardsContainer {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>