<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" arial-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa voce deseja iniciar?">
            </div>
            <div class="column">
                <ContadorProgressivo />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ContadorProgressivo from './ContadorProgressivo.vue'

export default defineComponent({
    name: 'TaskForm ',
    components: {
        ContadorProgressivo
    }
});
</script>