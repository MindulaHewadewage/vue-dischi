<script>
import axios from 'axios';
const apiBaseUrl = 'http://127.0.0.1:8000/api/';
export default {
    name: 'ShowPage',
    data() {
        return {
            game: {}
        }
    },
    methods: {
        getGame() {
            axios.get(apiBaseUrl + 'videogames/' + this.$route.params.id).then(res => { this.game = res.data })
        }
    },
    created() {
        this.getGame();
    }
}
</script>



<template>
    <h1 class="mb-3">BoolGaming</h1>
    <div class="card-section d-flex justify-content-center">
        <div class="card mt-3">
            <div class="row g-0">
                <div class="col-4">
                    <img :src="game.image_url" class="w-100 h-100 rounded-start" :alt="game.title">
                </div>
                <div class="col-8">
                    <div class="card-body p-4">
                        <h3 class="card-title">{{ game.title }}</h3>
                        <p class="card-text">
                            {{ game.description }}
                        </p>
                        <p class="card-text">Publisher: {{ game.publisher }}</p>
                        <p class="card-text">Piattaforma: {{ game.platform }}</p>

                        <p class="card-text m-0">Generi:</p>
                        <ul class="list-group-item">
                            <li v-for="genre in game.genres" class="list-group-item">
                                <span>{{ genre }}</span>
                            </li>
                        </ul>
                        <p class="card-text"><small class="text-muted">Data di rilascio: {{ game.releaseDate }}</small>
                        </p>
                        <p class="card-text"><small class="text-muted">Peso: {{ game.weight }}</small></p>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="text-center mt-4">
        <router-link to="/" class="btn btn-secondary">Torna alla home</router-link>
    </div>
</template>

<style scoped lang="scss">
.card-section {
    border-top: 1px solid gray;
}
</style>