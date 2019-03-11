<template>
  <div class="video">
    <iframe
      :src="videoUrl"
      frameborder="0"
      allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    >
    </iframe>
  </div>
</template>

<script>
export default {
  name: 'Video',
  mounted() {
    console.log(this.$route.params.video);
  },
  computed: {
    videoId() {
      return this.$route.params.video;
    },
    videoUrl() {
      return `https://www.youtube.com/embed/${this.videoId}?controls=0&playsinline=0&rel=0&autoplay=1`;
    },
  },
};
</script>

<style lang="scss" scoped>


.video {
  iframe {
    width: 100%;
    min-height: 50vh;
  }
}

</style>
