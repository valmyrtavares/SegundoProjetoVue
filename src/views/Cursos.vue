<template>
  <div class="cursos">
    <div v-if="loading">
      <PageLoading />
    </div>
    <transition>
      <div v-if="api">
        <h1>{{api.titulo}}</h1>
        <p>{{api.descricao}}</p>
        <ul>
          <li v-for="curso in api.cursos" :key="curso.id">
            <router-link :to="{name:'curso', params:{curso: curso.id}}">
              <h2>{{curso.nome}}</h2>
            </router-link>
            <p>{{curso.descricao}} - {{curso.totalAulas}} | Aulas {{curso.horas}}Horas</p>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>
<script>
import fetchData from "@/mixins/fetchData.js";
export default {
  name: "cursos",
  mixins: [fetchData],
  created() {
    this.fetchData("/cursos");
  }
};
</script>
