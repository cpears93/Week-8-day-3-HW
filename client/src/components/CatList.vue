<template lang="html">
	<div id="cat-list">
		<div class="flex">
			<h2>All the kitties!</h2>

		</div>
		<ul class="cards">

			<cat-item v-for="(cat, index) in cats" :key="index"  :cat="cat" />

		</ul>
	</div>
</template>

<script>

import CatItem from './CatItem.vue'

export default {
	name: "cat-list",
	props: ["cats"],
	components: {
		'cat-item': CatItem
	}
}
</script>

<style lang="css" scoped>

</style>
