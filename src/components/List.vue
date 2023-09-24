<script setup lang="ts">
import ListItem from "./ListItem.vue";

import {Person} from "../interfaces/Person.ts";

defineProps<{
	favList: boolean;
	characters: Person[];
}>();
</script>

<template>
	<div class="block">
		<h3>{{ !favList ? "Game of Thrones Characters" : "Favorites Characters" }}</h3>
		<ul>
			<li>
				<div class="block-child">
					<span>Picture</span>
					<span>Character Name</span>
					<span>Favorites</span>
				</div>
			</li>
			<ListItem
				v-for="c in characters"
				:key=c.id
				:image-url=c.imageUrl
				:fullName=c.fullName
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
	width: 60%;
	padding-right: 30px;
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

.block-child {
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
	padding-right: 30px;
}

.block-child p {
	font-size: 15px;
	margin: 0;
}
</style>