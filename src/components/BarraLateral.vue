<template>
    <header>
        <img src="../assets/logo.png" alt="">
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BarraLateral'
});
</script>

<style scoped>

header {
    padding: 15px;
    background: #0d3b66;
    width: 60%;
    height: 100vh;
    margin-right: -25px;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>
