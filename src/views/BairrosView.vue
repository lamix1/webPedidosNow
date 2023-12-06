<template>
    <p class="text-center fs-2">Gerenciar Bairros</p>
  
    <div class="card card-adc col-4 d-flex justify-content-center align-items-center p-4 float-start">
      <legend class="titulo-adc text-center">Adicione o Bairro</legend>
      <form @submit.prevent="adicionarBairro">
        <fieldset>
          <div class="mb-3">
            <input
              v-model="novoBairro.nome"
              type="text"
              class="form-control"
              placeholder="Nome"
              required
            />
          </div>
  
          <div class="input-group mb-3">
          <span class="input-group-text">$</span>
          <input
            v-model="novoBairro.preco_entrega"
            type="text"
            class="form-control"
            aria-label="Amount (to the nearest dollar)"
          />
          <span class="input-group-text">.00</span>
        </div>
  
          <button @click="adicionarBairro(bairro.id)" class="btn btn-danger btn-sm">
            Adicionar Bairro
          </button>
        </fieldset>
      </form>
    </div>
  
    <div
      class="card card-bairros col-4 d-flex justify-content-center align-items-center p-4 float-start"
    >
      <div class="card-nome text-center py-2">
        <legend class="titulo-tab text-center">Bairros</legend>
      </div>
  
      <table class="table mt-4">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Nome</th>
            <th scope="col">Preço</th>
            <th scope="col">Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="bairro in bairros" :key="bairro.id">
            <th scope="row">{{ bairro.id }}</th>
            <td>{{ bairro.nome }}</td>
            <td>{{ bairro.preco_entrega }}</td>
            <td>
              <button @click="excluirBairro(bairro.id)" class="btn btn-danger btn-sm">
                Excluir
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  <style>
  .card-adc {
    width: 40rem;
    height: 20rem;
    margin-left: 10%;
  }
  
  .card-bairros {
    width: 40rem;
    height: 20rem;
    margin-left: 10%;
  }
  
  .titulo-adc {
    margin-top: 10px;
  }
  
  .titulo-tab {
    margin-top: 1px;
  }
  </style>
  
  <script>
  import axios from 'axios'
  
  export default {
    data() {
      return {
        bairros: [],
        novoBairro: {
          nome: '',
          preco_entrega: '',
        }
      }
    },
    mounted() {
      this.carregarBairros()
    },
    methods: {
      carregarBairros() {
        axios
          .get('https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/bairros/')
          .then((response) => {
            this.bairros = response.data
          })
          .catch((error) => {
            console.error('Erro ao carregar bairros:', error)
          })
      },
      adicionarBairro() {
        axios
          .post('https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/bairros/', this.novoBairro)
          .then((response) => {
            console.log('Bairro adicionado com sucesso!', response.data)
            this.novoBairro = {
              nome: '',
              preco_entrega: '',
            }
            this.carregarBairros()
          })
          .catch((error) => {
            console.error('Erro ao adicionar bairro:', error)
          })
      },
      excluirBairro(id) {
        axios
          .delete(`https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/bairros/${id}/`)
          .then(() => {
            console.log('Bairro excluído com sucesso!')
            this.carregarBairros()
          })
          .catch((error) => {
            console.error('Erro ao excluir bairro:', error)
          })
      }
    }
  }
  </script>