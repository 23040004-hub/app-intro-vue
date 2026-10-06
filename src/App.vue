<script>
import EjemplosVue from './components/EjemplosVue.vue'

export default {
  name: 'App',

  components: {

    EjemplosVue,
  },
}
</script>

<template>
  <div class="aplicacion">



    <main class="contenido">

      <EjemplosVue />

    </main>

  </div>
</template>

<style scoped>
.aplicacion {
  min-height: 100vh;
  background-color: #f4f7fb;
}

.contenido {
  max-width: 1200px;

  margin: auto;

  padding: 35px;
}
</style>