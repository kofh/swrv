<template>
  <div class="content">
    <button @click="count = 1">component 1</button>
    <button @click="count = 2">component 2</button>
    <button @click="count = 3">component 3</button>
    <Repos :key="`${count}-${idx}`" v-for="idx in 5" :count="count" />
    <!-- <Simple /> -->
  </div>
</template>

<script>
// import Simple from '@/components/Simple.vue'
import Repos from '@/components/Repos.vue'
import { mutate } from '../../../src/use-swrv'

export default {
  components: { Repos },
  data () {
    return {
      count: 1
    }
  }
}
</script>

<style>
html, body { height: 100%; margin: 0;}
body {
  font-size: 2rem;
  display: flex;
  font-family:-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  justify-content: center;
  align-items: center;
}
</style>
