<template>
  <li class="list-group-item media d-flex" @click="selectVideo">
    <img class="mr-3" :src="thumbnailsUrl" />
    <div class="media-body">
      <span class="" v-html="video.snippet.title"></span>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: null,
  },
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    selectVideo() {
      this.$emit("selectedVideo", this.video);
    },
  },
};
</script>

<style scoped>
li {
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}
</style>