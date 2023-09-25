<script setup lang="ts">
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Popular from "./components/Popular.vue";
import List from "./components/List.vue";

import {Person} from "./interfaces/Person.ts";

import {onBeforeMount, Ref, ref} from "vue";

const temp: Person[] = [];
const characters: Ref<Person[]> = ref([]);

onBeforeMount(() => {
	fetch("https://thronesapi.com/api/v2/Characters")
		.then((response) => response.json())
		.then((data) => {
			data.forEach((c: Person) => {
				temp.push({
					id: c.id,
					firstName: c.firstName,
					lastName: c.lastName,
					fullName: c.fullName,
					title: c.title,
					family: c.family,
					imageUrl: c.imageUrl,
					favorite: false,
				})
			});
			characters.value = temp;
			
			console.log(characters.value);
		})
		.catch((error) => console.error(error));
})
</script>

<template>
  <Header />
  <div class="mother">
    <Popular :characters=characters />
	  <div class="child">
	    <List class="component" :characters=characters :favList=false />
	    <List class="component" :characters=characters :favList=true />
    </div>
  </div>
  <Footer />
</template>

<style scoped>
.mother {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
	margin-bottom: 30px;
}

.child {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-between;
	width: 55%;
}

.component {
	margin: 20px;
}
</style>
