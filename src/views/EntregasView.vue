<template>
    <div>
      <h2>Nova Entrega</h2>
  
      <form @submit.prevent="criarEntrega">
        <div class="mb-3">
          <label for="cliente" class="form-label">Nome do Cliente</label>
          <input v-model="novaEntrega.cliente" type="text" class="form-control" id="cliente" required>
        </div>
  
        <div class="mb-3">
          <label for="bairro" class="form-label">Bairro</label>
          <select v-model="novaEntrega.bairro" class="form-select" id="bairro" required>
            <option v-for="bairro in bairros" :key="bairro.id" :value="bairro.id">{{ bairro.nome }}</option>
          </select>
        </div>
  
        <div class="mb-3">
          <label for="motoboy" class="form-label">Motoboy</label>
          <select v-model="novaEntrega.motoboy" class="form-select" id="motoboy" required>
            <option v-for="motoboy in motoboys" :key="motoboy.id" :value="motoboy.id">{{ motoboy.nome }}</option>
          </select>
        </div>
  
        <div class="mb-3">
          <label for="produtos" class="form-label">Produtos</label>
          <div class="table-responsive m-3">
            <table class="table table-hover text-nowrap">
              <thead>
                <tr>
                  <th scope="col"><strong>ID</strong></th>
                  <th scope="col"><strong>Nome</strong></th>
                  <th scope="col"><strong>Preço</strong></th>
                  <th scope="col"><strong>Categoria</strong></th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="produto in produtos" :key="produto.id">
                  <td>
                    <input
                      type="checkbox"
                      :id="'produto_' + produto.id"
                      v-model="novaEntrega.produtos"
                      :value="produto.id"
                    />
                  </td>
                  <td>{{ produto.titulo }}</td>
                  <td>R$ {{ produto.preco }}</td>
                  <td>{{ produto.categoria }}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
  
        <div class="mb-3">
          <label for="endereco" class="form-label">Endereço</label>
          <textarea v-model="novaEntrega.endereco" class="form-control" id="endereco" required></textarea>
        </div>
  
        <button type="submit" class="btn btn-primary">Criar Entrega</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        novaEntrega: {
          cliente: '',
          bairro: '',
          motoboy: '',
          produtos: [],
          endereco: '',
        },
        bairros: [],
        motoboys: [],
        produtos: [],
      };
    },
    created() {
      this.carregarBairros();
      this.carregarMotoboys();
      this.carregarProdutos();
    },
    methods: {
      carregarBairros() {
        axios.get('http://0.0.0.0:19003/api/bairros/')
          .then((response) => {
            this.bairros = response.data;
          })
          .catch((error) => {
            console.error('Erro ao carregar bairros:', error);
          });
      },
      carregarMotoboys() {
        axios.get('http://0.0.0.0:19003/api/motoboys/')
          .then((response) => {
            this.motoboys = response.data;
          })
          .catch((error) => {
            console.error('Erro ao carregar motoboys:', error);
          });
      },
      carregarProdutos() {
        axios.get('http://0.0.0.0:19003/api/produtos/')
          .then((response) => {
            this.produtos = response.data;
          })
          .catch((error) => {
            console.error('Erro ao carregar produtos:', error);
          });
      },
      criarEntrega() {
  // Mapeia a lista de produtos para extrair apenas os IDs
  const produtosIds = this.novaEntrega.produtos.map(produto => produto);

  // Cria uma cópia dos dados da entrega excluindo a lista de produtos
  const dadosEntrega = { ...this.novaEntrega, produtos: produtosIds };

  axios.post('http://0.0.0.0:19003/api/entregas/', dadosEntrega)
    .then((response) => {
      console.log('Entrega criada com sucesso!', response.data);
      this.novaEntrega = {
        cliente: '',
        bairro: '',
        motoboy: '',
        produtos: [],
        endereco: '',
      };
    })
    .catch((error) => {
      console.error('Erro ao criar entrega:', error);
    });
},
    },
  };
  </script>