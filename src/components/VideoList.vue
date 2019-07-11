<template>
  <div>
    <ul class="list-group">
      <VideoListItem
        v-for="video in videos"
        :key="video.videoId"
        :video="video"
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
  props: ['videos'] //this is props has been v-bind in parent
}
</script>

<style scoped></style>
