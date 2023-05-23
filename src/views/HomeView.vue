<template>
  <div class="about">
    <!-- <h1>Jogo da Velha</h1> -->
    <Jogo />
  </div>
</template>

<script>
import Jogo from "@/components/Jogo.vue";

export default {
  components: {
    Jogo,
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    
  }
}
</style>
