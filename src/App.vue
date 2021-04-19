<template>
  <div class="container">
    <search-bar @termChange="onTermChange" />
    <div class="row">
      <video-detail :video="selectedVideo" />
      <video-list @selectedVideo="onVideoSelect" :videos="responseVideosList" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail.vue";

const API_KEY = "ADD_YOUR_YOUTUBE+API_KEY_HERE";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      responseVideosList: [],
      selectedVideo: null,
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((response) => {
          this.responseVideosList = response.data.items;
        });
    },

    onVideoSelect(video) {
      this.selectedVideo = video;
    },
  },
};
</script>


