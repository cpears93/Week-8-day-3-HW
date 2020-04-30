<template lang="html">
  <li class="cards__item">
    <div class="card">
      <div class="card__content">
        <div class="card__title">{{cat.name}}</div>
        <p class="card__text">{{cat.breed}}</p>
      </div>
    </div>
  </li>
</div>

</template>

<script>
export default {
  name: 'cat-item',
  props: ['cat']
}
</script>

<style lang="css" scoped>


</style>
