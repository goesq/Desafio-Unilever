<template>
    <div>
      <header>
        <div class="logo-wrapper">
          <a href="index.html">
            <img src="@/assets/images/controleunilever.png" alt="Logo icon">
          </a>
        </div>
        
        <nav class="nav-links">
          <a href="ativos.html">Adicionar</a>
          <a href="remover.html">Remover</a>
          <a href="#">Alterar</a>
          <a href="relatorio.html">Relatório</a>
          <a href="help.html">Ajuda</a>
          <i class="fa-solid fa-moon" @click="toggleDarkMode"></i>
        </nav>
      </header>
  
      <section class="main-section">
        <div class="section-wrapper">
          <div class="login-container">
            <div class="text-wrapper">
              <h1>EDITAR ATIVOS</h1>
              <input v-model="nome" type="text" placeholder="Nome" />
              <input v-model="quantidade" type="number" placeholder="Quantidade" />
              <input v-model="lote" type="number" placeholder="Lote" />
              <input v-model="tipo" type="text" placeholder="Tipo" />
              <button @click="alterarAtivo"><b>Alterar</b></button>
            </div>
          </div>
        </div>
      </section>
  
      <footer>
        <p>Todos os direitos reservados © | ControleUnilever - 2024</p>
      </footer>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nome: '',
        quantidade: '',
        lote: '',
        tipo: ''
      };
    },
    methods: {
      toggleDarkMode() {
        // Função para alternar entre modo claro e escuro
        document.body.classList.toggle('dark-mode');
      },
      alterarAtivo() {
        // Lógica para alterar o ativo (exemplo de placeholder)
        console.log('Alterando ativo:', this.nome, this.quantidade, this.lote, this.tipo);
        // Você pode adicionar aqui a lógica de API ou outras ações para alterar o ativo.
      }
    }
  };
  </script>
  
  <style src="../assets/css/global.css"></style>
  <style src="../assets/css/reset.css"></style>
  <style scoped src="../assets/css/header.css"></style>
  <style scoped src="../assets/css/main.css"></style>
  <style scoped src="../assets/css/footer.css"></style>
  