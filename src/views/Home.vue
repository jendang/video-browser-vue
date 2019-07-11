<template>
  <div class="container">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="My first Vue.js App" /> -->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <div v-if="selectedVideo === null">Loading ...</div>
      <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import axios from 'axios'
import SearchBar from '@/components/SearchBar.vue'
import VideoList from '@/components/VideoList.vue'
import VideoDetail from '@/components/VideoDetail.vue'

const API_KEY = 'AIzaSyC5dFd_cS4QfKtdha599vMyN_RoaBxzwtA'

export default {
  name: 'home',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
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
    },
    onVideoSelect(video) {
      // console.log(video)
      this.selectedVideo = video
    }
  }
  // computed: {
  //   renderMedia() {

  //     return this.data
  //   }
  // },
}
</script>

<style scoped></style>
