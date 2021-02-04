<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Title msg="Hello" />
    <FormCustom msg="Cerca un Pokemon" @sendForm="searchPokemon" />
    <FormCustom msg="Cerca un tipo di Pokemon" @sendForm="searchType" />
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
  methods: {
    searchPokemon(text) {
      console.log(text);
      this.axios.get(`${ this.base_url }/pokemon/${text}`).then((result) => {
        console.log(result);
        this.pokemons = [{
          name: result.data.name,
          height: result.data.height,
          weight: result.data.weight,
        }];
      }).catch((err) => {
      console.log(err)
      });
    },
    searchType(text) {
      console.log(text);
      this.axios.get(`${ this.base_url }/type/${text}`).then((result) => {
        console.log(result);
        const results = result.data.pokemon;
        const pokemons = results.map(element => {
          return { 
            name: element.pokemon.name,
            url: element.pokemon.url
            };
        });
        this.pokemons = pokemons;
      }).catch((err) => {
      console.log(err)
      });
    }
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
