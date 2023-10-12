<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import { store } from './components/data/store';

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
    getAPI() {
      axios.get(store.urlAPI)
        .then( res => {
          this.store.cardsList = res.data;
          // console.log(this.store.cardsList);
        })
        .catch( err => {
          console.log(err.code);
        })
    }
  },

  mounted() {
    
    this.getAPI();
    setTimeout(()=>
    console.log(this.store.cardsList),1500)

  }

}
</script>

<template>
  <h1>Hello World</h1>

  <Header />

  <Main />
  
</template>

<style lang="scss">

@use './scss/main.scss' as *;

</style>