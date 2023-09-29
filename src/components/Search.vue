<script setup lang="ts">
import {ref} from "vue";

const input = ref('');
const emit = defineEmits<{
	search: [value: string]
}>();

const handleInput = () => {
	emit("search", input.value);
}
</script>

<template>
	<input
		type="text"
		placeholder="Search for character..."
		v-model="input"
		@input="handleInput"
	/>
</template>

<style scoped>
input {
	width: 200px;
	height: 30px;
	border-radius: 5px;
	border: 2px solid #36013f;
	padding: 5px;
}
</style>