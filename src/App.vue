<template>
    <div class="container">
        
        <SearchBar v-on:termChange="onTermChange"></SearchBar>
        <div class="row">

          <VideoDetail v-bind:toDetail="selectedvideo"></VideoDetail>
        <VideoList v-bind:videos="videos" @mainparent="MainParent"></VideoList>
        
        </div>
        



    </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";
const API_KEY = "AIzaSyBn9s31zseps2qZmiFHTwbRk0FsDgSbsMw";
export default {
  name: "App",

  data: function() {
    return { videos: [], selectedvideo: null};
},
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },

  methods: {
    onTermChange: function(searchTerm) {
      console.log(searchTerm);
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          this.videos = response.data.items;
        });
    },
    MainParent: function(video_finale) {
     this.selectedvideo=video_finale;
    }
  }
};
</script>

