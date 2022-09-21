<script>
  import axios from "axios";
    export default {
      data() {
        return {
          cep: "",
          endereço: {},
        };
      },
      methods: {
        async buscar() {
         const url = 'https://www.viacep.com.br/ws/$(this.cep)/json';
         const res = await axios.get(url); 
         this.endereço = res.data;
        }
      },
    };
  </script>
<template>
    <form @submit.prevent="buscar">
      <input type="text" v-model="cep" placeholder="CEP:">
      <button type="submit">Procurar</button>
    </form>
    <div class="end">
      <p>Rua: {{endereço.logradouro}}</p>
      <p>Número: {{endereço.numero}}</p>
      <p>Bairro: {{endereço.bairro}}</p>
      <p>Rua: {{endereço}}</p>
      <p>Rua: {{endereço.lagradouro}}</p>
    </div>
</template>