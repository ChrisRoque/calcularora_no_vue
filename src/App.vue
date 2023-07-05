<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  recebe: 0,
  filtro: 0,
  
})

function alteraValorNum1(evento){
  estado.num1 = evento.target.value;
}

function alteraValorNum2(evento){
  estado.num2 = evento.target.value;
}

const soma = () => {
  const {num1, num2} = estado;
  return estado.recebe = num1 + num2;
}
const sub = () => {
  const {num1, num2} = estado;
  return estado.recebe = num1 - num2;
}
const divi = () => {
  const {num1, num2} = estado;
  return estado.recebe = num1 / num2;
}
const mult = () => {
  const {num1, num2} = estado;
   return estado.recebe = num1 * num2;
}

const filtroFuncao = () => {
  const { filtro } = estado;

    switch (filtro){
      case "+":
        return `O valor da soma é: ${soma()}`;
      case "-":
        return `O valor da subtração é: ${sub()}`;
      case "÷":
        return `O valor da divisão é: ${divi()}`;
      case "*":
        return `O valor da multiplicação é: ${mult()}`;
      default:
        return estado.filtro;
    }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light t-align-center">
      <h1>Calculadora</h1>
    </header>
    
    <div class="display">
      <input @keyup="alteraValorNum1" type="nuber" placeholder="Digite primeiro numero">
      <input @keyup="alteraValorNum2" type="nuber" placeholder="Digite segundo numero">

      <select  @change="evento => estado.filtro = evento.target.value" >
        <option value="Oparaçãr">Operador</option>
        <option  value="+" >+</option>
        <option  value="-">-</option>
        <option  value="÷">÷</option>
        <option  value="*">*</option>
      </select>
      
    </div>
    
    <div class="tela">
      <span> {{ filtroFuncao() }} </span>
    </div>
  </div>
</template>

<style scoped>
.container{
  margin-top: 5%;
  width: 480px;
  max-width: 100%;
  text-align: center;
}


.display{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: .2em;
}

.tela {
  max-width: 100%;
  background-color:#ccc ;
  font-size: 24px;
  margin-top: 16px;
  
}

</style>
