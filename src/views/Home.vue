<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="My first Vue.js App" /> -->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <h1>Hi there!</h1>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
import SearchBar from '@/components/SearchBar.vue'
const API_KEY = 'AIzaSyC5dFd_cS4QfKtdha599vMyN_RoaBxzwtA'

export default {
  name: 'home',
  components: {
    // HelloWorld,
    SearchBar
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            // maxResults: 5,
            part: 'snippet', //all information about video
            q: searchTerm
          }
        })
        .then(response => console.log(response))
    }
  }
}
</script>
