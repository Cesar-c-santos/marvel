<template lang="html">  
<div>
<h3>Lista Personagens Marvel</h3>

<ul>
<li v-for="character in characters">
<router-link :to="{name:'character', params: {id: character.id } }">{{character.name}}</router-link>

</li>

</ul>
    </div>

</template>


<script>

import axios from 'axios'
import {public_key, ts, hash} from '../marvel';

export default {
    name: 'Characters',

    data(){

        return {
            characters: []
         }

    },

    mounted(){
  this.getCharacters()
    },
    
 methods:{
 getCharacters: function(){

axios.get (`https://gateway.marvel.com:443/v1/public/characters?ts=${ts}&apikey=${public_key}&hash=${hash}`)
  .then ((result) => {
    
  result.data.data.results.forEach((item)  => {
 console.log(item)

 this.characters.push(item)

  })

 })
 .catch((error)=>{
 console.log(error)
 })

 }
 }
 }
 </script>
<style lang="css">
</style>
