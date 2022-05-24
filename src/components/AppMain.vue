<template>
  <div class="main">
      <ul>
          <AppCArd/>
      </ul>
  </div>
</template>

<script>
import AppCard from './AppCard.vue';
export default {
    name: "AppMain",
    components: {
        AppCard
    }
    

}
</script>

<style lang="scss">
.main {
    width: 100vh;
    height: 500px;
    background-color: aquamarine;
}

</style>