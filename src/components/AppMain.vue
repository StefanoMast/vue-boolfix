<template>
  <section class="movies">
      <div class="container">
          <ul>
              <AppCard v-for="item in movies" :key="item.id" :movie="item"/>
          </ul>
      </div>

  </section>
      
</template>

<script>
import AppCard from './AppCard.vue';

export default {
    name: "AppMain",
    components: {
        AppCard
    }, 
    props: {
        movies: Object
    }
    

};
</script>

<style lang="scss">
.movies {
    padding-top: 2rem;

}
.movies-list {
    display: flex;
    flex-wrap: wrap;
}


</style>