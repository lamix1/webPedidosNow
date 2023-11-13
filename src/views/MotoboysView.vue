<template>

        <p class="text-center fs-2">Gerenciar Motoboys</p>

        <div class="card card-adc col-4 d-flex justify-content-center align-items-center p-4 float-start">
        <legend class="titulo-adc text-center">Adicione Motoboy</legend>
        <form @submit.prevent="adicionarMotoboy">
        <fieldset>
          <div class="mb-3">
            <input v-model="novoMotoboy.nome" type="text" class="form-control" placeholder="Nome" required />
          </div>
  
          <div class="mb-3">
            <input v-model="novoMotoboy.telefone" type="text" class="form-control" placeholder="Telefone" required />
          </div>
  
          <div class="mb-3">
            <input v-model="novoMotoboy.email" type="email" class="form-control" placeholder="Email" required />
          </div>
  
          <button @click="adicionarMotoboy(motoboy.id)" class="btn btn-danger btn-sm">Adicionar Motoboy</button>
        </fieldset>
      </form>
      </div>


      <div class="card card-motoboys col-4 d-flex justify-content-center align-items-center p-4 float-start">
        
        <div class="card-nome text-center py-2">
                <legend class="titulo-tab text-center">Motoboys</legend>
            </div>

        <table class="table mt-4">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Nome</th>
          <th scope="col">Telefone</th>
          <th scope="col">Email</th>
          <th scope="col">Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="motoboy in motoboys" :key="motoboy.id">
          <th scope="row">{{ motoboy.id }}</th>
          <td>{{ motoboy.nome }}</td>
          <td>{{ motoboy.telefone }}</td>
          <td>{{ motoboy.email }}</td>
          <td>
            <button @click="excluirMotoboy(motoboy.id)" class="btn btn-danger btn-sm">Excluir</button>
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

.card-motoboys {
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
import axios from 'axios';
  
  export default {
    data() {
      return {
        motoboys: [],
        novoMotoboy: {
          nome: '',
          telefone: '',
          email: '',
        },
      };
    },
    mounted() {
      // Carregar motoboys ao iniciar
      this.carregarMotoboys();
    },
    methods: {
      carregarMotoboys() {
        axios
          .get('https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/motoboys/')
          .then((response) => {
            this.motoboys = response.data;
          })
          .catch((error) => {
            console.error('Erro ao carregar motoboys:', error);
          });
      },
      adicionarMotoboy() {
        axios
          .post('https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/motoboys/', this.novoMotoboy)
          .then((response) => {
            console.log('Motoboy adicionado com sucesso!', response.data);
            this.novoMotoboy = {
              nome: '',
              telefone: '',
              email: '',
            };
            this.carregarMotoboys(); // Recarregar a lista após adicionar
          })
          .catch((error) => {
            console.error('Erro ao adicionar motoboy:', error);
          });
      },
      excluirMotoboy(id) {
        axios
          .delete(`https://backendpedidosnow-dev-pabx.1.ie-1.fl0.io/api/motoboys/${id}/`)
          .then(() => {
            console.log('Motoboy excluído com sucesso!');
            this.carregarMotoboys(); // Recarregar a lista após excluir
          })
          .catch((error) => {
            console.error('Erro ao excluir motoboy:', error);
          });
      },
    },
  };
</script>