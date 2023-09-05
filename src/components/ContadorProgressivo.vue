<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <TemporizadorProgressivo :tempoEmSegundos="tempoEmSegundos" />
        <button class="button" @click="iniciar" :disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="finalizar" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue'
import TemporizadorProgressivo from './TemporizadorProgressivo.vue'

export default defineComponent({
    name: 'ContadorProgressivo ',
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    components: {
        TemporizadorProgressivo
    },
    methods: {
        iniciar() {
            this.cronometroRodando= true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)
        },
        finalizar() {
            clearInterval(this.cronometro)
        }
    }
});

</script>