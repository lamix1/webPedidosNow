<template>
  <div>
    <div class="container">
      <div v-for="(pedido, index) in pedidosFiltrados" :key="index">
        <div class="card">
          <div class="card-content">
            <p class="mesa">Mesa # {{ pedido.mesa }}</p>
            <p class="cliente">Cliente: {{ pedido.cliente }}</p>
            <p class="total">Total: R$ {{ pedido.total.toFixed(2) }}</p>
            <p class="status">Status: {{ pedido.status }}</p>
          </div>
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
      pedidos: [],
    };
  },
  computed: {
    pedidosFiltrados() {
      return this.pedidos.filter((pedido) => pedido.status === 'PRODUCAO');
    },
  },
  created() {
    axios
      .get('http://191.52.55.129:19002/api/pedidos/')
      .then((response) => {
        this.pedidos = response.data;
      })
      .catch((error) => {
        console.error('Erro ao buscar os pedidos:', error);
      });
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  width: 100%;
}

.card {
  width: 50rem;
  height: 15rem;
  margin-bottom: 10px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 20px;
  box-sizing: border-box;
}

.mesa {
  font-size: 24px;
  font-weight: bold;
}

.status {
  font-size: 18px;
  color: #d32f2f;
}

.cliente {
  font-size: 18px;
}

.total {
  font-size: 16px;
  margin-top: 5px;
}
</style>