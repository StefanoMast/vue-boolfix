<template>
  <li class="card">
      <div class="card-inner">
          <div class="card-front">
              <img 
               :src="posterUrl" alt="">
          </div>
          <div class="card-back">
           
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
                </i>
            </p>
          </div>
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
    posterUrl() {
         return this.cardObj.poster_path ? `https://image.tmdb.org/t/p/w342${this.cardObj.poster_path}` : require('../assets/img/immagine-vuota.jpg')
     }
    }

};
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.card {
  width: calc(100%/4 - 8px);
  height: 300px;
  margin: 4px;
  padding: 1rem;
  text-align: center;
  perspective: 1000px;
}

.card:hover {
    transform: rotateY(180deg);
}

.card-inner {
    width: 100%;
    height: 100%;
    position: relative;
    background-color: black;
    color: white;
    transform-style: preserve-3d;
    transition: transform .5s;
}

.language-flag {
    width: 2rem;
}

.card-front, .card-back {
    width: 100%;
    height: 100%;
    position: absolute;
    backface-visibility: hidden;
}

.card-front img {
    width: 100%;
}

.card-back {
    transform: rotateY(180deg);
}
</style>