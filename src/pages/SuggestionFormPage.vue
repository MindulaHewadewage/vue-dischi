<script>
import axios from 'axios';
const endpoint = '';
const emptyForm = { title: '', publisher: '', platform: '', genre: '', image: '', price: '', release_Date: '', size: '' };

export default {
    name: 'SuggestionFormPage',
    data: () => ({
        form: emptyForm,


    }),
    methods: {
        sendForm() {
            axios.post(endpoint, this.form)
                .then(() => { this.form = emptyForm })
        }
    }
}

</script>



<template>
    <section class="suggestion-form">
        <h3 class="my-4">Aggiungi un gioco</h3>
        <form novalidate @submit.prevent="sendForm">
            <div class="container">
                <div class="row">
                    <!-- TITOLO -->
                    <div class="col-6">
                        <div class="mb-3">
                            <label for="title" class="form-label">Titolo:</label>
                            <input type="text" class="form-control" id="title" placeholder="Titolo" name="title">
                        </div>
                    </div>

                    <!-- Publisher -->
                    <div class="col-6">
                        <div class="mb-3">
                            <label for="publisher" class="form-label">Publisher:</label>
                            <input type="text" class="form-control" id="publisher" placeholder="Publisher" name="publisher">
                        </div>
                    </div>


                    <!-- Piattaforma -->
                    <div class="col-3">
                        <div class="mb-3">
                            <label for="platform" class="form-label">Piattaforma:</label>
                            <select class="form-select" name="platform" id="Piattaforma">
                                <option value="">PC</option>
                                <option value="">PS4 </option>
                                <option value="">XBOX</option>
                                <option value="">SWITCH</option>
                            </select>
                        </div>
                    </div>

                    <!-- Genere -->
                    <div class="col-3">
                        <div class="mb-3">
                            <label for="genre" class="form-label">Genere:</label>
                            <select class="form-select" name="genre" id="genre">
                                <option value="">Horror</option>
                                <option value="">Fantasy</option>
                                <option value="">RPG</option>
                                <option value="">Sparatutto</option>
                            </select>
                        </div>
                    </div>

                    <!-- Immagine Copertina -->
                    <div class="col-6">
                        <div class="mb-3">
                            <label for="image" class="form-label">Immagine:</label>
                            <input type="url" class="form-control" id="image" placeholder="Immagine di copertina"
                                name="image">
                        </div>
                    </div>

                    <!-- Prezzo -->
                    <div class="col-4">
                        <div class="mb-3">
                            <label for="price" class="form-label">Prezzo:</label>
                            <input type="number" class="form-control" id="price" placeholder="Prezzo" name="price">
                        </div>
                    </div>

                    <!-- Data di rilascio -->
                    <div class="col-4">
                        <div class="mb-3">
                            <label for="release_date" class="form-label">Data di rilascio:</label>
                            <input type="date" class="form-control" id="release_date" placeholder="Data di rilascio"
                                name="release_date">
                        </div>
                    </div>


                    <!-- Peso -->
                    <div class="col-4">
                        <div class="mb-3">
                            <label for="size" class="form-label">Peso:</label>
                            <input type="number" class="form-control" id="size" placeholder="Peso" name="size">
                        </div>
                    </div>

                    <!-- Bottoni -->
                    <div class="mb-3 d-flex justify-content-end">

                    </div>


                </div>
            </div>
        </form>
    </section>
</template>

<style scoped lang="scss"></style>