<script setup>
import { ref } from 'vue';
import CookieBanner from './CookieBanner.vue';

const contentVisible = ref(false);
const showCookieBanner = ref(true);

function showContent(stat) {
	if (stat) {
		contentVisible.value = true;
		showCookieBanner.value = false;
	} else if (!stat) {
		contentVisible.value = false;
		showCookieBanner.value = true;
	}
}


</script>

<template>
	<div v-if="contentVisible" class="absolute m-0 top-1/2 translate-y-[-50%] translate-x-[500%]">
		<h1>this is the content</h1>
	</div>
	<CookieBanner v-if="showCookieBanner" @cookie-status="showContent" />
</template>

<style scoped>
.logo {
	height: 6em;
	padding: 1.5em;
	will-change: filter;
	transition: filter 300ms;
}

.logo:hover {
	filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
	filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
