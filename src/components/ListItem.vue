<script setup lang="ts">

const handleClick = () => {
	emit("btnClick", !props.favorite);
}

const props = defineProps<{
	fullName: string;
	imageUrl: string;
	family: string;
	favList: boolean;
	favorite: boolean;
}>();

const emit = defineEmits<{
	btnClick: [value: boolean]
}>();
</script>

<template>
	<li class="block-child" v-if="(family !== 'House Lannister') && (!favList || favList && favorite)">
		<img :src=imageUrl alt=name width="60" height="60"/>
		<p class="name">{{ fullName }}</p>
		<button @click="handleClick">{{ !favorite ? "Favorite" : "Unfavorite" }}</button>
	</li>
</template>

<style scoped>
.block-child {
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
}

.block-child p {
	font-size: 15px;
	margin: 0;
	padding: 15px 15px 0 15px;
}

.name {
	align-items: center;
	flex-basis: 50%;
}
</style>