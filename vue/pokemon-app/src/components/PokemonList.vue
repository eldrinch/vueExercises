<template>
  <div>
    <h1>Pokemon App</h1>
    <loader v-if="isLoading"></loader>
    <div class="div-pokemon" v-for:="(pokemon, index) in list" :key="index" @click="selectPokemon(getPokemonId(pokemon.url))">
      <img :src="getPokemonImage(getPokemonId(pokemon.url))" />
      {{ pokemon.name }}
    </div>
  </div>
</template>

<script>
import { getPokemonImageUrl, getPokemonList } from "../service/pokemon-service.js";
import { onMounted, ref } from "vue";
import { useRouter } from "vue-router";
import Loader from "./Loader.vue";

export default {
  components: {
    Loader,
  },

  setup() {
    const list = ref([]);
    const router = useRouter();
    const isLoading = ref(false);

    onMounted(() => {
      isLoading.value = true;
      getPokemonList()
        .then((resp) => {
          list.value = resp.results;
        })
        .finally(() => {
          isLoading.value = false;
        });
    });

    const getPokemonId = (url) => url.replace("https://pokeapi.co/api/v2/pokemon/", "").replace("/", "");

    const getPokemonImage = (id) => getPokemonImageUrl(id);

    const selectPokemon = (id) => router.push({ name: "pokemon", params: { id } });

    return { list, isLoading, getPokemonId, getPokemonImage, selectPokemon };
  },
};
</script>

<style>
.div-pokemon {
  display: flex;
  align-items: center;
  border: 1px solid lightgrey;
  border-radius: 0.2rem;
  margin: 0.5rem;
  cursor: pointer;
}
</style>
