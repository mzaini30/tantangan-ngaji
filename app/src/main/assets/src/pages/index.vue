<script setup>
	import confetti from 'canvas-confetti'
	import Piala from '/src/icon/piala.vue'
	import Diamond from '/src/icon/diamond.vue'

	async function selesai(){
		confetti()
	}
</script>

<template>
	<p class="absolute p-3 pt-2 w-full top-0 left-0 text-right text-indigo-500">
		<Piala class='icon'></Piala>
		1
		<Diamond class='icon'></Diamond>
		1
	</p>

	<div class="p-5 pt-2 grid content-center bg-indigo-50 w-full min-h-screen">
		<div class="text-center -mt-[10vh]">
			<p class="mb-2 text-sm">Tantangan hari ini</p>
			<p class="text-lg text-indigo-500 uppercase">Baca <span class="font-bold">juz 1</span> sampai <span class="font-bold">juz 30</span></p>
			<button class="mt-10 px-3 py-1 rounded outline-indigo-500 text-indigo-800 outline cursor-pointer" @click='selesai'>Selesai</button>
		</div>
	</div>

</template>

<style scoped>
	.icon {
		@apply inline-block w-5 h-auto
	}
</style>