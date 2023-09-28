<script setup lang="ts">
import PopularItem from "./PopularItem.vue";

import {Person} from "../interfaces/Person.ts";
import {onBeforeUpdate} from "vue";

const props = defineProps<{
	characters: Person[];
}>();

let king;
let queen;
let royalties: Person[] = [];

onBeforeUpdate(() => {
	king = props.characters
		.filter((c: Person) => c.title.toLowerCase().includes("king"))
		.splice(0, 1);
	queen = props.characters
		.filter((c: Person) => c.title.toLowerCase().includes("queen"))
		.splice(1, 1);
	royalties = [...king, ...queen]
})
</script>

<template>
  <div class="box">
	  <PopularItem
		  v-for="c in royalties"
		  class="component"
		  :image-url=c.imageUrl
		  :name=c.fullName
		  :title=c.title
		  :house=c.family
	  />
  </div>
</template>

<style scoped>
.box {
  display: flex;
	//margin: 15px 30px 30px 30px;
  justify-content: center;
}

.component {
	margin: 0 20px;
}
</style>