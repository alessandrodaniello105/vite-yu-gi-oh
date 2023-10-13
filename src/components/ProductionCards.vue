<script>
export default {
  name: 'ProductionCards',
  props: {
    name: String,
    archetype: String,
    type: String,
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
      </div>
      <div class="sub-text-box">

        <p>
          <strong>Type:</strong> {{ type }}
        </p>
        
        <p v-if="archetype">
          <strong>Archetype:</strong> {{ archetype }}
        </p>

        <p v-else>
          <strong>Archetype:</strong> none
        </p>

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
    position: relative;
    height: 100%;
  }
  .sub-text-box {
    position: absolute;
    bottom: 0;
    width: 100%;
    p {
      padding: 0 5px;
      font-size: 20px;
    }
  }
}
</style>