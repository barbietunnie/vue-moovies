<template>
    <div>
        <ul>
            <li :key="movie.id" v-for="movie in movies">
                <Movie :movie="movie" />
            </li>
        </ul>
    </div>
</template>
<script>
    import Movie from './Movie.vue';

    export default {
        name: 'MoviesList',
        data() {
            return {
                movies: []
            };
        },
        created: function() {
            this.fetchData();
        },
        methods: {
            fetchData: async function() {
                try {
                    const res = await fetch(`https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=${process.env.VUE_APP_TMDB_API_KEY ? process.env.VUE_APP_TMDB_API_KEY : ''}`);
                    const movies = await res.json();
                    this.movies = movies.results;
                } catch (e) {
                    console.error(e);
                }
            }
        },
        components: {
            Movie
        }
    };
</script>
<style scoped>
ul {
    list-style-type: none;
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-row-gap: 2.5rem;
    padding: 1rem;
    margin: 0;
    background: #111;
}
</style>
