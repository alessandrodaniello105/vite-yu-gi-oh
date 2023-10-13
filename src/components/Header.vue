<script>
export default {
  name: 'Header'
}
</script>

<template>
  <header>
    <div class="img-box">
      <img src="/logo.png" alt="">
    </div>
    <h1 class="text-ctm">Yu-Gi-Oh API</h1>
  </header>
</template>

<style lang="scss">
header {
  height: 100px;
  background-color: #FFFFFF;
  position: absolute;
  top: 0;
  display: flex;
  align-items: center;
  .img-box {
    align-self: center;
      vertical-align: middle;
      height: 45%;
    img {
      vertical-align: middle;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>