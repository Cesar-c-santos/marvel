<template lang="html">
<div>
<h3> Informação Personagem</h3>
<p>{{this.$route.params.id}}</p>

<img :src = "url" alt="">
<ul>
<li v-for="char in character">
{{char.name}}
{{char.description}}
</li>
</ul>

</div>
  </template>

  
  <script>
import {public_key, ts, hash} from '../marvel';
import axios from 'axios'
  export default {
      name: 'Characters',

      data(){

        return {
          character:[],
          url: '',
          size: 'standard_large.jpg',
        }

      },

mounted (){

this.getCharacter()
},

      methods: {
          getCharacter: function(){
         
            var characterId = this.$route.params.id
            axios.get (`https://gateway.marvel.com:443/v1/public/characters/${characterId}?ts=${ts}&apikey=${public_key}&hash=${hash}`)
            .then((result) =>{

              console.log(result)
              result.data.data.results.forEach((item) =>{

                this.character.push(item)

                this.url = `${item.thumbnail.path}/${this.size}`
                console.log(this.url)


              })


            })
            .catch((error) =>{
              console.log(errror)
            })

 
          }
        }
  }

  </script>
  <style lang="css">
  
  </style>