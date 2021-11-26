<template>
  <div id="app">

<!--     <Quest
      :a="'Pergunta 1'"
      :b="'Pergunta 2'"
      :c="'Pergunta 3'"
      :d="'Pergunta 4'"
      :correct="'Pergunta 1'"
    /> -->
    <Imc/>
  </div>
</template>

<script>
/* import Quest from "./components/Quest.vue"; */
import Imc from "./components/imc/Imc.vue";

export default {
  name: "App",
  components: {
    Imc,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
