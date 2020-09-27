<template>
  <div>
    <h1>
      Rick and morty planets
    </h1>
    <ul v-if="locations.length > 0">
      <li v-for="{id, name, residents} in locations" :key="id">
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
    this.fetchLocations();
  },
  methods: {
    fetchLocations: async () => {
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

</style>
