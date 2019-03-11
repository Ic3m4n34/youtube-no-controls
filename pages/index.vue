<template>
  <section class="container">
    <div class="control has-icons-left has-icons-right">
      <input
        class="input is-large"
        v-model="video"
        type="text"
        placeholder="Youtube Link"
        @keyup.enter="goToVideo"
        @paste="checkLinkValidity"
      >
      <span class="icon is-medium is-left">
        <i class="fab fa-youtube" />
      </span>
      <span class="icon is-medium is-right">
        <i
          :class="checkedCssClass"
          class="fas fa-check"
        />
      </span>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      video: null,
      linkIsValid: false,
    };
  },
  methods: {
    goToVideo() {
      this.$router.push(`/video/${this.videoId}`);
    },
    checkLinkValidity() {
      if (this.videoId.length > 0 && this.video.includes('youtu')) this.linkIsValid = true;
    },
  },
  computed: {
    videoId() {
      return this.video.replace('https://youtu.be/', '');
    },
    checkedCssClass() {
      return this.linkIsValid ? 'fa-check--checked' : '';
    },
  },
};
</script>

<style lang="scss" scoped>

.fa-check {
  &--checked {
    color: green;
  }
}

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
