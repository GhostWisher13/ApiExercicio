<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const res = await axios.get(url);
      this.endereco = res.data;  
    },
  },
};
</script>

<template>
  <main>
  <div class="container">
    <h1>Busca CEP</h1>
    <form @submit.prevent="buscar">
      <input type="text" placeholder="CEP" v-model="cep" />
      <button type="submit">Buscar</button>
    </form>
    <form class="end">
      <label for="rua">Rua</label>
      <input type="text" v-model="endereco.logradouro" />
      <label for="rua">Bairro</label>
      <input type="text" v-model="endereco.bairro" />
      <label for="rua">Cidade</label>
      <input type="text" v-model="endereco.localidade" />
      <label for="rua">Estado</label>
      <input type="text" v-model="endereco.uf" />
      <label for="rua">DDD</label>
      <input type="text" v-model="endereco.ddd" />
    </form>
  </div>
  </main>
</template>
<style>
.container {
  background-color: #8c41aab2;
  padding: 10px;
  border-color: black;
}
.end {
  display: flex;
  flex-direction: column;
}
</style>
