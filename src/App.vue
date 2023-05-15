<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: 'soma',
  resultado: 0,
})

const calcular = () => {
  const { operacao } = estado;

  switch (operacao) {
    case 'soma':
      return estado.resultado = Number(estado.numero1) + Number(estado.numero2);
    case 'subtrair':
      return estado.resultado = Number(estado.numero1) - Number(estado.numero2);
    case 'multiplicar':
      return estado.resultado = Number(estado.numero1) * Number(estado.numero2);
    case 'dividir':
      return estado.resultado = Number(estado.numero1) / Number(estado.numero2);
    default:
      return 0;
  }

}

</script>

<template>
<div class="container">
  <header class="p-5">
    <h1>Calculadora Aritmética:</h1>
  </header>
  <form>
    <div class="row">
      <div class="col-4">
        <label for="numero1">Número 1:</label>
        <input class="form-control" id="numero1" type="number" @change="evento => estado.numero1 = evento.target.value">
      </div>
      <div class="col-4">
        <label for="numero2">Número 2:</label>
        <input class="form-control" id="numero2" type="number" @change="evento => estado.numero2 = evento.target.value">
      </div>
    </div>
    <div class="row">
      <div class="col-8">
        <label for="operacao">Operação:</label>
        <select class="form-control" id="operacao" @change="evento => estado.operacao = evento.target.value">
          <option value="soma">+</option>
          <option value="subtrair">-</option>
          <option value="multiplicar">*</option>
          <option value="dividir">/</option>
        </select>
      
        <label for="resultado">Resultado:</label>
        <input class="form-control" id="resultado" type="number" readonly :value="calcular()">
      </div>
    </div>
  </form>
</div>
</template>

<style scoped>

</style>
