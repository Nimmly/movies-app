<template>
    <div>
        <h3>Store movies</h3>
        <b-form @submit="storeMovie">
            <b-form-group 
                    label="Title:"
                    >
                <b-form-input 
                      type="text"
                      v-model="form.title"
                      required
                      placeholder="title">
                </b-form-input>
            </b-form-group>
        <b-form-group 
                    label="Director:"                   
                    >
            <b-form-input 
                      type="text"
                      v-model="form.director"
                      required
                      placeholder="Enter director">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="ImageURL:"                    
                    >
            <b-form-input 
                      type="text"
                      v-model="form.imageUrl"
                      required
                      placeholder="Enter image URL">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="Duration:"                    
                    >
            <b-form-input
                      type="text"
                      v-model="form.duration"
                      required
                      placeholder="Enter duration">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="Release Date:"                    
                    >
            <b-form-input 
                      type="text"
                      v-model="form.releaseDate"
                      required
                      placeholder="Enter release date">
            </b-form-input>
        </b-form-group>
        <b-form-group 
                    label="Genre:"                   
                    >
            <b-form-input 
                      type="text"
                      v-model="form.genre"
                      required
                      placeholder="Enter genre">
            </b-form-input>
        </b-form-group>
        </b-form>
        <b-button type="submit" variant="primary">Submit</b-button>
        <div>List of movies</div>
      
    </div>
</template>

<script>
import {movies} from '../services/movies.js'
export default {
    data(){
        return{
            form:{
                title: '',
                director: '',
                imageUrl: '',
                duration: '',
                releaseDate: '',
                genre: ''
            }
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
          movies.store(this.form)
      }
  }
}
</script>

<style>

</style>
