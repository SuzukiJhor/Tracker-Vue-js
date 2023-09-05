<template>
  <main class="columns is-gapless is-multiline">
    <div class="column">
      <BarraLateral />
    </div>
    <div class="column is-three-quarters">
      <TaskForm  @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TaskList v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
  
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import TaskForm  from './components/TaskForm .vue';
import TaskList from './components/TaskList.vue';
import Itarefa from './interfaces/ITarefa'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    TaskForm ,
    TaskList
  },
  data () {
    return {
      tarefas: [] as Itarefa []
    }
  },
  methods: {
    salvarTarefa (tarefa: Itarefa) {
      this.tarefas.push(tarefa)
    }
  }
});
</script>

<style>
main {
  display: flex;
  background-color: #4a4a4a;
  
}

.column {
  margin:0;
  padding: 0
}
.lista {
  padding: 1.5 rem;
}

</style>
