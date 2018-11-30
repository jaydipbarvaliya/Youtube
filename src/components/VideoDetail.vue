<template>
    <div v-if="toDetail" class="col-md-8">

        <div class="embed-responsive embed-responsive-16by9">
            <iframe  class="embed-responsive-item" v-bind:src="urlgenerator" ></iframe>
        </div> 
    
        <div class="details">
            <h4>{{toDetail.snippet.title}}</h4>
            <p>{{toDetail.snippet.description}}</p>
            

        </div>

        
    </div>    
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["toDetail"],
  computed: {
    urlgenerator() {
        const videoId1=this.toDetail.id.videoId;
      return 'https://www.youtube.com/embed/'+videoId1;
    }
  }
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid ddd;
  border-radius: 4px;
}
</style>
