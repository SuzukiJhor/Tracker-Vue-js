<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" arial-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa voce deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <ContadorProgressivo @aoContadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ContadorProgressivo from './ContadorProgressivo.vue'

export default defineComponent({
    name: 'TaskForm ',
    emits: ['aoSalvarTarefa'],
    components: {
        ContadorProgressivo
    },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            console.log('tempo da tarefa: ', tempoDecorrido);
            console.log('descrição da tarefa:', this.descricao);
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })

            this.descricao = ''

        }
    }
});
</script>

<style>
.box{
    width:90%;
    margin-top:20px;
}

.formulario {
    color: var(--texto-primario) !important;
    background-color: var(--bg-primario) !important;
}
</style> 