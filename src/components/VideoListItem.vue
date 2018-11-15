<template>
    
            <li class="list-group-item media" @click="onVideoSelect">
                
                <img class ="mr-3" v-bind:src="thumbnailUrl" />
                <div class="media-body">
                    {{ sing_vid_obj.snippet.title}}
                    
                </div>

            </li>

</template>

<script>
export default {
  name: "VideoListItem",
  props: ["sing_vid_obj"],
  computed: { 
    thumbnailUrl() {
      return this.sing_vid_obj.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect: function(event) {
      this.$emit('VideoSelect', this.sing_vid_obj);
    
    }
  }
};
</script>
<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>
