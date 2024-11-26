<script setup lang="ts">
import { computed } from 'vue';

    const props  = defineProps(['equacao', 'total'])

    const resultado = computed(()=>{
        return props.total()
    })
</script>

<template>
  <div class="container">
    <main>
      <p>Insira nos campos a baixo valor, mais tipo de conta, mais valor para realizar a sua equação</p>

      <form @submit.prevent="props.total()">
        <input type="text" :class="{'invalido': isNaN(props.equacao.valorA)}" v-model="props.equacao.valorA"  placeholder="ValorA"  required/>

        <select required v-model="props.equacao.operador">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="/">/</option>
          <option value="*">*</option>
        </select>

        <input type="text" :class="{'invalido': isNaN(props.equacao.valorB)}"  v-model="props.equacao.valorB" required placeholder="ValorB">
        <p> = </p>
        <p id="total" > {{ resultado }}</p> 

      </form>
    </main>
  </div>

</template>

<style scoped  lang="sass">
    main
      padding: 30px

      p
        padding: 25px
        font-size: 1.6rem
        white-space: nowrap

      form
        select
          width:60px
          margin: 0 12px 012px

        input
          width: 300px
          padding-left: 5px

          &.invalido
            border: red 2px solid
            
        p
          display: inline-block

        #total
          display: block
          color: green
          font-size: 40px

</style>


