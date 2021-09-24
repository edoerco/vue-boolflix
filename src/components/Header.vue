<template>
  <header>
    <div class="container">
      <h1>BOOLFLIX</h1>
      <div class="search">
        <input type="text" placeholder="Cerca Serie" name="" id="">
        <button>Cerca</button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/vars.scss';

header {
  height: 100px;
  width: 100%;
  background-color: $primary;

  .container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    width: 95%;
    margin: 0 auto;

    h1 {
      color: $secundary
    }
  }
}

</style>
