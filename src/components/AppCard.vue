<template>
  <li class="card">
      <div class="card-inner">
          <img
            v-if="cardObj.poster_path"
            :src="`http://image.tmdb.org/t/p/w300/${object.poster_path}`"
            :alt="cardTitle"
            />
          <img
            v-else
            src="../assets/img/immagine-vuota.jpg"
            alt="Poster_not_available"
            />
          <h2 class="title">{{cardTitle}}</h2>
          <h4 class="orginal-title">{{cardOriginalTitle}}</h4>
          <!-- se la lingua ha la bandiera faccio vedere l'immagine -->
          
          <img 
          v-if="languageHasImage" class="language-flag" 
          :src="require(`../assets/img/${cardObj.original_language}.png`)" 
          :alt="cardObj.original_language"
          />
          <!-- altrimenti faccio vedere il testo -->
          <p v-else class="language">{{cardObj.original_language}}</p>
          <p class="vote">Voto: {{cardObj.vote_average}}</p>
          <p>
              <i v-for="n in 5" :key="n" class="fas fa-star" :class="n <= filledStars ? 'fas' : 'far'">
    <!-- //se n è minore o uguale al voto, allora metto *, altrimenti metto # -->
              </i>
          </p>
          
    </div> 
  </li>
</template>

<script>
export default {
    name: "AppCard",
    props: {
        cardObj: Object
    },
    data() {
        return {
            flags: ["en", "it"]
        }
    },
    computed: {
    languageHasImage() {
        return this.flags.includes(this.cardObj.original_language);
    },
    cardTitle() {
        return this.cardObj.title ? this.cardObj.title : this.cardObj.name;
    },
    cardOriginalTitle () {
        return this.cardObj.orginal_title ? this.cardObj.orginal_title : this.cardObj.orginal_name;
    },
    filledStars() {
        return Math.ceil(this.cardObj.vote_average / 2);
    }
    }

};
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.card {
  width: calc(100%/4 - 8px);
  margin: 4px;
  padding: 1rem;
  border: 1px solid black;
  text-align: center;
    
}

.language-flag {
    width: 2rem;
}

</style>