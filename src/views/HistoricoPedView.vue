<template>
  <div>
    <div class="container">
      <div v-for="(pedido, index) in pedidosFiltrados" :key="index">
        <div class="card" @click="showModal(pedido)">
          <div class="card-content">
            <p class="mesa">Mesa # {{ pedido.mesa }}</p>
            <p class="cliente">Cliente: {{ pedido.cliente }}</p>
            <p class="total">Total: R$ {{ pedido.total.toFixed(2) }}</p>
            <p class="status">Status: {{ pedido.status }}</p>
          </div>
        </div>
      </div>
    </div>

    <div v-if="selectedPedido" class="modal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <h2>Detalhes do Pedido</h2>
        <p><strong>Mesa:</strong> {{ selectedPedido.mesa }}</p>
        <p><strong>Cliente:</strong> {{ selectedPedido.cliente }}</p>
        <p><strong>Total:</strong> R$ {{ selectedPedido.total.toFixed(2) }}</p>
        <p><strong>Status:</strong> {{ selectedPedido.status }}</p>
        <h3>Itens do Pedido</h3>
        <ul>
          <li v-for="(item, itemIndex) in selectedPedido.itens" :key="itemIndex">
            {{ item.produto.titulo }} x {{ item.quantidade }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      pedidos: [],
      selectedPedido: null
    }
  },
  computed: {
    pedidosFiltrados() {
      return this.pedidos.filter((pedido) => pedido.status == 'Pago')
    }
  },
  methods: {
    showModal(pedido) {
      this.selectedPedido = pedido
      const modal = document.querySelector('.modal')
      modal.style.display = 'block'
    },
    closeModal() {
      this.selectedPedido = null
      const modal = document.querySelector('.modal')
      modal.style.display = 'block'
    }
  },
  created() {
    axios
      .get('http://0.0.0.0:19003/api/pedidos/')
      .then((response) => {
        this.pedidos = response.data
      })
      .catch((error) => {
        console.error('Erro ao buscar os pedidos:', error)
      })
  }
}
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
  border-left: 6px solid #d32f2f;
}
.card:hover {
  top: -4px;
  box-shadow: 0 4px 4px #999;
  transition: all 0.2s ease-in-out;
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

.modal {
  display: none;
  position: fixed;
  z-index: 1;
  left: 50%;
  top: 50%;
  width: 55rem;
  height: 25rem;
  transform: translate(-50%, -50%);
  border-radius: 10px;
  box-shadow: black;
}

.modal-content {
  background-color: #fff;
  padding: 20px;
  width: 100%;
  height: 100%;
  border-radius: 8px;
}

.close {
  position: absolute;
  top: 0;
  right: 0;
  padding: 10px;
  cursor: pointer;
}
</style>
