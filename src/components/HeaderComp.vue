<template>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-light bg-light m-3">
  <!-- Container wrapper -->
  <div class="container-fluid">
    <!-- Toggle button -->
    <button
      class="navbar-toggler"
      type="button"
      data-mdb-toggle="collapse"
      data-mdb-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <i class="fas fa-bars"></i>
    </button>

    <!-- Collapsible wrapper -->
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <!-- Navbar brand -->
      <a class="navbar-brand mt- mt-lg-0" href="#">
        <img
          src="../assets/PedidosNOW.png"
          height="50"
          loading="lazy"
        />
      </a>
    </div>
      <!-- Left links -->
      <div class="float-end">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0 fs-6">
        <li class="nav-item m-2">
              <a class="nav-link" aria-current="page" href="#"><RouterLink to="/pedidosAbertos">Pedidos Abertos</RouterLink></a>
            </li>
            <li class="nav-item m-2">
              <a class="nav-link" href="#"><RouterLink to="/historicoPedidos">Histórico de Pedidos</RouterLink></a>
            </li>
            <li class="nav-item m-2">
              <a class="nav-link" href="#"><RouterLink to="/editarCardapio">Editar Cardápio</RouterLink></a>
            </li>
            <li class="nav-item m-2">
              <a class="nav-link" href="#"><RouterLink to="/visuCardapio">Visualizar Cardápio</RouterLink></a>
            </li>
            <li class="nav-item m-2">
              <a class="nav-link" href="#"><RouterLink to="/funcionarios">Controle de Funcionários</RouterLink></a>
            </li>
      </ul>
      <!-- Left links -->
    </div>
    <!-- Collapsible wrapper -->
  </div>
  <!-- Container wrapper -->
</nav>
<!-- Navbar -->


</template>

<style scoped>

li a {
    text-decoration: none;
    color: black;
}

</style>
