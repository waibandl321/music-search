<template>
  <div class="result">
    <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          検索結果
        </h1>
        <p>検索キーワード： {{ $route.params.keyword }}</p>
      </v-col>
    </v-row>
    <v-row class="text-center">
      <v-col class="mb-4 albums__list">
         <v-card
         v-for="(album, i) in albums"
         :key="i"
    class="mx-auto card__item"
  >
      <v-row dense>
        <v-col cols="12">
          <v-card
            color="black"
            dark
          >
          <a :href="album.artistViewUrl" class="album__link">
            <v-img :src="album.artworkUrl100" width="100%"></v-img>
            <v-card-title class="headline" v-text="album.collectionCensoredName">{{ album.collectionCensoredName }}</v-card-title>
            <v-card-subtitle v-text="album.artistName" class="text-left">{{ album.artistName }}</v-card-subtitle>
            </a>
          </v-card>
        </v-col>
      </v-row>
  </v-card>
      </v-col>
    </v-row>
  </v-container>
    
  </div>
</template>


<script>
import axios from 'axios'
  export default {
    data() {
      return {
        albums: [],
      }
    },
    created() {
      const vm = this
      axios.get(`https://itunes.apple.com/search?term=${this.$route.params.keyword}&entity=album`)
      .then(response => {
        console.log(response.data)
        vm.albums = response.data.results
        
      })
    }
  };
</script>

<style scoped>
  .albums__list {
    display: flex;
    flex-wrap: wrap;
    margin-left: -20px;
    margin-right: -20px;
  }
  .card__item {
    box-shadow: none!important;
    border: none;
    outline: none;
    width: calc(100% / 4);
    box-sizing: border-box;
    padding: 20px;
  }
  .album__link {
    text-decoration: none;
    color: inherit;
  }
</style>