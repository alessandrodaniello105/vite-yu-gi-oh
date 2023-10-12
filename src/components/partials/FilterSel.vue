<script>
export default {
  name: 'FilterSel'
}
</script>

<template>
  <div class="filter-selector">
    <span>Sono la tua search-bar preferita!</span>

    <select
      class="form-select"
      aria-label="Default select example"
      name="archetype"
      id="archetype">
      <option selected>Select Archetype</option>
      <option value="1">Alien</option>
      <option value="2">Noble Knight</option>
      <option value="3">Sinful Spoils</option>
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