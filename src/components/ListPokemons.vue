<script setup>
import { defineProps, ref, computed, watchEffect } from 'vue';
import Paginacao from './Paginacao.vue';

const props = defineProps({
  pokemons: Array,
  selectPokemon: Function,
  searchPokemon: String,
  urlImgSvg: String
});

let currentPage = ref(1);
const itemsPerPage = 9; 

const pokemonsFiltered = computed(() => {
  if (props.pokemons && props.searchPokemon) {
    const searchTerm = props.searchPokemon.toLowerCase();

    if (!isNaN(searchTerm) && Number(searchTerm) > 0 && Number(searchTerm) <= 200) {
      return props.pokemons.filter(pokemon =>
        pokemon.id === Number(searchTerm)
      );
    } else {
      return props.pokemons.filter(pokemon =>
        pokemon.name.toLowerCase().includes(searchTerm)
      );
    }
  }
  return props.pokemons;
});

const paginatedPokemons = computed(() => {
  if (!pokemonsFiltered.value) return [];
  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return pokemonsFiltered.value.slice(start, end);
});

const totalPages = computed(() => {
  if (!pokemonsFiltered.value) return 1;
  return Math.ceil(pokemonsFiltered.value.length / itemsPerPage);
});

const changePage = (page) => {
  if (page >= 1 && page <= totalPages.value) {
    currentPage.value = page;
  }
};

watchEffect(() => {
  currentPage.value = 1;
});
</script>

<template>
  <div>
    <div class="row">
      <div v-if="paginatedPokemons.length === 0" class="col-12 text-center">
        <p>Pokémon não encontrado =(</p>
      </div>
      <div class="col-4" v-for="pokemon in paginatedPokemons" :key="pokemon.id"
           @click="() => props.selectPokemon(pokemon)">
        <div class="card p-2 mb-3 cardsPokemon">
          <p class="text-center">{{ pokemon.name }}</p>
          <img :src="props.urlImgSvg + pokemon.url.split('/')[6] + '.svg'" class="card-img-top" alt="..."
               height="80" />
        </div>
      </div>
    </div>
    <Paginacao
     v-if="paginatedPokemons.length > 0" 
     :currentPage="currentPage" 
     :totalPages="totalPages" 
     :changePage="changePage" 
     />
  </div>
</template>

<style lang="scss" scoped>
.cardsPokemon {
  background: rgb(198, 238, 174);
  background: radial-gradient(circle, rgba(198, 238, 174, 1) 0%, rgba(148, 187, 233, 1) 100%);
  cursor: pointer;

  &:hover {
    background: rgb(198, 238, 174);
    background: radial-gradient(circle, rgb(174, 245, 133) 0%, rgb(89, 150, 219) 100%);
  }

  img {
    &:hover {
      padding: 0.1rem;
    }
  }
}

</style>

