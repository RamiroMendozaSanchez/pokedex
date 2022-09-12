<template>
  <div>
    <div class="static">
      <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">
              Nombre
            </th>
            <th class="text-left">
              Habilidad
            </th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(pokemon, i) in pokemon_info"
            :key="i"
          >
            <td>{{ pokemon.name }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pokemon_info: [],
  },
  data() {
    return {
    };
  },
};
</script>

<style scoped>
.static{
  position: inherit;
  margin-top: 1rem;
}

.pointer{
    cursor: pointer;
}
</style>