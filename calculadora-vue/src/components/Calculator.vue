<template>
  <div class="calculator">
    <h2>Calculadora Aritmética</h2>

    <div class="inputs">
      <input 
        type="number" 
        v-model.number="num1" 
        placeholder="Digite o primeiro número"
      />

      <select v-model="operacao">
        <option value="+">Adição (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (*)</option>
        <option value="/">Divisão (/)</option>
      </select>

      <input 
        type="number" 
        v-model.number="num2" 
        placeholder="Digite o segundo número"
      />
    </div>

    <h3>Resultado: {{ resultado }}</h3>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const num1 = ref(0)
const num2 = ref(0)
const operacao = ref('+')

const resultado = computed(() => {
  if (operacao.value === '+') return num1.value + num2.value
  if (operacao.value === '-') return num1.value - num2.value
  if (operacao.value === '*') return num1.value * num2.value
  if (operacao.value === '/') {
    return num2.value !== 0 ? (num1.value / num2.value).toFixed(2) : 'Erro: Divisão por zero'
  }
  return ''
})
</script>
