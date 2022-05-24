<template>
  <li class="card">
      <div class="card-">
          <h2 class="title">Titolo</h2>
          <h4 class="orginal-title">Titolo orginale</h4>
          <p class="language">Lingua</p>
          <p class="vote">Voto</p>
      </div>
  </li>
</template>

<script>
export default {
    name: "AppCard"

}
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