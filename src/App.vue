<script setup>
import { ref, computed } from "vue";
const name = 'vue dinamico';

const counter = ref(0);
const numfav = ref([]);


const increment = () => {
  counter.value++;
}

const decrement = () => {
 counter.value--;
};

const resetValue = () => {
  counter.value = 0;
};

const addValue = () => {
  numfav.value.push(counter.value)
}

const bloquear= computed (() => { const number = numfav.value.find((num) => num === counter.value);
    return number || number === 0;
});

const classCounter = computed(() =>
{
  if (counter.value === 0) {
    return 'zero'
  }
  if (counter.value > 0 ) {
    return 'positivo'
  }
  if (counter.value < 0){
    return 'negativo'
  }
});
 

</script>

<template>
  <div class="container text-center mt-3">
    <h1> Adios casino montecarlo</h1>
 <h2 :class= "classCounter">
  {{ counter }}</h2>
  <div class="btn-group">
    <button @click="increment" class="btn btn-success">Click incremetar</button>
     <button @click="decrement" class="btn btn-danger">Decrement</button>
    <button @click="resetValue" class="btn btn-secondary">Clic reset</button>
    <button @click="addValue" :disabled="bloquear" class="btn btn-primary">Add</button>
  </div>
  <ul class="list-group mt-4">
  <li v-for="(numerof) in numfav">
    {{ numerof }}

  </li>
 </ul>
  </div>
 
</template>

<style>
.negativo{
  color:red;
}
.positivo{
  color:green;
}
.zero {
  color:aqua;
}

</style>
