<template>
  <div class="card card-adc col-4 d-flex justify-content-center align-items-center p-4 float-start">
    <form>
      <fieldset>
        <legend>Adicionar Funcionários</legend>
        <form>
      <div class="mb-3">
        <input
          type="text"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
          placeholder="Nome"
        />
      </div>
      <div class="mb-3">
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
          placeholder="Email"
        />
      </div>
      <div class="mb-3">
        <input
          type="password"
          class="form-control"
          id="exampleInputPassword1"
          placeholder="Senha"
        />
      </div>
      <button type="submit" class="btn btn-primary">Adicionar</button>
    </form>
        </fieldset>
    </form>
  </div>

  <div class="card card-funcionarios float-end">
        <div class="card-header text-center py-3">
          <h5 class="mb-0 text-center">
            <strong>Funcionários</strong>
          </h5>
        </div>
        <div class="card-body">
          <div class="table-responsive">
            <table class="table table-hover text-nowrap">
              <thead>
                <tr>
                  <th scope="col"><strong>Nome</strong></th>
                  <th scope="col"><strong>Email</strong></th>
                  <th scope="col"><strong>Login</strong></th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Maria</td>
                  <td>maria@gmail.com</td>
                  <td>eduardo1</td>
                </tr>
                <tr>
                  <td>Paulo</td>
                  <td>paulo@gmail.com</td>
                  <td>paulo1</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    


</template>

<style>
.card-adc {
  width: 40rem;
  height: 20rem;
  margin-left: 10%;
  
}

.card-funcionarios {
  width: 40rem;
  height: 20rem;
  margin-right: 10%;
}

.btn-primary {
  background-color: #d32f2f;
  border-color: #d32f2f;
}

</style>