<script>
import { store } from "../data/store";
import ProductionCards from "./ProductionCards.vue";
import FilterSel from './partials/FilterSel.vue'

export default {
  name: "Main",
  components: {
    ProductionCards,
    FilterSel
  },
  data() {
    return {
      store,
      filterStr: ''
    };
  },
  methods: {
    testCycle() {
      console.log(this.store.cardsList)
    },
    filterAPI() {
      store.urlAPI = `${store.urlAPI}&archetype=${this.filterStr}`
    }
  },
  mounted() {
    setTimeout(this.testCycle,1500);
  }
};
</script>

<template>
  <main>
    <div class="container">

      <FilterSel
        v-model="filterStr" 
        @select="this.filterAPI()"
      />

      <div class="row">
        <ProductionCards
          v-for="card in store.cardsList"
          :key="card.id"
          :image="`https://images.ygoprodeck.com/images/cards/${card.id}.jpg`"
          :name="card.name"
          :archetype="card.archetype"
        />
      </div>

    </div>
  </main>
</template>

<style lang="scss">

@use '../scss/partials/vars' as *;

main {
  background-color: $primary-color;
  .container {
    margin-top: 100px;
    background-color: white;
    .row {
      padding: 50px;
    }
  }
  
}


</style>