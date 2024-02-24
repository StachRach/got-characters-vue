<script setup lang="ts">
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Popular from "./components/Popular.vue";
import List from "./components/List.vue";

import {Person} from "./interfaces/Person.ts";

import {Ref, ref} from "vue";
import {useQuery} from "vue-query";

const temp: Person[] = [];
const characters: Ref<Person[]> = ref([]);

const fetchData = () => {
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
		
		console.table(characters.value);
	})
	.catch((error) => console.error(error));
}

const {isLoading, isError, error} = useQuery("characters", fetchData);
</script>

<template>
	<Header />
	<template v-if="isLoading">
		<div class="mother">
			<h1>Loading...</h1>
		</div>
	</template>
	<template v-else-if="isError">
		<div class="mother">
			<h1>Error: {{ error }}</h1>
		</div>
	</template>
	<template v-else>
		<div class="mother">
			<Popular :characters=characters />
			<div class="child">
				  <List class="component" :characters=characters :favList=false />
				  <List class="component" :characters=characters :favList=true />
			</div>
		</div>
	</template>
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
	width: 60%;
}

.component {
	margin: 20px;
}
</style>
