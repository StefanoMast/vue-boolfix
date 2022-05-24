<template>
  <li class="card">
      <div class="card-inner">
          <h2 class="title">{{movie.title}}</h2>
          <h4 class="orginal-title">{{movie.original_title}}</h4>
          <p class="language">{{movie.original_language}}</p>
          <p class="vote">Voto: {{movie.vote_avarage}}</p>
      </div>
  </li>
</template>

<script>
export default {
    name: "AppCard"

};
</script>

<style lang="scss" scoped>
.card {
    &-inner {
        width: calc(100%/4 - 8px);
        margin: 4px;
        padding: 1rem;
        border: 1px solid black;
        text-align: center;
    }
}

</style>