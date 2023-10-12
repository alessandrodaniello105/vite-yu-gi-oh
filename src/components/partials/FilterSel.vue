<script>
export default {
  name: 'FilterSel',
  data() {
    return {
      filterStr: ''
    }
  },
  methods: {
    testClick() {  
    console.log(this.filterStr);
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
      name="archetype"
      id="archetype">
      <option selected>Select Archetype</option>
      <option @click="this.testClick" value="Alien">Alien</option>
      <option @click="this.testClick" value="Noble Knight">Noble Knight</option>
      <option @click="this.testClick" value="Sinful Spoils">Sinful Spoils</option>
    </select>

  </div>
</template>

<style lang="scss" scoped>
@use '../../scss/partials/vars' as *;

.filter-selector {
  background-color: $primary-color;
  select {
    width: 200px;
  }
} 
</style>