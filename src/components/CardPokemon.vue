<script setup>
const pokemon = defineProps(["name", "xp", "height", "img", "loading", "types", "abilities", "weight", "baseStats", "id"]);
</script>

<template>
  <div class="card CardPokemonSelected" :class="loading ?  '' : 'animate__animated animate__flipInY'"> 
    <img 
      v-if="name"
      :src="img" 
      height="230" class="card-img-top pt-2" 
      :alt="name">
    <img 
      v-else=""
      src="../assets/img/egg_pokemon.svg"
      height="240" class="card-img-top pt-2" 
      alt="???">
    <div class="card-body">
      <div class="d-flex justify-content-center align-items-center position-relative">
        <span class="badge bg-primary position-absolute start-0">ID: {{ id }}</span>
        <h2 class="card-title mb-0">{{ name || '???' }}</h2>
    
      </div>
      <hr>
      <div class="row">
        <section class="col">
          <strong>XP:</strong>
          <span>{{ xp }}</span>
        </section>
        <section class="col">
          <strong>Height:</strong>
          <span>{{ height }}</span>
        </section>
        <section class="col">
          <strong>Weight:</strong>
          <span>{{ weight }}</span>
        </section>
      </div>
      <div class="row mt-4">
        <section class="col">
          <strong>Type(s):</strong>
          <span v-for="type in types" :key="type.type.name">{{ type.type.name }} </span>
        </section>
        <section class="col">
          <strong>Abilities:</strong>
          <span v-for="ability in abilities" :key="ability.ability.name">{{ ability.ability.name }} </span>
        </section>
      </div>
      <div class="row mt-4">
        <section class="col">
          <strong>Base Stats:</strong>
          <div class="row">
            <div class="col-6" v-if="baseStats?.hp">
              <strong>HP:</strong> {{ baseStats.hp }}
            </div>
            <div class="col-6" v-if="baseStats?.attack">
              <strong>Attack:</strong> {{ baseStats.attack }}
            </div>
            <div class="col-6" v-if="baseStats?.defense">
              <strong>Defense:</strong> {{ baseStats.defense }}
            </div>
            <div class="col-6" v-if="baseStats?.specialAttack">
              <strong>Special Attack:</strong> {{ baseStats.specialAttack }}
            </div>
            <div class="col-6" v-if="baseStats?.specialDefense">
              <strong>Special Defense:</strong> {{ baseStats.specialDefense }}
            </div>
            <div class="col-6" v-if="baseStats?.speed">
              <strong>Speed:</strong> {{ baseStats.speed }}
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.CardPokemonSelected {
  height: 75vh; 
  background-color: rgb(236, 233, 233);
  overflow: hidden;

  @media (max-width: 768px) {
    height: 100%; 
  }
}
.position-relative {
  position: relative;
}

.position-absolute {
  &.end-0 {
    position: absolute;
    right: 0;
  }
}


</style>

