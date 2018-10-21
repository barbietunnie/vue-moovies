<template>
    <div>
        <router-link :to="moviePath">
            <img :src="posterPath" :alt="movie.title" />
        </router-link>
    </div>
</template>
<script>
const POSTER_PATH_PREFIX = 'https://image.tmdb.org/t/p/w154';

export default {
    name: 'Movie',
    props: ['movie'],
    computed: {
        posterPath: function() {
            return `${POSTER_PATH_PREFIX}${this.movie.poster_path}`;
        },
        moviePath: function() {
            return `/movies/${this.movie.id}`;
        }
    }
}
</script>
<style scoped>
a {
    text-decoration: none;
}

h3 {
    color: #415A77;
}
img {
    box-shadow: 0 0 35px #111;
}
</style>

