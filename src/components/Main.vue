<script>
import axios from 'axios';
import { store } from "../data/store";
import ProductionCards from "./ProductionCards.vue";
import FilterSel from './partials/FilterSel.vue'
import Results from './partials/Results.vue';

export default {
  name: "Main",
  components: {
    ProductionCards,
    FilterSel,
    Results
  },
  data() {
    return {
      store,
      filterStr: 'Select Archetype'
    }
  },

  methods: {
    testCycle() {
      console.log(this.store.cardsList)
    },

    getAPI(param) {
      axios.get(param)
        .then( res => {
          store.cardsList = res.data.data;
          store.cardsTotal = store.cardsList.length

          // console.log(this.store.cardsList);
        })
        .catch( err => {
          console.log(err.code);
        })
    }
  },
  mounted() {
    setTimeout(this.testCycle,1500);
  }
};
</script>

<template>
  <main>
    <div class="container p-0">


      <FilterSel />

      <Results :cardsNum="store.cardsTotal" />

      

      <div class="row">


        <ProductionCards
          v-for="card in store.cardsList"
          :key="card.id"
          :image="`https://images.ygoprodeck.com/images/cards/${card.id}.jpg`"
          :name="card.name"
          :archetype="card.archetype"
          :type="card.type"
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


@media (min-width: 1400px) {
  .container {
    max-width: 1550px !important; 
  }
}

</style>