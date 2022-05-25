<template>
  <li class="card">
      <div class="card-inner">
          <div class="card-image">
            <img class="card-img" v-if="cardObj.poster_path"
                :src="(`https://image.tmdb.org/t/p/w342${posterPath}`)"
                alt=""
            />
            <img class="card-empty"
            v-else
            src="../assets/img/immagine-vuota.jpg"
            alt="Poster_not_available"
            />
          </div>
          <h2 class="title">{{cardTitle}}</h2>
          <h4 class="orginal-title">{{cardOriginalTitle}}</h4>
          <!-- se la lingua ha la bandiera faccio vedere l'immagine -->
          
          <img 
          v-if="languageHasImage" class="language-flag" 
          :src="require(`../assets/img/${cardObj.original_language}.png`)" 
          :alt="cardObj.original_language"
          />
        
          <p v-else class="language">{{cardObj.original_language}}</p>
          <p class="vote">Voto: {{filledStars}}</p>
          <p>
              <i v-for="n in filledStars" :key="n" class="fas fa-star" :class="n <= 5 ? 'fas' : 'far'">
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
            flags: ["en", "it", "el", "es", "fr", "pt", "sv", "ja", "sh"]
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
    },
    posterPath() {
         return this.cardObj.poster_path;
     }
    }

};
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.card {
  width: calc(100%/5 - 8px);
  margin: 4px;
  padding: 1rem;
  text-align: center;
    
}

.language-flag {
    width: 2rem;
}

.card-img {
    width: 100%;
    height: 300px;
}

.card-empty {
    width: 100%;
    height: 300px;
}

</style>