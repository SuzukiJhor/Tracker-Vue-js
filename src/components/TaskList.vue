<template>
    <BoxDiv>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <TemporizadorProgressivo :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxDiv>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import TemporizadorProgressivo from './TemporizadorProgressivo.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxDiv from './BoxDiv.vue';

export default defineComponent({
    name: 'TaskList',
    components: {
        TemporizadorProgressivo,
        BoxDiv
    },
    props: {
        tarefa: {
            type:  Object as PropType<ITarefa>,
            required: true
        }
    }
});

</script>

<style scoped> 

</style>