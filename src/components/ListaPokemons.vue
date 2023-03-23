<script setup>
    const pokemon = defineProps([
        "name",
        "url","abilities"
    ])
</script>

<template>
    <div class="col-4 col-md-5 col-xl-3">
        <div class="card p-2 mb-3 cardListPokemon">
            <p class="text-center text-body-secondary">{{ pokemon.name }}</p>
            <img 
            :src="url" class="card-img-top" 
            :alt="name"
            height ="80"
            />
            <p class="text-center text-body-secondary"> {{ pokemon.abilities }}</p>
            
        </div>
    </div>
    
</template>

<style scoped>
.cardListPokemon{
    background-color: #0093E9;
    background-image: linear-gradient(160deg, #0093E9 0%, #80D0C7 100%);
    cursor: pointer;
}
.cardListPokemon:hover{
    background-image: linear-gradient(160deg, #00a2ff 0%, #4b928a 100%);
}

.cardListPokemon img:hover{
    padding: .1rem;
}
</style>