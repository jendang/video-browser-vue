<template>
  <div>
    <li class="list-group-item media" @click="onVideoSelect">
      <!-- <img :src="video.snippet.thumbnails.default.url" /> -->
      <img class="mr-3" :src="thumbnailUrl" />
      <div class="media-body">{{ video.snippet.title }}</div>
    </li>
  </div>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  computed: {
    //format data inside the templates
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video)
    }
  }
}
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}
</style>
