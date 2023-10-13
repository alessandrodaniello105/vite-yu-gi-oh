<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import { store } from './data/store';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data(){
    return {
      store
    }
  },

  methods: {
    getAPI(param) {
      axios.get(param)
        .then( res => {
          store.cardsList = res.data.data;
          store.cardsTotal = store.cardsList.length
          // console.log(this.store.cardsList);
          
          this.getArchetypes('https://db.ygoprodeck.com/api/v7/archetypes.php')
        })
        .catch( err => {
          console.log(err.code);
        })
    },
    getArchetypes(param) {
      axios.get(param)
        .then( res => {
          store.archetypesList = res.data
          store.cardsTotal = store.cardsList.length
        })
        .catch( err => {
          console.log(err.code)
        })
    },
    getTypes(param) {
      axios.get(param)
        .then( res => {
          store.typesList = res.data
          store.cardsTotal = store.cardsList.length
          console.log(store.archetypesList)
        })
        .catch( err => {
          console.log(err.code)
        })
    }
  },

  mounted() {
    
    this.getAPI(store.urlAPI);

    // console.log(`${store.urlAPI}&archetype=alien`);

    // arrays seems to be empty because of async functions (ajax request)
    setTimeout(()=>
    console.log(this.store.cardsList),1500);

  }

}
</script>

<template>

  <Header />

  <Main />

</template>

<style lang="scss">

@use './scss/main.scss' as *;

</style>