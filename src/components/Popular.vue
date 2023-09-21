<script setup lang="ts">
import Image from "../assets/square.png";
import PopularItem from "./PopularItem.vue";
// import { ref } from "vue";

interface Character {
  id: number;
  name: string;
  imageUrl: string;
  films: string[];
  tvShows: string[];
}

const data: Character[] = [
  {
    id: 1,
    name: "Jon Snow",
    imageUrl: Image,
    films: ["a", "b", "c"],
    tvShows: ["d", "e", "f"],
  },
  {
    id: 2,
    name: "Arya Stark",
    imageUrl: Image,
    films: ["a", "b", "c"],
    tvShows: ["d", "e", "f"],
  },
  {
    id: 3,
    name: "Cersei Lannister",
    imageUrl: Image,
    films: ["a", "b", "c"],
    tvShows: ["d", "e", "f"],
  },
]

// const characters = ref(data)
</script>

<template>
  <div class="box">
    <div v-for="c in data">
      <PopularItem
          :films=c.films
          :tv-shows=c.tvShows
          :image-url=c.imageUrl
          :name=c.name
      />
    </div>
  </div>
</template>

<style scoped>
.box {
  display: flex;
  margin-top: 15px;
  margin-bottom: 30px;
  justify-content: center;
}
</style>