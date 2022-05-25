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
    apiKey: "02271e765b18b4b64347f49cbd81a43a",
    moviesList: [],
    seriesList: []
  };
},
  methods: {
  search(searchKey) {
    const options = {
      params: {
        api_key: this.apiKey,
        query: searchKey,
      },
    };
    // sintassi chiamate multiple
    const reqMovies = axios.get("https://api.themoviedb.org/3/search/movie", options);
    const reqSeries = axios.get("https://api.themoviedb.org/3/search/tv", options);

    axios.all([reqMovies, reqSeries]). then(resp => {
      this.moviesList = resp[0].data.results;
      this.seriesList = resp[1].data.results;   
    });
    // sintassi chiamate separate
    // axios
    // .get("https://api.themoviedb.org/3/search/movie", options)
    // .then((resp)=> {
    //   this.moviesList = resp.data.results;
    // });


    // axios
    // .get("https://api.themoviedb.org/3/search/tv", options)
    //     .then((resp) => {
    //       this.seriesList = resp.data.results;
    //   });
  }
}
};
</script>

<style lang="scss">
@import "./assets/style/common.scss";

</style>
