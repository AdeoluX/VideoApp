<template>
  <ul class="list-group">
    <VideoListItem
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @videoSelect="onVideoSelect"
    />
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem.vue';
export default {
  name: 'VideoList',
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video);
    },
  },
  components: {
    VideoListItem,
  },
  props: {
    videos: Array,
  },
};
</script>

<style></style>
