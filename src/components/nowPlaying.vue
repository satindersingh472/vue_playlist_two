<template>
<!-- all playing is a parent div for all the html inside a now playing -->
  <div class="all_playing">
    <h1>Now playing from playlist</h1>
    <!-- div currently playing will have a list of now playing song -->
    <div ref="currently_playing">
      <h2>the song to be played will get displayed here</h2>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    // playing now will display the currently playing song
    playing_now(play_song) {
        this.$refs[`currently_playing`][`innerHTML`] = ``;
        this.$refs[`currently_playing`][`innerHTML`] = play_song;
      
    },
  },
  mounted() {
    // this line will listen for recieve song event and call the playing now function if it happens
    this.$root.$on(`recieve_song`, this.playing_now);
  },
};
</script>

<style scoped>
.all_playing {
  display: grid;
  width: 30vw;
}
</style>
