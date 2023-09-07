<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro conteudo': modoEscuroAtivo}">
    <div class="">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarters">
      <TaskForm @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TaskList v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxDiv v-if="listaVazia">
          Nenhuma Tarefa até Agora!
        </BoxDiv>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import TaskForm from './components/TaskForm .vue';
import TaskList from './components/TaskList.vue';
import Itarefa from './interfaces/ITarefa'
import BoxDiv from './components/BoxDiv.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    TaskForm,
    TaskList,
    BoxDiv
  },
  data() {
    return {
      tarefas: [] as Itarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaVazia(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: Itarefa) {
      this.tarefas.push(tarefa)
    },

    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.column {
  margin: 0;
  padding: 0;
  width: 100%;
}

.lista {
  padding: 1.5 rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
