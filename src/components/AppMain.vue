<template>
  <section class="movies">
      <div class="container">
          <h2>Film</h2>
          <ul class="list">
              <AppCard v-for="item in movies" :key="item.id" :cardObj="item"/>
          </ul>
          <h2>SerieTv</h2>
          <ul class="list">
              <AppCard v-for="item in series" :key="item.id" :cardObj="item"/>
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
        movies: Array,
        series: Array
    }, 
    data() {
        return {};
    }
};
</script>

<style lang="scss" scoped>
.movies {
    display: flex;
    flex-wrap: wrap;
    padding-top: 2rem;
}

ul {
    display: flex;
    flex-wrap: wrap;
}

</style>