<template>
  <!-- list all is parent html for all songs list -->
  <div class="list_all" ref="list_all">
    <h1>List of available songs</h1>
    <!-- song outer div is parent div for song inner div i.e it will contain list of all songs -->
    <div
      class="song_outer_div"
      v-for="song in songs"
      :key="song[`id`]"
      :song="song"
    >
      <!-- song inner div is every song in the list  and click event will call the send to playlist-->
      <div class="song_inner_div" @click="send_to_playlist">
        <button >song:{{ song[`title`] }}</button>
        <img
          :src="song[`image_url`]"
          :alt="`images is for song${song[`song_id`]}`"
        />
        <p>artist: {{ song[`artist`] }}</p>
        <p>sond_id: {{ song[`song_id`] }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    // send to plalist will set sent songs = outerHTML of clicked element's parentElement
    send_to_playlist(details) {
      if (details[`target`][`localName`] === `button`) {
        let sent_song = details[`target`][`parentElement`][`outerHTML`];
        // then it will set a global event get song which can be listened by any component with value of sent song
        this.$root.$emit(`get_song`, sent_song);
      } else {
        alert(`please press the button with song name to add song to the playlist`);
      }
    },
  },
  data() {
    return {
      songs: [
        {
          title: `Yaadgar`,
          artist: `Gulab Sidhu`,
          song_id: 1,
          image_url: `https://cover.djpunjab.is/52274/300x700/Yaadgar-Gulab-Sidhu.jpg`,
        },
        {
          title: `Zulf`,
          artist: `Nirvair Pannu`,
          song_id: 2,
          image_url: `https://cover.djpunjab.is/52273/300x700/Click---EP-Nirvair-Pannu.jpg`,
        },
        {
          title: `Godspeed`,
          artist: `Tyson Sidhu`,
          song_id: 3,
          image_url: `https://cover.djpunjab.is/52165/300x700/GODSPEED-Tyson-Sidhu.jpg`,
        },
      ],
    };
  },
};
</script>

<style scoped>
.list_all {
  text-align: center;
  display: grid;
  place-items: center;
}
img {
  display: grid;
  height: 100px;
  width: 100px;
}
.song_outer_div {
  width: 30vw;
}
.song_inner_div {
  display: grid;
  grid-template-columns: 1fr 1fr;
  place-items: center;
  width: 100%;
  background-color: bisque;
  margin: 10px 0px 10px 0px;
}
</style>
