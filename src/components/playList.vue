<template>
  <!-- playlist all will contain the list of all songs in the playlist -->
  <div class="playlist_all">
    <h1>PlayList of Songs</h1>
    <!-- playlist items is a parent div for list of songs in a playlist -->
    <h2>
      please add songs from songs list
    </h2>
    <div class="playlist_items" ref="playlist" @click="send_to_play"></div>
  </div>
</template>

<script>
export default {
  components: {},
  methods: {
    // send to play function will check if button only is clicked in a div and set play song = outerhtml of target's parentelement
    send_to_play(details) {
      if (details[`target`][`localName`] === `button`) {
        let play_song = details[`target`][`parentElement`][`outerHTML`];
        this.$root.$emit(`recieve_song`, play_song);
        // if clicked somewhere else on the div then alert message will get displayed
      } else {
        alert(`please press the button name with song to play`);
      }
    },
    // display song will display song by the value it got from sent song from songlist component
    display_song(sent_song) {
      // if conditional will check if there is any previous value of sent song is there inside the playlist ref
      // if there is h2 element present before playlist ref it will get deleted
      // and if there is a value present it will prevent the repetion of adding a song to playlist
      if (this.$refs[`playlist`][`innerHTML`].includes(sent_song) === false &&  this.$refs[`playlist`][`previousElementSibling`][`localName`] === `h2`) {
        this.$refs[`playlist`][`previousElementSibling`][`outerHTML`] = "";
        this.$refs[`playlist`][`innerHTML`] += sent_song;
        // now the previous h2 element got deleted and now the statment wil add other songs one by one
      } else if(this.$refs[`playlist`][`innerHTML`].includes(sent_song) === false && this.$refs[`playlist`][`previousElementSibling`][`localName`] !== `h2`){
        this.$refs[`playlist`][`innerHTML`] += sent_song;
      }
      // if one is clicked more than once there will be an error
       else if (this.$refs[`playlist`][`innerHTML`].includes(sent_song)=== true )  {
        alert(`Cannot add one song more than once`);

      }
    },
  },
  mounted() {
    // this line will listen for get song event then call the display song when get song happens
    this.$root.$on(`get_song`, this.display_song);
  },
};
</script>

<style scoped>
.playlist_all {
  width: 30vw;
}
.playlist_items {
  display: grid;
  gap: 10px;
}
</style>
