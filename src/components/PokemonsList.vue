<template>
    <div class="pokemons-list">
        <PokemonCard
            v-for="(pokemon, index) in pokemons"
            :key="index"
            :pokemon="pokemon"
            :imgUrl="imgUrl"
        />
        <div ref="infinitescrolltrigger">
            Loading...
        </div>
    </div>
</template>

<script>
import PokemonCard from './PokemonCard.vue';

import axios from 'axios';

export default {
    name: 'PokemonsList',
    components: {
        PokemonCard
    },
    props: {
        apiUrl: {
            type: String,
        }
    },
    data() {
        return {
            imgUrl: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/",
            pokemons: [],
            nextUrl: '',
            currentUrl: ''
        }
    },
    methods: {
        getData() {
        axios.get(this.currentUrl)
            .then(response => {
                if(response.status === 200) {
                    this.nextUrl = response.data.next;
                    response.data.results.forEach( p => {
                    p.id = p.url.split("/").filter(part => !!part).pop();
                    this.pokemons.push(p)
                    })
                }
            })
            .catch(error => {
                console.log(error)
            })
        },
        scrollTrigger() {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if(entry.intersectionRatio > 0 && this.nextUrl) {
                        this.currentUrl = this.nextUrl;
                        this.getData();
                    }
                });
            });

            observer.observe(this.$refs.infinitescrolltrigger);
        }
    },
    created() {
        this.currentUrl = this.apiUrl;
        this.getData();
    },
    mounted() {
        this.scrollTrigger();
    }
}
</script>