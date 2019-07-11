<template>
  <div class="container">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="My first Vue.js App" /> -->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList :videos="videos"></VideoList>
  </div>
</template>

<script>
// @ is an alias to /src

import axios from 'axios'
import SearchBar from '@/components/SearchBar.vue'
import VideoList from '@/components/VideoList.vue'

const API_KEY = 'AIzaSyC5dFd_cS4QfKtdha599vMyN_RoaBxzwtA'

export default {
  name: 'home',
  components: {
    SearchBar,
    VideoList
  },
  data() {
    return {
      videos: []
    }
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
        .then(response => {
          //this.videos from data func above
          this.videos = response.data.items
        })
    }
  }
}
</script>
