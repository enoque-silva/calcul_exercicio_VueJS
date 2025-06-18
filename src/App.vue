<script setup>

import { ref, computed } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
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

</script>

<template>
  <div class="container-sm">

    <header class="p-5 my-4 text-center">
      <div class="text-primary fs-3" style="--bs-text-opacity: .7;">Exercício</div>
      <h1 class="fs-2">Calculadora Vue.JS</h1>
    </header>

    <input class="form-control" type="number" placeholder="Digite o primeiro número" v-model.number="numero1">

    <select class="form-select my-3" v-model="operacao">
      <option value="+">Somar (+)</option>
      <option value="-">Subtrair (-)</option>
      <option value="*">Multiplicar (*)</option>
      <option value="/">Dividir (/)</option>
    </select>

    <input class="form-control" type="number" placeholder="Digite o segundo número" v-model.number="numero2">

    <div class="mt-3">
      <div class="fs-4 text-primary">Resultado: {{ resultado }}</div>
    </div>
  </div>
</template>

<style scoped>
</style>
