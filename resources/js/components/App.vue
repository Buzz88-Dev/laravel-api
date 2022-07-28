<template>
    <div class="card" style="width: 18rem;">
        <!-- <img src="..." class="card-img-top" alt="..."> -->
        <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
    </div>
</template>

<script>
export default {
    name : 'App',

    data(){
        return {
            posts: []
        }
    },

    created() {
        // qui facciamo la richiesta con axios di tipo get
        axios.get('http://127.0.0.1:8000/api/posts')
            .then(response => {
                this.posts = response.data.response.data;   // me ne da 2 perche in PostController ho indicato: $per_page = $request->query('per_page', 2);
                console.log(this.posts);
                console.log(response); // andare in http://127.0.0.1:8000/ e guardare la console; l oggetto risposta è piu complesso rispetto a quello che ci serve; i dati sono in data, response, data
            })
            .catch(error => console.log('errore!!!'))
    },
}
</script>

<style lang="scss" scoped>
</style>
