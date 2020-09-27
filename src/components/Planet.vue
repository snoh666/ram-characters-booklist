<template>
  <div class="planet">
    <div class="planet__header">
      <h5>
        {{name}}
      </h5>
      <button v-on:click="() => getCharactersData(residents)">
        Show residents
      </button>
    </div>
    <div v-if="characters.length > 0">
      <ul>
        <li v-for="character in characters" v-bind:key="character.id">
          <Character v-bind:name="character.name" v-bind:image-url="character.image" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Character from "@/components/Character";
export default {
  name: "Planet",
  components: {Character},
  props: {
    name: String,
    residents: Array,
  },
  data: () => ({
    characters: [],
  }),
  methods: {
    getCharactersData: async function (array) {
      const response = await Promise.all(array.map(link => fetch(link).then(response => response.json())));
      console.log('[RESPONSE]', response);
      this.characters = response;
    }
  }
}
</script>

<style scoped>
  .planet {
    margin: 1rem 0;
    padding: 0 1rem;
  }

  .planet__header {
    margin: 1rem 0;
    padding: 0 .5rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  ul {
    list-style: none;
    padding: 0 .75rem;
  }
</style>
