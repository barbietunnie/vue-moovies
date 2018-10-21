<template>
    <header>
        <h1>
            <router-link to="/">
                <img src="../assets/logo.svg" alt="Logo" />
            </router-link>
        </h1>
    </header>
</template>

<script>
    export default {
        name: 'Header',
        props: {
            title: String
        },
        data() {
            return {
                show: false
            };
        }
    }
</script>

<style scoped>
    header {
        background-color: #0D1B2A;
        padding: 10px;
        color: white;
        margin: 0;
    }
    h1 {
        margin: 0;
    }
</style>
