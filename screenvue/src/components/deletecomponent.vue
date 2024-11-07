<template>
  <div>
    <header>
      <div class="logo-wrapper">
        <a href="index.html">
          <img src="@/assets/images/controleunilever.png"" alt="Logo icon" />
        </a>
      </div>

      <nav class="nav-links">
        <router-link to="/ativos">Adicionar</router-link>
        <router-link to="/remover">Remover</router-link>
        <router-link to="#">Alterar</router-link>
        <router-link to="/relatorio">Relatório</router-link>
        <router-link to="/help">Ajuda</router-link>
        <i class="fa-solid fa-moon" @click="toggleDarkMode"></i>
      </nav>
    </header>

    <section class="main-section">
      <div class="section-wrapper">
        <div class="login-container">
          <div class="text-wrapper">
            <h1>REMOVER</h1>
            <!-- Agora usamos id_ativo em vez de lote -->
            <input v-model="id_ativo" type="text" placeholder="ID do Ativo" />
            <button @click="removerAtivo"><b>Remover</b></button>
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
import axios from 'axios';

// Criando uma instância do axios com o baseURL
const api = axios.create({
  baseURL: 'http://localhost:5000/api', // Substitua pela URL correta do seu backend
});

export default {
  data() {
    return {
      id_ativo: "",  // ID do ativo que será removido
    };
  },
  methods: {
    async removerAtivo() {
      // Verifica se o campo id_ativo está preenchido corretamente
      if (this.id_ativo === "") {
        alert("Por favor, preencha o campo ID do Ativo.");
        return;
      }

      try {
        // Envia uma requisição DELETE para o backend com o id_ativo na URL
        const response = await api.delete(`/produtos/${this.id_ativo}`);

        // Exibe a mensagem de sucesso retornada pela API
        alert(response.data.message);

        // Limpa o campo após sucesso
        this.id_ativo = "";
      } catch (error) {
        // Exibe uma mensagem de erro se houver falha
        const errorMessage = error.response?.data?.message || 'Erro desconhecido';
        alert("Erro ao remover o ativo: " + errorMessage);
      }
    },
    toggleDarkMode() {
      // Alterna entre os modos claro e escuro
      document.body.classList.toggle("dark-mode");
    },
  },
};
</script>

<style src="../assets/css/global.css"></style>
<style src="../assets/css/reset.css"></style>
<style scoped src="../assets/css/main.css"></style>
<style scoped src="../assets/css/header.css"></style>
<style scoped src="../assets/css/footer.css"></style>
