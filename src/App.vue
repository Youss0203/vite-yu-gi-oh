<template lang="">
  <AppHeader/>
  <main>
    <AppSearch/>
    <CharactersList :charactersList="characters"/>
  </main>
</template>
<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import CharactersList from './components/CharactersList.vue';
import AppSearch from './components/AppSearch.vue';
export default {
  components:{
    AppHeader,
    CharactersList,
    AppSearch,
  },
  data() {
    return {
      characters:[],
    }
  },
  methods:{
    getCharacters(){
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=30&offset=0')
  .then( (response) => {
    // handle success
    console.log(response);
    this.characters=response.data.data
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
    }
  },
  created() {
    this.getCharacters();
  },
}
</script>
<style lang="scss">
  @use "./styles/general.scss";

  main{
    background-color: #D48F38;
    padding:2rem;
  }
</style>