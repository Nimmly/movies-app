<template>
    <div>
        <h3>Store movies</h3>
        <b-form @submit.prevent="storeMovie">
            <b-form-group 
                    label="Title:"
                    >
                <b-form-input 
                      type="text"
                      v-model="form.title"
                      placeholder="title">
                </b-form-input>
            </b-form-group>
        <b-form-group 
                    label="Director:"                   
                    >
            <b-form-input 
                      type="text"
                      v-model="form.director"
                      placeholder="Enter director">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="ImageURL:"                    
                    >
            <b-form-input 
                      type="text"
                      v-model="form.imageUrl"
                      placeholder="Enter image URL">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="Duration:"                    
                    >
            <b-form-input
                      type="text"
                      v-model="form.duration"
                      placeholder="Enter duration">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="Release Date:"                    
                    >
            <b-form-input 
                      type="text"
                      v-model="form.releaseDate"
                      placeholder="Enter release date">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="Genre:"                   
                    >
            <b-form-input 
                      type="text"
                      v-model="form.genre"
                      placeholder="Enter genre">
            </b-form-input>
        </b-form-group>
        <b-button type="submit" variant="primary">Submit</b-button>
        </b-form>
        <div>List of movies
        <div class='container'>
        <movie-row
         v-for="movie in movies"
         :key="movie.id"
         :movie="movie"/>
        </div>
        </div>
      
    </div>
</template>

<script>
import { movies } from '../services/movies.js'
import MovieRow from './MovieRow.vue'
export default {
    components:{
        MovieRow
    },
    data(){
        return{
            form:{
                title: '',
                director: '',
                imageUrl: '',
                duration: '',
                releaseDate: '',
                genre: ''
            },
            movies:[]
        }
    },
    beforeRouteEnter (to, from, next) {
    movies.getAll()
      .then((response) => {
          next((vm) => {
            vm.movies = response.data
          })
      })
  },
  methods:{
      storeMovie(){
          movies.add(this.form).then(() => {
              this.$router.push('/movies')
          })
      }
  }
}
</script>

<style>

</style>
