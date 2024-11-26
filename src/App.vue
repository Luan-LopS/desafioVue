<script setup lang="ts">
  import { reactive } from "vue";
  import Header from "./components/Header.vue";
  import Footer from "./components/Footer.vue";
  import Main from "./components/Main.vue";

const equacao = reactive({
  valorA: '',
  valorB : '',
  operador : '',
  hitorico: []
})

function total (){
  const {valorA, valorB, operador, hitorico} = equacao
  const A: number = parseFloat(valorA)
  const B: number = parseFloat(valorB) 

  let resultado: number | string 
  
  if(!isNaN(A)){
    resultado = A
    
    switch (operador) {
    case '+':
      if(!isNaN(A) && !isNaN(B)){
        resultado = A + B
      }
      break      
  
    case '-':
      if(!isNaN(A) && !isNaN(B)){
        resultado =  A - B
      }
      break

    case '*':
      if(!isNaN(A) && !isNaN(B)){
        resultado =  A * B
      }
      break

    case '/':
      if(B === 0){
        resultado = 'Não divisivel'
      }else if(!isNaN(A) && !isNaN(B)){
        resultado =  A / B
      }
      break 
    }
    return resultado
  }
  
}
</script>

<template>
  <div class="container">
    <Header></Header>

    <Main :equacao="equacao" :total="total"></Main>

    <Footer></Footer>
  </div>

</template>

<style scoped  lang="sass">
   *
    margin: 0
    padding: 0
    box-sizing: border-box
    font-size: 20px
    margin: auto 0
    background: #0000

  .container
    margin: 0 auto
    max-width: 1200px
    width: 100%
    text-align: center
    display: block

</style>


