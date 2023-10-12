<script>
import ProductionCards from "./ProductionCards.vue";
import { store } from "./data/store.js";

export default {
  name: "Main",
  components: {
    ProductionCards,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    testCycle() {
      console.log(this.store.cardsList)
    }
  },
  mounted() {
    setTimeout(this.testCycle,1500)
  }
};
</script>

<template>
  <main>
    <div class="container">
      <div class="row">
        <ProductionCards
          v-for="card in store.cardsList"
          :key="card.id"
          :image="card.card_images.image_url"
          :name="card.name"
        />
      </div>
    </div>
  </main>
</template>

<style lang="scss">
</style>