<template>
  <div class="home">
    <characters/>
      </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Characters from '@/components/Characters.vue'


export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Characters
  }

}

</script>
