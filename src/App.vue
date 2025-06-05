    <script setup>
    import { ref, computed } from 'vue';
    
    const numero1 = ref(0);
    const numero2 = ref(0);
    const operacao = ref('soma');
    
    const resultado = computed(() => {
      switch(operacao.value) {
        case 'soma':
          return numero1.value + numero2.value;
        case 'subtracao':
          return numero1.value - numero2.value;
        case 'multiplicacao':
          return numero1.value * numero2.value;
        case 'divisao':
          return numero2.value !== 0 
            ? (numero1.value / numero2.value).toFixed(2) 
            : 'Erro: divisão por zero';
        default:
          return 0;
      }
    });
    </script>


<template>
  <div class="calculadora">
    <h1>Calcule com VueJS</h1>
    
    <div class="inputs">
      <input type="number" v-model.number="numero1" placeholder="Primeiro número">
      <select v-model="operacao">
        <option value="soma">+</option>
        <option value="subtracao">-</option>
        <option value="multiplicacao">×</option>
        <option value="divisao">÷</option>
      </select>
      <input type="number" v-model.number="numero2" placeholder="Segundo número">
    </div>
    <div class="resultado">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>


<style scoped>
.calculadora {
  max-width: 500px;
  margin: 200px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #000000;
  border-radius: 24px;
}

.inputs {
  display: flex;
  gap: 10px;
  align-items: center;
  justify-content: center;
  margin: 20px 0;
}

input, select {
  padding: 8px;
  font-size: 16px;
}

.resultado {
  margin-top: 20px;
  font-size: 18px;
  color: #000000;
}
</style>