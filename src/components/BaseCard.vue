<template>
    <div class="">
        <img :src="imgUrl + pokemon.id + '.png'" width="100" alt="pokemon_img">
        <div>{{ pokemon.name }}</div>
    </div>
</template>

<script>
export default {
    name: "BaseCard",
    props: {
        pokemon: {
            type: Object,
        },
        imgUrl: {
            type: String
        }
    },
}
</script>