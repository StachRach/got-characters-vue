<script setup lang="ts">
import ListItem from "./ListItem.vue";
import Search from "./Search.vue";

import {Person} from "../interfaces/Person.ts";
import {Ref, toRef} from "vue";

const props = defineProps<{
	favList: boolean;
	characters: Person[];
}>();

let data: Ref<Person[]> = toRef(props.characters);

const handleSearch = (input: string) => {
	if (props.favList) {
		data.value = props.characters.filter((c: Person) => c.fullName.toLowerCase().includes(input.toLowerCase()));
	}
}
</script>

<template>
	<div class="block">
		<h3>{{ !favList ? "Game of Thrones Characters" : "Favorites Characters" }}</h3>
		<Search
			v-if="favList"
			@search="(value: string) => handleSearch(value)"
		/>
		<ul class="ul-list">
			<li>
				<div class="block-child">
					<p>Picture</p>
					<p>Character Name</p>
					<p>Favorites</p>
				</div>
			</li>
			<ListItem
				v-for="c in data"
				:key=c.id
				:image-url=c.imageUrl
				:fullName=c.fullName
				:title=c.title
				:family=c.family
				:favList=favList
				:favorite=c.favorite
				@btnClick="(value: boolean) => c.favorite = value"
			/>
		</ul>
	</div>
</template>

<style scoped>
.block {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	
	box-shadow: 0 0 60px -3px rgba(0, 0, 0, 0.2);
	border-radius: 10px;
	border-color: rgba(0, 0, 0, 0.2);
	color: #36013f;
	width: 80%;
	margin-bottom: 30px;
}

.block h3 {
	font-size: 21px;
	padding-top: 10px;
}

.block li {
	list-style: none;
	padding: 15px;
}

.ul-list {
	padding-inline-start: 0;
}

.block-child {
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
	align-content: stretch;
}

.block-child p {
	font-size: 16px;
	margin: 0;
}
</style>