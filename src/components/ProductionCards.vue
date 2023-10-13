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
  <div class="col-6 col-lg-3 col-xl-2 my-3">
    <div class="card_ctm">

      <img :src="image" :alt="name">

      <div class="text-box">
        <h3 class="title">{{ name }}</h3>
        <p>{{ archetype }}</p>
      </div>

    </div>
  </div>
</template>

<style lang="scss">
@use '../scss/partials/vars' as *;

.card_ctm {
  position: relative;
  text-align: center;
  background-color: $primary-color;
  min-height: 550px;
  .text-box {
    padding: 5px;
    p {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 20px;
    }
  }
}
</style>