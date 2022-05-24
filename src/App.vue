<template>
  <div class="container">
    <AppHeader @searchClick="search"/>
    <AppMain/>
  </div>


</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue'
import axios from "axios";


export default {
    name: "App",
    components: {
    AppHeader,
    AppMain
},
  methods: {
  search(searchKey) {
    axios.get("https://api.themoviedb.org/3/search/movie?api_key=9437af37c20a760ff2a23962de6d7fa4&query=vita")
    .then((resp)=> {
      console.log(resp);
    });
  }
}
}
</script>

<style lang="scss">
@import "./assets/style/common.scss";

</style>
