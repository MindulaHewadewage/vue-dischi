<script>
import axios from 'axios';
const apiUrl = 'http://127.0.0.1:8000/api/videogames';
export default {
    name: 'HomePage',
    data() {
        return {
            games: []
        }
    },
    methods: {
        fetchGames() {
            axios.get(apiUrl).then(res => { this.games = res.data })
        }
    },
    created() {
        this.fetchGames();
    }
}
</script>



<template>
    <h1 class="mb-3">BoolGaming's catalog</h1>

    <div class="card-section d-flex justify-content-around flex-wrap pt-3">

        <div v-for="game in games" class="card mb-4 mx-2">
            <div class="row g-0">
                <div class="col-7 m-0">
                    <img :src="game.image" class="w-100 h-100 rounded-start" :alt="game.title">
                </div>
                <div class="col-5 m-0">
                    <div class="card-body">
                        <h4 class="card-title">{{ game.title }}</h4>
                        <p class="card-text">Prezzo: <b>${{ game.price }}</b></p>
                        <p class="card-text">Publisher: {{ game.publisher }}</p>
                        <p class="card-text">Piattaforma: {{ game.platform }}</p>

                        <p class="card-text m-0">Generi:</p>
                        <ul class="list-group-item">
                            <li v-for="genre in game.genres" class="list-group-item">
                                <span>{{ genre }}</span>
                            </li>
                        </ul>
                        <p class="card-text"><small class="text-muted">Data di rilascio: {{ game.releaseDate }}</small></p>
                        <p class="card-text"><small class="text-muted">Peso: {{ game.weight }}</small></p>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped lang="scss">
.card-section {
    border-top: 1px solid gray;

    .card {
        width: 450px;
    }
}
</style>