<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Title msg="Hello" />
    <FormCustom />
    <Cards :cards="pokemons" />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Title from "./components/Title.vue";
import Cards from "./views/Cards.vue";
import FormCustom from "./components/Form.vue";

export default {
  name: "App",
  components: {
    // HelloWorld
    Title,
    Cards,
    FormCustom
  },
  data() {
    return {
      pokemons: [],
      count: 0,
    }
  },
  mounted() {
    this.axios.get(`${ this.base_url }/pokemon`).then((result) => {
      //const { data: { results } } = result; //<---ECMASCRIPT6 destrutturazione equivale a result.data.results cioe' dopo posso usare direttamente results
      this.pokemons = result.data.results;
      this.count = result.data.count;
    }).catch((err) => {
      console.log(err)
    });
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
