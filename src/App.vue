<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <VideoList :videos="videos" @videoSelect="onVideoSelect" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
const API_KEY = 'AIzaSyDOlvVVY1AZ8JJ-e01IQWjzmUTpb9np5yM';
export default {
  components: { SearchBar, VideoList },
  name: 'App',
  data() {
    return {
      videos: [],
    };
  },
  methods: {
    onTermChange: function (searchTerm) {
      console.log(searchTerm);
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        });
    },
    onVideoSelect(video) {
      console.log(video);
    },
  },
};
</script>
