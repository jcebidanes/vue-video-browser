<template>
  <ul class="list-group col-sm-4">
    <video-list-item
      @selectedVideo="onVideoSelect"
      :video="video"
      v-for="video in videos"
      :key="video.etag"
    />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";

export default {
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: {
    videos: Array,
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("selectedVideo", video);
    },
  },
};
</script>

<style>
</style>