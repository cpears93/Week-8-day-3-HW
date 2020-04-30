<template lang="html">
  <li class="cards__item">
    <div class="card">
      <div class="card__content">
        <div class="card__title">{{dog.name}}</div>
        <p class="card__text">{{dog.breed}}</p>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  name: 'dog-item',
  props: ['dog']
}
</script>

<style lang="css" scoped>
</style>
