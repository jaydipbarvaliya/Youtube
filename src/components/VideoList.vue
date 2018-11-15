<template>
    <ul class="list-group col-md-4">
   <VideoListItem 
        v-for="s_video in videos" v-bind:sing_vid_obj="s_video" @VideoSelect="clicko">
    </VideoListItem>
    
   </ul>
    
    <!-- v-bind:videos="videos" -->
</template>
<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  props: ["videos"],
  components: {
    VideoListItem
  },
  methods:{
    clicko: function(clicko_video ){
      this.$emit('mainparent',clicko_video);
    }
  }

};
</script>
<style>
</style>

