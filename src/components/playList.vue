<template>
  <div>
    <h1>PlayList of Songs</h1>
    <div class="playlist" ref="playlist"></div>
  </div>
</template>

<script>
export default {
  components: {},
  methods: {
    display_song(sent_song) {
      if (this.$refs[`playlist`][`innerHTML`].includes(sent_song) === false) {
        this.$refs[`playlist`][`innerHTML`] += `<div  class="play"> ${sent_song} </div>`;
      } 
    },
  },
  mounted() {
    this.$root.$on(`get_song`, this.display_song);
  },
};
</script>

<style scoped>
.play{
    display: grid;
    place-items: center;
}
</style>
