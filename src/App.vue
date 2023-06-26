<script setup>
import { computed, reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  valor1: 0,
  valor2: 0,
  operacao: ''
})

const somar = (valor1, valor2) => {
  return valor1 + valor2
}

const subtrair = (valor1, valor2) => {
  return valor1 - valor2
}

const dividir = (valor1, valor2) => {
  return valor1 / valor2
}

const multiplicar = (valor1, valor2) => {
  return valor1 * valor2
}

const resultado = computed(() => {
  const valor1 = parseInt(estado.valor1)
  const valor2 = parseInt(estado.valor2)
  const operacao = estado.operacao
  console.log(operacao)

  switch (operacao) {
    case 'subtracao':
      return subtrair(valor1, valor2)
    case 'multiplicacao':
      return multiplicar(valor1, valor2)
    case 'divisao':
      return dividir(valor1, valor2)
    default:
      return somar(valor1, valor2)
  }

}

)


</script>

<template>
  <div class="container">
    <Cabecalho />
    <Formulario
    :valor1="estado.valor1"
    :valor2="estado.valor2"
    :captura-valor1="event => estado.valor1 = event.target.value" 
    :captura-valor2="event => estado.valor2 = event.target.value"
    :resultado="resultado" 
    :operacao="estado.operacao"
    :define-operacao="event => estado.operacao = event.target.value" />
  </div>
</template>

<style scoped></style>
