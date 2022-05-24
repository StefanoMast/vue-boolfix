<template>
  <div id="app">
    <AppHeader @searchClick="search"/>
    <AppMain :movies="moviesList"/>
  </div>


</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from "axios";


export default {
    name: "App",
    components: {
    AppHeader,
    AppMain
},
data() {
  return {
    apiKey: "9437af37c20a760ff2a23962de6d7fa4",
    moviesList: []
  }
},
  methods: {
  search(searchKey) {
    axios
    .get("https://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: this.apiKey,
        query: searchKey
    }}
    )
    .then((resp)=> {
      this.moviesList = resp.data.results;
    });
  }
}
};
</script>

<style lang="scss">
@import "./assets/style/common.scss";

</style>
