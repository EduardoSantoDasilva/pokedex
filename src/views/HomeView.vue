<script setup>
import {ref,onMounted, reactive, computed } from 'vue';
import ListaPokemons from "../components/ListaPokemons.vue"
import CardPokemonSelect from "../components/CardPokemonSelect.vue"

let url = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/");
let pokemons = reactive(ref());
let searchPokemonFild = ref("");
let pokemonSelected = reactive(ref());
let loading = ref(false);

onMounted( async()=>{
 await fetch("https://pokeapi.co/api/v2/pokemon?limit=200&offset=0")
  .then(res => res.json())
  .then(data => pokemons.value = data.results)
})

const PokemonFiltered = computed(()=>{
    if(pokemons.value && searchPokemonFild.value){
      return pokemons.value.filter(pokemon=>
        pokemon.name.toLowerCase().includes(searchPokemonFild.value.toLowerCase())
      );
    }
    return pokemons.value
})

const selectPokemon = async (pokemon) =>{
  loading.value = true;
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(data => pokemonSelected.value = data)
  .catch(err => alert(err))
  .finally(()=> loading.value=false)

  console.log(pokemonSelected.value)
  
}
  
</script>
<!--:abilities="pokemonSelected?.abilities[0].ability.name"-->
<template>
  <main>
    <div class="container text-body-secondary">
        <div class="row pt-3">
          <div class="col-sm-12 col-md-6">
            <CardPokemonSelect
            :name="pokemonSelected?.name"
            :abilities="pokemonSelected?.abilities"
            :xp="pokemonSelected?.base_experience"
            :species="pokemonSelected?.species.name"
            :height="pokemonSelected?.height"
            :weight="pokemonSelected?.weight"
            :url="pokemonSelected?.sprites.other.dream_world.front_default"
            :loading="loading"
            />
            
          </div>

          <div class="col-sm-12 col-md-6">
            <div class="card card-list">
              <div class="card-body row">
                <div class="mb-3">
                  <label for="searchPokemonFild" class="form-label visually-hidden">Pesquisar Pokemon</label>
                  <input 
                      v-model="searchPokemonFild"
                      type="name" class="form-control" 
                      id="searchPokemonFild" 
                      placeholder="Pesquisar">
                </div>
                <ListaPokemons 
                  v-for="pokemon in PokemonFiltered"
                  :key="pokemon.name"
                  :name="pokemon.name"
                  :url=" url + pokemon.url.split('/')[6] + '.svg' "
                  @click = "selectPokemon(pokemon)"
                />
              </div>
                
            </div>
            
            
          </div>
        </div>
    </div>
  </main>
</template>

<style scoped>
.card-list{
  max-height: 75vh;
  overflow: scroll;
  overflow-x: hidden;
}

@media (max-width: 768px){
  .card-list{
  max-height: 48vh;
  
}
}
</style>