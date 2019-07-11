<template>
  <div class="col-md-4">
    <ul class="list-group">
      <VideoListItem
        v-for="video in videos"
        :key="video.videoId"
        :video="video"
        @videoSelect="onVideoSelect"
      ></VideoListItem>
    </ul>
  </div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem.vue'

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: ['videos'], //this is props has been v-bind in parent
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video)
    }
  }
}
</script>

<style scoped></style>
