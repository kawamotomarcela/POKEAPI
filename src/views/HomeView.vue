<script setup>
import { onMounted, ref } from "vue";
import ListPokemons from "../components/ListPokemons.vue";
import CardPokemon from "../components/CardPokemon.vue";

let urlImgSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/");
let pokemons = ref([]);
let searchPokemon = ref("");
let pokemonSelected = ref(null);
let loading = ref(false);



onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=200&offset=0")
    .then(res => res.json())
    .then(res => {
      pokemons.value = res.results.map((pokemon, index) => ({
        ...pokemon,
        id: index + 1 
      }));
    });
});

const selectPokemon = async (pokemon) => {
  loading.value = true;
  await fetch(pokemon.url)
    .then(res => res.json())
    .then(res => {
      pokemonSelected.value = {
        name: res.name,
        base_experience: res.base_experience,
        height: res.height,
        sprites: res.sprites,
        types: res.types,
        abilities: res.abilities,
        weight: res.weight,
        baseStats: {
          hp: res.stats.find(stat => stat.stat.name === "hp")?.base_stat,
          attack: res.stats.find(stat => stat.stat.name === "attack")?.base_stat,
          defense: res.stats.find(stat => stat.stat.name === "defense")?.base_stat,
          specialAttack: res.stats.find(stat => stat.stat.name === "special-attack")?.base_stat,
          specialDefense: res.stats.find(stat => stat.stat.name === "special-defense")?.base_stat,
          speed: res.stats.find(stat => stat.stat.name === "speed")?.base_stat
        },
        id: res.id
      }
    })
    .catch(err => alert(err))
    .finally(() => { loading.value = false; });
  
  console.log(pokemonSelected.value);
}
</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-3">
        <div class="col-sm-12 col-md-6">
          <CardPokemon
            :name="pokemonSelected?.name"
            :xp="pokemonSelected?.base_experience"
            :height="pokemonSelected?.height"
            :img="pokemonSelected?.sprites?.other?.dream_world?.front_default"
            :loading="loading"
            :types="pokemonSelected?.types"
            :abilities="pokemonSelected?.abilities"
            :weight="pokemonSelected?.weight"
            :baseStats="pokemonSelected?.baseStats"
            :id="pokemonSelected?.id"
          />
        </div>
        <div class="col-sm-12 col-md-6">
          <div class="card card-list">
            <div class="card-body row">
              <div class="mb-3">
                <label hidden for="searchPokemon" class="form-label">Pesquisar Pokemon</label>
                <input v-model="searchPokemon" type="text" class="form-control" id="searchPokemon" placeholder="Pesquisar...">
              </div>
              <ListPokemons 
                :pokemons="pokemons" 
                :selectPokemon="selectPokemon"
                :searchPokemon="searchPokemon"
                :urlImgSvg="urlImgSvg"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.container {
  margin-bottom: 20px; 
}
.card-list {
  max-height: 92%;
  margin-bottom: 2rem;
}
</style>
