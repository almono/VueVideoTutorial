<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList v-bind:videos="videos" @videoClick="createVideoDetail"></VideoList>
    </div>
  </div>
</template>


<script>

import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = 'API KEY';

export default {
  name: 'App',
  components: {
    SearchBar: SearchBar,
    VideoList: VideoList,
    VideoDetail: VideoDetail
  },
  data: function() {
    return {
      videos: [],
      selectedVideo: null
     };
  },
  methods: {
    createVideoDetail(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {

      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(
        response => {
          this.videos = response.data.items;
        }
      );

    }
  }
};

</script>
