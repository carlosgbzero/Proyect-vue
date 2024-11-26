<script setup lang="ts">
  import { ref, computed } from 'vue';
  

  class Registro{
     private  monto: number;
     private saldoActual: number; 
    constructor(monto:number, saldoActual:number){
      this.monto = monto;
      this.saldoActual = saldoActual
    }

    getMonto(){
      return this.monto;
    }

    getSaldoActual(){
      return this.saldoActual;
    }
  }

  const ahorro = ref<number>(400);
  const registros =  ref<Registro[]>([])

  const depositar = () =>{
    ahorro.value += 100;
    registros.value.push(new Registro(100, ahorro.value))
  }

  const retirar = () => {
    ahorro.value -= 100;
    registros.value.push(new Registro(-100, ahorro.value))
  }

  const estado = computed (()=>{
    let clase = 'conDinero'
    if(ahorro.value < 800)
      clase = 'sinDinero'
    return clase;
    })

  
    const bloquearRetiro = computed (()=>{
    let est:boolean = false;
    if(ahorro.value == 0)
      est = !est;
    return est;
    })
    
    
   
    const revertirArray = computed (()=>{ 
    return registros.value.slice().reverse();
    })

  

</script>

<template>
  <h3 v-bind:class="estado">Mis Ahorros:  {{ ahorro }}</h3>
  <button @click="depositar" class="btn btn-primary"> Depositar </button>
  <button @click="retirar" :disabled="bloquearRetiro" class="btn btn-primary"> Retirar </button>
  <h4>Registro</h4>
  <ul>
    <li v-for="(i, index) in revertirArray" :key="index">
      <span v-if="i.getMonto() < 0">
        Retiro ||
      </span>
      <span v-else>
        Deposito ||
      </span>
      {{ i.getMonto() }} || {{ i.getSaldoActual() }}
    </li>
  </ul>
</template>

<style scoped>
  h3{
    font-size: 50px;
  }

  button{
    
    margin-left: 5px;
  }
  .conDinero{
    color: green;
    font-style: normal;
  }
  .sinDinero{
    color: red;
    font-style: oblique;
  }

</style>
