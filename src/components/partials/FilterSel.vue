<script>
import axios from 'axios';
import {store} from '../../data/store'

export default {
  name: 'FilterSel',
  data() {
    return {
      store,
      filterStr: 'Select Archetype'
    }
  },
  methods: {
    getAPI(param) {
      axios.get(param)
        .then( res => {
          store.cardsList = res.data.data;
          // console.log(this.store.cardsList);

          
        })
        .catch( err => {
          console.log(err.code);
        })
    },

    startFilter() {  
      console.log(this.filterStr)
      if(this.filterStr == "Select Archetype") {
        store.urlAPI = 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0';
        this.getAPI(store.urlAPI)
      }else {
        store.urlAPI = `https://db.ygoprodeck.com/api/v7/cardinfo.php?&archetype=${this.filterStr}`;
        this.getAPI(store.urlAPI)
      }
      
      console.log('nuovo url', store.urlAPI)
    }
  }
}
</script>

<template>
  <div class="filter-selector">
    <span>Sono la tua search-bar preferita!</span>

    <select
      v-model="filterStr"
      class="form-select"
      aria-label="Default select example"
      >
      <option @click="this.startFilter" selected>Select Archetype</option>
      <option v-for="(element, index) in store.archetypesList" :key="index" @click="this.startFilter" :value="element.archetype_name">{{element.archetype_name}}</option>

    </select>

  </div>
</template>

<style lang="scss" scoped>
@use '../../scss/partials/vars' as *;

.filter-selector {
  font-weight: bold;
  color: white;
  background-color: $primary-color;
  padding: 15px 0;
  select {
    margin: 5px 0;
    width: 200px;
  }
} 
</style>