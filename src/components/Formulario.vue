<script setup>

const props = defineProps(['valor1', 'valor2', 'capturaValor1', 'capturaValor2', 'resultado', 'defineOperacao'])
</script>

<template>
    <form class="row">
        <div class="col-3">
            <label class="d-block">Digite o primeiro número</label>
            <input :value="valor1" @change="props.capturaValor1"  class="w-100" type="number" required>
        </div>
        <div class="col-3">
            <label class="d-block">Digite o segundo número</label>
            <input :value="valor2" @change="props.capturaValor2"  class="w-100" type="number"  required>
        </div>
        <div class="col-2">
            <label class="d-block">Escolha a operação</label>
            <select @change="props.defineOperacao" class="w-100">
                <option value="soma">Soma</option>
                <option value="subtracao">Subtração</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
            </select>
        </div>
        <div class="col-4">
            <label class="d-block">Resultado</label>

            <input v-if="!props.resultado" class="w-100" type="text" required value=0>
            <input v-else-if="props.resultado == 'Infinity'" class="w-100" type="text" required value="Não é possível dividir por zero">
            <input v-else class="w-100" type="text" required :value="props.resultado">
        </div>
    </form>
</template>