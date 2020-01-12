<template>
  <ul class="list-group col-md-4">
    <div class="video-list">Videos list ({{ videos.length }})</div>
    <VideoListItem v-for="video in videos"
                   v-bind:video="video"
                   v-bind:key="video.etag"
                   @videoClick="videoClicked">
    </VideoListItem>
  </ul>
</template>

<script>

import VideoListItem from './VideoListItem';

export default {
  name: 'VideoList',
  components: {
    VideoListItem: VideoListItem
  },
  methods: {
    videoClicked(video) {
      this.$emit('videoClick',video);
    }
  },
  props: ['videos']
};
</script>

<style>
  .video-list {
    padding: 10px 20px 10px 20px;
    border: 1px solid rgba(0, 0, 0, 0.125);
    margin-bottom: 5px;
  }
</style>
