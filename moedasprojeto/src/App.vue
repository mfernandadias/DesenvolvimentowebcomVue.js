<template>
 
  <div class="container grid-lg my-2 py2 text-dark">

    <div class="card">

      <div class="card-header">
        <div class="h4"> Exibindo as Moedas </div>
      </div>
     
      <div class="card-body">

        <HelloWorld :quotes="quotes" />


      </div>



    </div>

  </div>


</template>

<script>

import HelloWorld from './components/HelloWorld.vue';
import api from '@/servidor/api.js';
import { onMounted, reactive, toRefs } from 'vue';


export default {
  name: 'App',

  components: {
    HelloWorld
 },

// expor os dados da nossa API no nosso component
 setup() {

   const data = reactive ({  // dados reativos

    quotes: { },

   });

   onMounted( async() => {

     const response = await api.all();
     data.quotes = response.data;


   })

   return { ...toRefs(data) }

 }

}
</script>

<style>

  .h4 {
    text-align: center;
    margin-bottom: 10px;;
  }

  .card {
    box-shadow:  inset 0 0 1em rgb(129, 94, 158), 0 0 1em rgb(100, 67, 119);
  }


</style>