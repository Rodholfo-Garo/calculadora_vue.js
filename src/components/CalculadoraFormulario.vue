
<template>
    <div class="container">
        <fieldset class="border border-primary rounded p-5 mb-3">
            <legend class="form-label text-center">
                <h2>Calculadora</h2>
            </legend>

            <div class="row align-items-center ">
                <div class="col">
                    <h3>Escolha a Operação que deseja fazer!</h3>
                </div>

                <div class="col-md-3">
                    <select v-model="estado.operacao" @change="calculaResultado"
                        class="form-control fs-5 badge text-bg-primary">
                        <option value="" disabled selected hidden>Operação</option>
                        <option value="adicao"> Soma +</option>
                        <option value="subtracao">Subtração -</option>
                        <option value="divisao">Divisão /</option>
                        <option value="multiplicacao">Multiplicação *</option>
                    </select>
                </div>
            </div>

            <div class="mb-3">
                <label class="form-label" for="numero1">Insira o primeiro número:</label>
                <input v-model="estado.numero1" class="form-control" type="number" name="" id="numero1"
                    placeholder="Insira o primeiro número">
            </div>

            <div class="mb-3">
                <label class="form-label" for="numero2">Insira o segundo número:</label>
                <input v-model="estado.numero2" class="form-control" type="number" name="" id="numero2"
                    placeholder="Insira o segundo número">
            </div>

            <div class="mb-3">
                <label class="form-label" for="resultado">Resultado:</label>
                <input v-bind:class="{ 'resultado-negativo': estado.resultado < 0 }" v-model="estado.resultado"
                    class="form-control" type="number" name="" id="resultado">
            </div>

            <button class="btn btn-danger" @click="limpaCampos()">Limpar</button>
        </fieldset>
    </div>
</template>
  
<script setup>
import { reactive } from 'vue';

const estado = reactive({
    operacao: '',
    numero1: '',
    numero2: '',
    resultado: '',
});

const calculaResultado = () => {
    switch (estado.operacao) {
        case 'adicao':
            estado.resultado = estado.numero1 + estado.numero2;
            break;
        case 'subtracao':
            estado.resultado = estado.numero1 - estado.numero2;
            break;
        case 'multiplicacao':
            estado.resultado = estado.numero1 * estado.numero2;
            break;
        case 'divisao':
            estado.resultado = estado.numero1 / estado.numero2;
            break;
        default:
            estado.resultado = 0;
    }
};

const limpaCampos = () => {
    estado.operacao = '';
    estado.numero1 = '';
    estado.numero2 = '';
    estado.resultado = '';
};
</script>
  
<style scoped>
.resultado-negativo {
    border: 1px solid red;
}</style>
  