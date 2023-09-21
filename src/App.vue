<script setup lang="ts">
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Popular from "./components/Popular.vue";
</script>

<template>
  <Header />
  <div class="mother">
    <Popular />
  </div>
  <Footer />
</template>

<style scoped>
.mother {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.child {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-between;
}
</style>
