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
    moviesList: [],
    seriesList: []
  };
},
  methods: {
  search(searchKey) {
    axios
    .get("https://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: "9437af37c20a760ff2a23962de6d7fa4",
        query: searchKey
    },
    })
    .then((resp)=> {
      this.moviesList = resp.data.results;
    });


    axios
    .get("https://api.themoviedb.org/3/search/tv", {
       params: {
       api_key: "6b6f49a0543af0887649fa643a8df95b",
       query: searchKey,
      },
        })
        .then((resp) => {
          this.seriesList = resp.data.results;
          console.log(this.seriesList);
      });
  }
}
};
</script>

<style lang="scss">
@import "./assets/style/common.scss";

</style>
