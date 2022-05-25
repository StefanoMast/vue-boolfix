<template>
  <header>
      <div class="header">
          <div class="header-title">
            <a href="https://fontmeme.com/it/font-netflix/"><img src="https://fontmeme.com/permalink/220525/4a516320d47a6a57a93d3cb02a3ef22f.png" alt="font-netflix" border="0"></a>
          </div>
          <div class="div">
            <input type="text" placeholder="Inizia la ricerca" v-model="searchKey"> 
            <button @click="$emit('searchClick', searchKey)"><i class="fa-solid fa-magnifying-glass"></i></button>
          </div>
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
    background-color: rgb(19, 19, 19);
    width: 100%;
    height: 100px;
    position: fixed;
    display: flex;
    justify-content: space-between;
}
h1 {
        text-transform: uppercase;
        color: red;
        font-size: 4rem;
        padding: 1rem;
        display: flex;
        justify-content: flex-start;
    }
.div {
    display: flex;
    justify-content: flex-end;
}
input {
    width: 200px;
    height: 30px;
    margin-top: 1.5rem;
    background-color: rgb(34, 34, 34);
    border-style: none;
    color: white;
}

button {
    height: 30px;
    margin-top: 1.5rem;
    margin-right: 2rem;
    background-color: rgb(34, 34, 34);
    border-style: none;
}



</style>