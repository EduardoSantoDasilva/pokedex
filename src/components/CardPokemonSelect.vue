<script setup>
const pokemon = defineProps(["name","xp","height","weight","url","loading","abilities","species"]);
</script>

<template>
    <div class="card cardListPokemonSelect"
    :class="loading ? '' : 'animate__animated animate__backInDown'"
    >
        <img v-if="pokemon.name" :src="url" class="card-img-top p-3" :alt="name" >
        <img v-else src="../assets/egg_pokemon.svg" class="card-img-top p-3" alt="???" >
        <div class="card-body">
            <h5 class="card-title text-center mb-5">{{ pokemon.name || 'Pokemon'}}</h5>
            <hr>
            <div class="row">
                    <section class="col">
                        <strong>XP:</strong>
                        <span class="p-2">{{ pokemon.xp || '00' }}</span>
                    </section>

                    <section class="col">
                        <strong>ALTURA:</strong>
                        <span class="p-2">{{ pokemon.height || '00' }}</span>
                    </section>

                    <section class="col">
                        <strong>LARGURA:</strong>
                        <span class="p-2">{{ pokemon.weight || '00' }}</span>
                    </section>

                    <section class="col">
                        <strong>ESPÉCIE:</strong>
                        <span class="p-2">{{ pokemon.species || '00' }}</span>
                    </section>

                    <section class="pt-1 text-center">
                        <strong>habilidade:</strong>
                        <span class="p-1" v-for="i in pokemon.abilities">{{ i.ability.name|| '00' }}</span>
                    </section>
                
                
            </div> 
        </div>
    </div>
</template>

<style scoped>
    .cardListPokemonSelect{
        height: 75vh;
        background-color: #f70a0a;
        background-image: linear-gradient(160deg, #e73b3b 0%, #ce7869 100%);
    }

    .cardListPokemonSelect img{
        height: 300px;
    }

    @media(max-width: 768px){
        .cardListPokemonSelect{
        height: 30vh;
        width: 40%;
        margin: 0 auto 10px auto;
        }
        .cardListPokemonSelect img{
        height: 100px;
        }

    }
</style>