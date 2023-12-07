<template>
  <div class="container col-5 position-absolute top-50 start-50 translate-middle">
    <p class="text-center fs-2">Editar Cardápio</p>
    <form @submit.prevent="adicionarItem">
      <fieldset>
        <legend>Adicione itens</legend>
        <div class="mb-3">
          <input
            v-model="novoItem.titulo"
            type="text"
            id="disabledTextInput"
            class="form-control"
            placeholder="Nome"
          />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">$</span>
          <input
            v-model="novoItem.preco"
            type="text"
            class="form-control"
            aria-label="Amount (to the nearest dollar)"
          />
          <span class="input-group-text">.00</span>
        </div>

        <div class="mb-3">
          <select
            v-model="novoItem.categoria"
            class="form-select"
            aria-label="Default select example"
          >
            <option selected disabled>Categoria</option>
            <option v-for="categoria in categorias" :key="categoria.id" :value="categoria.id">{{categoria.descricao}}</option>
          </select>
        </div>
        <button type="submit" class="btn btn-primary float-end">Adicionar</button>
      </fieldset>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      novoItem: {
        titulo: '',
        preco: '',
        categoria: ''
      },
      categorias: []
    }
  },
  created() {
    axios.get('http://0.0.0.0:19003/api/categorias/').then((response) => {
      this.categorias = response.data
    })
  },
  methods: {
    adicionarItem() {
      axios
        .post('http://0.0.0.0:19003/api/produtos/', this.novoItem)
        .then((response) => {
          console.log('Item adicionado com sucesso!', response.data)
          this.novoItem = {
            titulo: '',
            preco: '',
            categoria: ''
          }
        })
        .catch((error) => {
          console.error('Erro ao adicionar item:', error)
        })
    }
  }
}
</script>
