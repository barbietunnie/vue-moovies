<template>
    <transition name="fade">
        <div class="movie-wrapper" :style="styles">
            <div class="movie-info">
                <h1>{{ movie.title }}</h1>
                <h3>Release Date: {{ movie.release_date }}</h3>
                <p>
                    {{ movie.overview }}
                </p>
            </div>
        </div>
    </transition>
</template>
<script>
const BACKDROP_PATH_PREFIX = 'https://image.tmdb.org/t/p/w1280';

export default {
    name: 'MovieDetail',
    data() {
        return {
            movie: {}
        };
    },
    created: function() {
        this.fetchData();
    },
    computed: {
        styles: function() {
            return `background-image: url(${BACKDROP_PATH_PREFIX}${this.movie.backdrop_path}); background-repeat: no-repeat; background-size: cover;`;
        }
    },
    methods: {
        fetchData: async function() {
            try {
                const res = await fetch(`https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=${process.env.VUE_APP_TMDB_API_KEY ? process.env.VUE_APP_TMDB_API_KEY : ''}`);
                const movie = await res.json();
                this.movie = movie;
            } catch (e) {
                console.error(e);
            }
        }
    }
}
</script>
<style scoped>
.movie-wrapper {
    position: relative;
    padding-top: 50vh;
}
.movie-info {
    background: #FFF;
    color: #222;
    padding: 2rem 10%;
}
</style>


