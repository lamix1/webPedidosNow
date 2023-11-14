<template>
  <div class="d-flex justify-content-center align-items-center">
    <div class="card">
      <div class="card-header text-center py-3 bg-danger text-light">
        <h5 class="mb-0 text-center">
          <strong>Cardápio</strong>
        </h5>
      </div>
      <div class="card-body m-3">
        <div class="form-group">
          <input
            type="text"
            class="form-control"
            id="searchInput"
            v-model="searchTerm"
            placeholder="Busca por nome"
          />
        </div>

        <div class="table-responsive m-3">
          <table class="table table-hover text-nowrap">
            <thead>
              <tr>
                <th scope="col"><strong>ID</strong></th>
                <th scope="col"><strong>Nome</strong></th>
                <th scope="col"><strong>Peso</strong></th>
                <th scope="col"><strong>Preço</strong></th>
                <th scope="col"><strong>Categoria</strong></th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in filteredProdutos" :key="item.id">
                <th scope="row">{{ item.id }}</th>
                <td>{{ item.titulo }}</td>
                <td>{{ item.gramas }}</td>
                <td>R$ {{ item.preco }}</td>
                <td>{{ item.categoria }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      produtos: [],
      searchTerm: ''
    }
  },
  computed: {
    filteredProdutos() {
      return this.produtos.filter((item) =>
        item.titulo.toLowerCase().includes(this.searchTerm.toLowerCase())
      )
    }
  },
  mounted() {
    this.getProdutos()
  },
  methods: {
    getProdutos() {
      axios
        .get('https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/produtos/')
        .then((response) => {
          this.produtos = response.data
        })
        .catch((error) => {
          console.error('Erro ao buscar os produtos:', error)
        })
    }
  }
}
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
