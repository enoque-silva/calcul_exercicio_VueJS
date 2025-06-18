<script setup>

import { ref, computed } from 'vue';

const numero1 = ref('');
const numero2 = ref('');
const operacao = ref('+');

const resultado = computed(() => {
  switch (operacao.value) {
    case '+':
      return numero1.value + numero2.value
    case '-':
      return numero1.value - numero2.value
    case '*':
      return numero1.value * numero2.value
    case '/':
      return numero2.value !== 0 ? (numero1.value / numero2.value) : 'Erro (divisão por zero)'
    default:
      return 0
  }
})

function limpar() {
  numero1.value = '';
  numero2.value = '';
  operacao.value = '+';
}

</script>

<template>
  <div class="container-sm">

    <header class="p-5 my-4 text-center">
      <h2 class="text-primary fs-3 m-0" style="--bs-text-opacity: .7;">Exercício</h2>
      <h1 class="fs-2">Calculadora Vue.JS</h1>
    </header>

    <input class="form-control" type="number" placeholder="Digite o primeiro número" v-model.number="numero1">

    <select class="form-select my-3 text-primary fw-bold" v-model="operacao">
      <option value="+">Somar (+)</option>
      <option value="-">Subtrair (-)</option>
      <option value="*">Multiplicar (*)</option>
      <option value="/">Dividir (/)</option>
    </select>

    <input class="form-control" type="number" placeholder="Digite o segundo número" v-model.number="numero2">
    
    <button class="btn btn-primary my-3 w-100" @click="limpar">Apagar</button>

    <div class="text-center mt-4">    
        <p class="text-primary fs-3 m-0">Resultado:</p>
        <h3 class="fs-1 text-primary p-0 m-0">{{ resultado }}</h3>         
    </div>

  </div>
</template>

<style scoped>
</style>
