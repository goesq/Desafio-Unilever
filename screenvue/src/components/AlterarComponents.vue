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
            <input v-model="id_ativo" type="text" placeholder="id_ativo" />
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
      tipo: '',
      id_ativo: ''
    };
  },
  created() {
    // Verifica se o id_ativo foi fornecido na URL ou de algum outro lugar
    if (this.id_ativo) {
      this.carregarAtivo(this.id_ativo);
    }
  },
  methods: {
    toggleDarkMode() {
      // Função para alternar entre modo claro e escuro
      document.body.classList.toggle('dark-mode');
    },
    // Método para carregar os dados do ativo com base no id_ativo
    carregarAtivo(id) {
      // Exemplo de chamada para uma API para buscar o ativo
      fetch(`https://api.example.com/ativos/${id}`)
        .then(response => response.json())
        .then(data => {
          this.nome = data.nome;
          this.quantidade = data.quantidade;
          this.lote = data.lote;
          this.tipo = data.tipo;
        })
        .catch(error => {
          console.error('Erro ao carregar o ativo:', error);
        });
    },
    // Método para alterar os dados do ativo
    alterarAtivo() {
      // Verifica se todos os campos estão preenchidos
      if (!this.nome || !this.quantidade || !this.lote || !this.tipo || !this.id_ativo) {
        alert("Todos os campos devem ser preenchidos!");
        return;
      }
      
      // Criando o objeto com os dados a serem alterados
      const ativo = {
        nome: this.nome,
        quantidade: this.quantidade,
        lote: this.lote,
        tipo: this.tipo
      };
      
      // Exemplo de chamada para a API para alterar o ativo
      fetch(`https://api.example.com/ativos/${this.id_ativo}`, {
        method: 'PUT', // Método de atualização
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(ativo)
      })
        .then(response => response.json())
        .then(data => {
          console.log('Ativo alterado com sucesso:', data);
          alert("Ativo alterado com sucesso!");
        })
        .catch(error => {
          console.error('Erro ao alterar o ativo:', error);
          alert("Erro ao alterar o ativo.");
        });
    }
  }
};
</script>

<style src="../assets/css/global.css"></style>
<style src="../assets/css/reset.css"></style>
<style scoped src="../assets/css/header.css"></style>
<style scoped src="../assets/css/main.css"></style>
<style scoped src="../assets/css/footer.css"></style>
