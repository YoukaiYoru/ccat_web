<!-- Project Portfolio -->

<template>
<!-- title -->
<h1 class="mx-16">
	<!-- white text colour in style -->
	<span class="text-primary-test"
	>Portafolio de proyectos</span>
</h1>

<!-- search bar -->
<QuerySelector />


<!-- carousel -->

<!-- make a 3x3 grid carousel of items -->

<v-row class="mx-0">
	<v-col cols="4" v-for="(item, id) in visible" :key="id">

		<ProjectItem
		img-src="src/assets/patata.jpg"
		:title="item.title"
		description="item.description"
		:id="item.id"
		/>

	</v-col>
</v-row>

<v-row class="my-5">
	<v-col class="text-center" cols="12">
		<!-- a pagination linked to "page" -->
		<v-pagination v-model="page.val" :length="pages" circle></v-pagination>
	</v-col>
</v-row>


</template>

<script setup>

import ProjectItem from '@/components/SearchProjects/ProjectItem.vue';
import QuerySelector from '@/components/SearchProjects/QuerySelector.vue';
import {reactive, computed} from 'vue'

const itemWidth= "33.33%"
const itemHeight= "33.33%"
const itemsPerPage = 9
const page = reactive({val: 1})

function clicked () {
	console.log('clicked')
	// log page number
	console.log(page.val)
}

const items = [
	{ id: 1, title: 'Item 1' },
	{ id: 2, title: 'Item 2' },
	{ id: 3, title: 'Item 3' },
	{ id: 4, title: 'Item 4' },
	{ id: 5, title: 'Item 5' },
	{ id: 6, title: 'Item 6' },
	{ id: 7, title: 'Item 7' },
	{ id: 8, title: 'Item 8' },
	{ id: 9, title: 'Item 9' },
	{ id: 10, title: 'Item 10' },
	{ id: 11, title: 'Item 11' },
	{ id: 12, title: 'Item 12' },
	{ id: 13, title: 'Item 13' },
	{ id: 14, title: 'Item 14' },
	{ id: 15, title: 'Item 15' },
	{ id: 16, title: 'Item 16' },
	{ id: 17, title: 'Item 17' },
	{ id: 18, title: 'Item 18' },
	{id:19, title: 'Item 19'}
]

const pages = computed(() => {
	return Math.ceil(items.length / itemsPerPage)
})

const visible = computed(() => {
	console.log('visible')
	return items.slice((page.val - 1) * itemsPerPage, page.val * itemsPerPage)
})

</script>

<style scoped>
.text-primary-test {
	color: #778DA9;
}

h1 {
	line-height: 3;
}
</style>
