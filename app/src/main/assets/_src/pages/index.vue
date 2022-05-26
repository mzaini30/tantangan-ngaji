<script setup>
	import confetti from 'canvas-confetti'
	import Piala from '/src/icon/piala.vue'
	import Diamond from '/src/icon/diamond.vue'
	import {ref} from 'vue'
	import localforage from 'localforage'

	const level = ref(1)
	const diamond = ref(0)

	function reset(){
		level.value = 1
		diamond.value = 0
	}

	async function init(){
		let data = await localforage.getItem('dataTantanganNgaji')
		if (data){
			level.value = data.level
			diamond.value = data.diamond
		}
	}
	init()

	async function selesai(){
		if (level.value > 30){
			const levelSeharusnya = level.value % 30
			diamond.value += levelSeharusnya	
		} else {
			diamond.value += level.value
		}

		level.value++

		localforage.setItem('dataTantanganNgaji', {
			level: level.value,
			diamond: diamond.value
		})

		confetti()
	}

	function olahNilai(x){
		if (x > 30){
			x %= 30
			if (x == 0){
				x = 30
			}
		}
		return x
	}
	function bacaAwal(){
		let nilai = diamond.value + 1
		return olahNilai(nilai)
	}
	function bacaAkhir(){
		let nilai = diamond.value + level.value
		return olahNilai(nilai)
	}
</script>

<template>
	<p class="absolute p-3 pt-2 w-full top-0 left-0 text-right text-indigo-500">
		<Piala class='icon'></Piala>
		{{ level.toLocaleString() }}
		<Diamond class='icon'></Diamond>
		{{ diamond.toLocaleString() }}
	</p>

	<div class="p-5 pt-2 grid content-center bg-indigo-50 w-full min-h-screen">
		<div class="text-center -mt-[10vh]">
			<p class="mb-2 text-sm">Tantangan hari ini</p>
			<p class="text-lg text-indigo-500 uppercase">
				Baca <span class="font-bold">juz {{ bacaAwal() }}</span>
				<span v-if='level > 1 && bacaAwal() != bacaAkhir()'>
					sampai <span class="font-bold">juz {{ bacaAkhir() }}</span>
				</span>
			</p>
			<button class="mt-10 px-3 py-1 rounded outline-indigo-500 text-indigo-800 outline cursor-pointer" @click='selesai'>Selesai</button>
			<!-- <button class="mt-10 px-3 py-1 ml-5 rounded outline-red-500 text-red-800 outline cursor-pointer" @click='reset'>Reset</button> -->
		</div>
	</div>

</template>

<style scoped>
	.icon {
		@apply inline-block w-5 h-auto
	}
</style>