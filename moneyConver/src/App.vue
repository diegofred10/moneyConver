<template>
  <div class="fondo">
    <Navbar />
    <Conver />
  </div>
</template>

<script>
import Conver from './components/Conver.vue';
import Navbar from './components/Navbar.vue';
export default {
  name: "App",
  components: {
    Conver,
    Navbar,
  },
};
</script>

<style>
.fondo {
  height: 100vh;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
</style>