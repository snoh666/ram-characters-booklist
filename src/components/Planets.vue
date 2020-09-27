<template>
  <div>
    <h1>
      Rick and morty planets
    </h1>
    <ul v-if="locations?.length > 0">
      <li v-for="{id, name, residents} in locations" v-bind:key="id">
        <Planet
            v-bind:name="name"
            v-bind:residents="residents"
        />
      </li>
    </ul>
    <p v-else>No locations available</p>
  </div>
</template>

<script>
import Planet from "./Planet";

export default {
  name: "Planets",
  components: {
    Planet,
  },
  data: () => ({
    locations: [],
  }),
  created () {
    this.getLocations();
  },
  methods: {
    getLocations: async function () {
      const response = await fetch("https://rickandmortyapi.com/api/location", {
        method: "GET",
      });
      const data = await response.json();
      this.locations = data.results;
    }
  }
}
</script>

<style scoped>
  h1 {
    margin: 1rem .25rem;
  }
  ul {
    list-style: none;
  }
</style>
