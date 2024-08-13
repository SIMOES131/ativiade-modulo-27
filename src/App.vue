<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: 'soma',
});

const resultado = computed(() => {
  const { num1, num2, operacao } = estado;
  switch (operacao) {
    case 'soma':
      return num1 + num2;
    case 'subtracao':
      return num1 - num2;
    case 'multiplicacao':
      return num1 * num2;
    case 'divisao':
      return num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container">
    <h1> Calculadora Aritmética</h1>
  <div class="calculadora">
    <input type="number" v-model="estado.num1" placeholder="Número 1">
    <input type="number" v-model="estado.num2" placeholder="Número 2">
    <select v-model="estado.operacao">
      <option value="soma">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">*</option>
      <option value="divisao">/</option>
    </select>
    
    <p>Resultado: {{ resultado }}</p>
  </div>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
}

h1 {
  font-weight: bold;
  margin-bottom: 40px;
}

.calculadora {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 300px;
  margin: auto;
}
input, select {
  padding: 5px;
  font-size: 20px;
  text-align: center;
  font-weight: bold;
}
p {
  font-size: 25px;
  font-weight: bold;
}
</style>
