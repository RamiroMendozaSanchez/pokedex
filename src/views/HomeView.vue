<template>
  <div>
    <div class="content">
      <div class="grid-cards">
        <div class="cards">
          <div v-for="(data, index) in pokemons" :key="index">
            <v-app id="inspire">
              <v-card
                class="mx-autor"
                max-width="400"
                :elevation="4"
              >
                <v-img
                  class="white--text align-end pointe"
                  height="200px"
                  :src="data.img"
                >
                </v-img>

                <v-card-text class="text--primary">
                  <div>{{ data.name }}</div>
                </v-card-text>

                <v-card-actions class="primary">
                  <v-btn class="pa-md-4 mx-lg-auto" color="white" text @click="send_info(data)"> Guardar </v-btn>
                </v-card-actions>
              </v-card>
            </v-app>
          </div>
        </div>
      </div>
      <div class="info">
        <pokemonInfo
          :pokemon_info="selected_pokemon"
          @send_url="receiveUrl"
        ></pokemonInfo>
         <v-btn
        rounded
        color="error"
        class="ma-4"
        @click="vaciar()"
      >
        Vaciar 
      </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import pokemonInfo from "/src/components/pokemonInfo.vue";
export default {
  components: {
    pokemonInfo,
  },
  data() {
    return {
      isActive: true,
      pokemons: [],
      selected_pokemon: [],
    };
  },
  created() {
    let instance = this;
    for (let i = 0; i <= 10; i++) {
      axios
        .get(`https://pokeapi.co/api/v2/pokemon/${i + 1}`)
        .then((response) => {
          console.log(response);
          let pokemon = {
            abilities: response.data.abilities,
            name: response.data.name,
            img: response.data.sprites.front_default,
          };
          instance.pokemons.push(pokemon);
        })
        .catch((err) => {
          console.log(err);
        });
      console.log(this.pokemons);
    }
  },
  methods: {
    send_info(pokemon_info) {
      this.selected_pokemon.push(pokemon_info);
    },

    vaciar() {
      this.selected_pokemon.splice(0, this.selected_pokemon.length)
    },

    receiveUrl(url) {
      window.location.replace(url);
    },
  },
};
</script>

<style scoped>
.content {
  width: 90%;
  height: 100%;
  margin: 0 auto;
  display: grid;
  grid-template-columns: auto auto auto auto auto auto auto auto auto auto auto;
  grid-template-rows: auto;
}

.center {
  text-align: center;
  margin-top: 1%;
}

.pointer {
  cursor: pointer;
}

.grid-cards {
  grid-column: 1/9;
}

.cards{
  margin-top: 1rem;
  gap: 1rem;
  display: grid;
  grid-auto-flow: dense;
  grid-auto-rows: 22rem;
  grid-template-columns: repeat(auto-fill, minmax(15rem, 1fr));
}

.info{
  grid-column: 10/12;
}
</style>
