<template>
      <div>
        <h2>{{ msg }}</h2>
        <form action="" v-on:submit.prevent> 
            <BaseInput 
                type="text" 
                placeholder="Inserisci un nome" 
                id="searchPokemon" 
                name="name"  
                :value="searchText"
                @input="searchtext = $event"
            />
            <BaseInput 
                type="submit" 
                id="submitPokemon" 
                name="submit"  
                value="Cerca"
                @click="sendSearch"
            />
        </form>
      </div>
</template>

<script>
import BaseInput from "./BaseInput.vue";

export default {
    name: "FormCustom",
    props: ["msg"],
    components: {
        BaseInput
    },
    data() {
        return {
            searchText: ""
        }
    },
    methods: {
        sendSearch() {
            this.$emit('sendForm' , this.searchText);
        }
    }
}
</script>

<style>

</style>