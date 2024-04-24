<script setup>
import { onMounted } from 'vue';

const emit = defineEmits(['cookieStatus']);

function acceptCookies(stat) {
	localStorage.setItem('acceptCookies', stat);
	if (!stat || !localStorage.getItem('acceptCookies')) {
		alert('Need to accept cookies to view content')
	}
	emit('cookieStatus', stat);
}

onMounted(() => {

	window.addEventListener('keypress', (Event) => {
		if (localStorage.getItem('acceptCookies') === 'false' || !localStorage.getItem('acceptCookies')) {
			if (Event.keyCode === 97 || Event.keyCode === 65) {
				acceptCookies(true)
			} else if (Event.keyCode === 100 || Event.keyCode === 68) {
				acceptCookies(false)
			}
		}
	})
	localStorage.getItem('acceptCookies') === 'true' ? emit('cookieStatus', true) : emit('cookieStatus', false);
})

</script>
<template>
	<div
		class="fixed inset-x-0 bottom-0 z-50 flex flex-col items-center justify-center bg-gray-800 text-white p-4 sm:p-6 lg:p-8">
		<p class="text-lg md:text-xl text-center mb-4">
			Accept cookies to view content
		</p>
		<div class="flex flex-col md:flex-row gap-2">
			<button @click="acceptCookies(true)" class="bg-teal-600 w-full min-w-[200px] hover:bg-teal-700 px-4 py-2 text-sm md:text-base font-semibold rounded-lg
				mb-2 md:mb-0">
				(A)ccept
			</button>
			<button @click="acceptCookies(false)" class=" bg-gray-600 w-full min-w-[200px] hover:bg-gray-700 px-4 py-2 text-sm md:text-base font-semibold
				rounded-lg">
				(D)ecline
			</button>
		</div>
	</div>
</template>


<style scoped></style>