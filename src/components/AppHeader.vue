<template>
  <header>
      <div class="header">
          <h1>boolfix</h1>
          <input type="text" placeholder="ciao"> 
      </div>
  </header>
</template>

<script>
export default {
    name: "AppHeader",
    components: {
    
    }
}
</script>

<style lang="scss" scoped>

.header {
    background-color: darkgrey;
    height: 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    h1 {
    text-transform: uppercase;
    color: red;
    }
    

}

</style>