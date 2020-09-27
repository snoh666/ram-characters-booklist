<template>
  <div class="character__wrapper">
    <img v-bind:src="imageUrl" alt="Character Face">
    <h6>{{name}}</h6>
  </div>
</template>

<script>
export default {
  name: "Character",
  props: {
    name: String,
    imageUrl: String,
    status: Boolean,
  },
}
</script>

<style scoped>
  .character__wrapper {
    margin: 1rem 0;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  img {
    width: 64px;
    height: 64px;
  }
</style>
