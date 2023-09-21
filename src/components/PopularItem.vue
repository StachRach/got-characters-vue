<script setup lang="ts">
defineProps<{
  name: string;
  imageUrl: string;
  films: string[];
  tvShows: string[];
}>();
</script>

<template>
  <div class="popular-item">
    <img :src=imageUrl :alt=name width="290" height="290"/>
    <p class="name-fav">{{ name }}</p>
    <p>Films: <span>{{ films.length }}</span></p>
    <p>TV series: <span>{{ tvShows.length }}</span></p>
  </div>
</template>

<style scoped>
.popular-item {
  display: flex;
  flex-direction: column;
  box-shadow: 0 0 60px -3px rgba(0, 0, 0, 0.2);
  border-radius: 20px;
  border-color: rgba(0, 0, 0, 0.2);
  color: #36013f;
  padding: 24px;
}

.popular-item img {
  border-radius: 20px;
  box-shadow: 0 0 20px 5px rgba(0, 0, 0, 0.2);
}

.popular-item p {
  text-align: left;
  padding-left: 20px;
}

.popular-item p span {
  text-align: right;
  font-weight: bold;
}

.name-fav {
  padding-bottom: 30px;
  font-size: 20px;
}
</style>