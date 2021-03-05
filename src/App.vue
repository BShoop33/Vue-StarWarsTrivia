<template>
  <div id="app">
    <div class="header-container">
      <div class="logo-container">
        <img class="triviaLogo" src="StarWarsTrivia.png" alt="starwars logo" />
        <button class="hideButton">Hide All</button>
      </div>
      <div class="difficultyFilterContainer">
        <button class="easyButton">Easy</button>
        <button class="mediumButton">Medium</button>
        <button class="hardButton">Hard</button>
        <button class="showAllButton">Show All</button>
      </div>
    </div>

    <triviaCards />
  </div>
</template>

<script>
import triviaCards from "./components/triviaCards.vue";

export default {
  components: { triviaCards },
};
</script>

<style>
body {
  background-image: url("https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.hdwallpaper.nu%2Fwp-content%2Fuploads%2F2017%2F04%2Fstar_wars-23.jpg&f=1&nofb=1");
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
  border-color: #4cade6;
  border-style: solid;
}

.triviaLogo {
  width: 35em;
  margin-left: 30em;
}
</style>