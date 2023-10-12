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
          // console.log(this.store.cardsList);
        })
        .catch( err => {
          console.log(err.code);
        })
    }
  },

  mounted() {
    
    this.getAPI(store.urlAPI);

    console.log(`${store.urlAPI}&archetype=alien`);

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