<script>
export default {
  name: 'ProductionCards',
  props: {
    name: String,
    archetype: String,
    id: Number,
    image: String
  }
}
</script>

<template>
  <div class="col-3">
    <div class="card_ctm">
      <img :src="image" :alt="name">
      <h4>{{ name }}</h4>
      <p>{{ archetype }}</p>
    </div>
  </div>
</template>

<style lang="scss">

</style>