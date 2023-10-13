<script>
import { store } from '../../data/store';
export default {
  name: 'Results',
  props: {
    cardsNum: Number
  },
  data() {
    return {
      store
    }
  }
}
</script>

<template>
  <div>Found {{ cardsNum }} cards</div>
</template>

<style lang="scss" scoped>
@use '../../scss/partials/vars' as *;
div {
  background-color: $secondary-color;
  height: 50px;
  color: white;
  font-weight: bold;
  line-height: 45px;
  padding: 0 20px;
}
</style>