<template>
  <h1>
    Hello Vue application
  </h1>
  <Planets />
</template>

<script>
import Planets from './components/Planets';

export default {
  name: 'App',
  components: {
    Planets,
  }
}
</script>

<style>
</style>
