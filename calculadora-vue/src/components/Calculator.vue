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
<style scoped>
.calculator {
  max-width: 400px;
  margin: 30px auto;
  padding: 20px;
  text-align: center;
  border-radius: 10px;
  background: #f4f4f4;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
.inputs {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}
input, select {
  flex: 1;
  padding: 8px;
  font-size: 16px;
}
</style>




