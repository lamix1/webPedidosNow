<template>
  <div class="d-flex justify-content-center align-items-center">
    
    <div class="card">
      <div class="card-header text-center py-3">
        <h5 class="mb-0 text-center">
          <strong>Cardápio</strong>
        </h5>
      </div>
      <div class="card-body">
        <div class="table-responsive">
          <table class="table table-hover text-nowrap">
            <thead>
        <tr>
          <th scope="col"><strong>ID</strong></th>
          <th scope="col"><strong>Nome</strong></th>
          <th scope="col"><strong>Peso</strong></th>
          <th scope="col"><strong>Preço</strong></th>
          <th scope="col"><strong>Categoria</strong></th>
          <!-- <th scope="col"><strong>Disponibilidade</strong></th> -->
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in produtos" :key="item.id">
                <th scope="row">{{ item.id }}</th>
                <td>{{ item.titulo}}</td>
                <td>{{ item.gramas }}</td>
                <td>R$ {{ item.preco }}</td>
                <td>{{ item.categoria }}</td>
                <!-- <input class="form-check-input" type="checkbox" v-model="item.disponivel" /></td> -->
              </tr>
      </tbody>
    </table>
  </div>
  </div>
</div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      produtos: [], 
    };
  },
  mounted() {
    this.getProdutos(); 
  },
  methods: {
    getProdutos() {
      axios.get('https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/produtos/')
        .then((response) => {
          this.produtos = response.data; 
        })
        .catch((error) => {
          console.error('Erro ao buscar os produtos:', error);
        });
    },
  },
};
</script>

<style scoped>

.card {
  width: 80%;
  height: 80%;
  border-radius: 30px;
}

.table {
  border-radius: 70px;
  width: 100%;
  height: 100%;
}
</style>