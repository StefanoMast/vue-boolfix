<template>
  <header>
      <div class="header">
          <h1>boolfix</h1>
          <input type="text" placeholder="ciao" v-model="searchKey"> 
          <button @click="$emit('searchClick', searchKey)">Search</button>
          <!-- //devo creare props per fare in modo che il figlio invii dati al padre
          //devo creare quindi un main che sarà il genitore in cui ci sarà dentro la search-bar. Nel mio caso è il genitore (main) che passa al figlio (header) -->
        </div>
          
      
  </header>
</template>

<script>
export default {
    name: "AppHeader",
    data() {
        return {
            searchKey: ""
        }
    },
    components: {
    
}
}
</script>

<style lang="scss" scoped>

.header {
    background-color: darkgrey;
    width: 100vh;
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