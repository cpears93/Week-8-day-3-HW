<template lang="html">
	<div id="dog-list">
		<div class="flex">
			<h2>All the puppers!</h2>
		</div>
		<ul class="cards">
			<dog-item v-for="(dog, index) in dogs" :key="index"  :dog="dog" />
		</ul>
	</div>
</template>

<script>

import DogItem from './DogItem.vue';

export default {
	name: "dog-list",
	props: ["dogs"],
	components: {
		'dog-item': DogItem
	}
}
</script>

<style lang="css" scoped>
.flex {
	display: flex;
	justify-content: center;
}

.cards {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
