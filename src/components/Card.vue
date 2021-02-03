<template>
    <div class="card" >
        {{ name }} <br>
        {{ url }}
    </div>
</template>

<script>
export default {
    name: "Card",
    // props: [
    //     "name",
    //     "url"
    // ]
    props: {
        name: {
            type: String,
            required: true
        },
        url: {
            type: String
        }
    }
}
</script>

<style>

</style>