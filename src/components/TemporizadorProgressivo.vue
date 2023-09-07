<template>
    <section>
        <strong class='relogio'> {{ tempoDecorrido }}</strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent ({
    name: 'TemporizadorProgressivo',
    props: {
        tempoEmSegundos: {
            type: Number,
            default: 0
        }
    },
    computed: {
        tempoDecorrido () :string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
        }
    }
})

</script>

<style>
.relogio {
    color: var(--texto-primario);
    margin-left: 5px;
}
</style>