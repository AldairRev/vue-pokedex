<template>
    <div class="pokemon-card">
        <img
            class="pokemon-card__pokemon"
            :src="imgUrl + pokemon.id + '.png'"
            alt="pokemon_img"
        >
        <div class="pokemon-card__name">{{ pokemon.name }}</div>
    </div>
</template>

<script>
export default {
    name: "PokemonCard",
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