<template>
  <div class="d-flex justify-content-center align-items-center">
    
      <div class="card">
        <div class="card-header text-center py-3">
          <h5 class="mb-0 text-center">
            <strong>Pedidos Abertos</strong>
          </h5>
        </div>
        <div class="card-body">
          <div class="table-responsive">
            <table class="table table-hover text-nowrap">
              <thead>
                <tr>
                  <th scope="col"><strong>Funcionário</strong></th>
                  <th scope="col"><strong>ID</strong></th>
                  <th scope="col"><strong>Nome</strong></th>
                  <th scope="col"><strong>Mesa</strong></th>
                  <th scope="col"><strong>Pedido</strong></th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Maria</td>
                  <td>2</td>
                  <td>Eduardo</td>
                  <td>10</td>
                  <td>Chawarma de Frango</td>
                </tr>
                <tr>
                  <td>Paulo</td>
                  <td>3</td>
                  <td>Telma</td>
                  <td>20</td>
                  <td>Porção de Calabresa</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    
  </div>

</template>

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