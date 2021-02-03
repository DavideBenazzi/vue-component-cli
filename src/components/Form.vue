<template>
      <div>
        <h2>Cerca un Pokemon</h2>
        <form action="" v-on:submit.prevent> 
            <input type="text" v-model="searchText">
            <input type="submit" value="Cerca" @click="sendSearch"> 
        </form>
      </div>
</template>

<script>
export default {
    name: "FormCustom",
    data() {
        return {
            searchText: ""
        }
    },
    methods: {
        sendSearch() {
            console.log(this.searchText)
            this.$emit('sendForm' , this.searchText);
        }
    }
}
</script>

<style>

</style>