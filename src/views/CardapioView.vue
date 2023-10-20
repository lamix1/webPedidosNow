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
          <th scope="col"><strong>Disponibilidade</strong></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Porção de Batata Frita</td>
          <td>500g</td>
          <td>R$25,00</td>
          <td>Porção</td>
          <td><input class="form-check-input" type="checkbox" /></td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Chawarma de Frango</td>
          <td>250g</td>
          <td>R$50,00</td>
          <td>Chawarma</td>
          <td><input class="form-check-input" type="checkbox" /></td>
        </tr>
        <tr>
          <th scope="row">8</th>
          <td>Fanta em Lata</td>
          <td>350ml</td>
          <td>R$5,00</td>
          <td>Bebida</td>
          <td><input class="form-check-input" type="checkbox" /></td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Chawarma de Carne</td>
          <td>150g</td>
          <td>R$20,00</td>
          <td>Chawarma</td>
          <td><input class="form-check-input" type="checkbox" /></td>
        </tr>
        <tr>
          <th scope="row">6</th>
          <td>Porção de Carne</td>
          <td>150g</td>
          <td>R$30,00</td>
          <td>Porção</td>
          <td><input class="form-check-input" type="checkbox" /></td>
        </tr>
        <tr>
          <th scope="row">7</th>
          <td>Coca-Cola em Lata</td>
          <td>350ml</td>
          <td>R$5,00</td>
          <td>Bebida</td>
          <td><input class="form-check-input" type="checkbox" /></td>
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