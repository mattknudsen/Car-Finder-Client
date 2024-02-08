<template>
  <HomePage/>

</template>

<script>
import { ref } from 'vue'
//import HelloWorld from './components/HelloWorld.vue'
import HomePage from './components/HomePage.vue'

export default {
  name: 'LayoutDefault',

  components: {
    //HelloWorld,
    HomePage
  },

  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>

<style scoped>
</style>
