<template>
    <div class='row'>
        <div class='col-sm' v-text="movie.title"></div>
        <div class='col-sm' v-text="movie.director"></div>
        <div class='col-sm' v-text="movie.releaseDate"></div>
        <div class='col-sm' v-text="movie.genre"></div>
    </div>
</template>

<script>
export default {
    props:{
        movie:{
            type: Object,
            required: true
        }
    }
}
</script>

<style>

</style>
