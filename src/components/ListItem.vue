<script setup lang="ts">
import Crown from '../assets/crown.png'
import Star from '../assets/star.png'
import EmptyStar from '../assets/empty-star.png'

const handleClick = () => {
	emit("btnClick", !props.favorite);
}

const props = defineProps<{
	fullName: string;
	imageUrl: string;
	title: string;
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
		<p class="name">
			{{ fullName }}
			<img
				v-if="title.toLowerCase().includes('lady')
					|| title.toLowerCase().includes('lord')"
				class="crown"
				:src="Crown"
				alt="crown"
			/>
			<span class="hide">{{ title }}</span>
		</p>
		<img
			:src="!favorite ? EmptyStar : Star"
			:alt="!favorite ? 'Favorite' : 'Unfovorite'"
			class="star"
			@click="handleClick"
		/>
	</li>
</template>

<style scoped>
.crown {
	width: 15px;
	height: 15px;
}

.hide {
	display: none;
}

.crown:hover + .hide {
	display: block;
	position: absolute;
	background-color: #36013f;
	color: white;
	padding: 5px;
	border-radius: 5px;
}

.star {
	width: 35px;
	height: 35px;
	padding: 15px;
}

.star:hover {
	cursor: pointer;
}

.block-child {
	display: flex;
	flex-direction: row;
	align-items: center;
	align-content: center;
	justify-content: space-evenly;
}

.block-child p {
	font-size: 15px;
	margin: 0;
}

.name {
	align-items: center;
	flex-basis: 50%;
}
</style>