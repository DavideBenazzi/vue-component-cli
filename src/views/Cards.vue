<template>
  <div class="cards">
      <Card v-for="(card , index) in cards" :key="index" :name="card.name" :url="card.url" />
  </div>
</template>

<script>
import Card from "../components/Card.vue";
export default {
    name: "Cards",
    components: {
        Card
    },
    props: ["cards"],
     created() {
        console.log(this.cards);
    }
}
</script>
   
<style>

</style>