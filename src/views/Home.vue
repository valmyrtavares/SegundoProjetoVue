<template>
  <div class="home">
    <div v-if="loading">
      <PageLoading />
    </div>
    <transition>
      <div v-if="api" class="conteudo">
        <div>
          <h1>Sobre a {{api.titulo}}</h1>
          <p>{{api.descricao}}</p>
          <div>
            <router-link tag="button" class="btn-cursos" to="/cursos">Cursos</router-link>
            <h2>Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <p>{{avaliacao.nome}}</p>
                <p>{{avaliacao.descricao}}</p>
              </li>
            </ul>
          </div>
        </div>
        <img src="../assets/04.png" alt="aprenda web design" />
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";
export default {
  name: "home",
  mixins: [fetchData],
  created() {
    this.fetchData("/home");
  }
};
</script>
<style scoped>
.btn-cursos {
  border-radius: none;
  background: #4b8;
  color: white;
  cursor: pointer;
  padding: 15px 20px;
  font-size: 1rem;
  margin-bottom: 40px;
  margin-top: 10px;
  box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
  font-size: "avenir", Helvetica, Arial, sans-serif;
}
img {
  max-width: 100%;
}
</style>
