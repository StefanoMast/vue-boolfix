<template>
  <li class="card">
      <div class="card-inner">
          <h2 class="title">{{movie.title ? movie.title : movie.name}}</h2>
          <h4 class="orginal-title">{{movie.original_title ? movie.original_title : movie.original_title}}</h4>
          <div class="language">
            <div v-if="movie.orginal_language === 'it'">
                <p>Lingua:</p>
                <span :class="`fi fi-it`"></span>
            </div>
            <div v-else-if="movie.orginal_language === 'gb'">
                <p>Lingua:</p>
                <span :class="`fi fi-gb`"></span>
            </div>
            <div v-else-if="movie.orginal_language === 'es'">
                <p>Lingua:</p>
                <span :class="`fi fi-es`"></span>
            </div>
            <div v-else-if="movie.original_language === 'fr'">
                <p>Lingua:</p>
                <span :class="`fi fi-fr`"></span>
            </div>
            <div v-else>
                <p>Lingua:</p>{{movie.original_language}}
            </div>
          </div>
          <div class="vote">{{movie.original_vote.average}}</div>
    </div>
  </li>
</template>

<script>
export default {
    name: "AppCard",
    props: {
        movie: Object
    },
    data() {
        return {
        };
    },

};
</script>

<style lang="scss" scoped>
@import "~flag-icons/css/flag-icons.css";
@import "~@fortawesome/fontawesome-free/css/all.min.css";


.card {
  width: calc(100%/4 - 8px);
  margin: 4px;
  padding: 1rem;
  border: 1px solid black;
  text-align: center;
    
}

</style>