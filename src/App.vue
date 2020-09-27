<template>
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
@import url('https://fonts.googleapis.com/css2?family=Epilogue&display=swap');

*, *::before, *::after {
  font-family: 'Epilogue', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
