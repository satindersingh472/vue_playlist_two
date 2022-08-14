<template>
  <div class="list_all" ref="list_all">
    <h1>List of available songs</h1>
    <div
      class="song_outer_div"
      v-for="song in songs"
      :key="song[`id`]"
      :song="song"
    >
      <div class="song_inner_div">
        <button @click="send_to_playlist">song:{{ song[`title`] }}</button>
         <img
          :src="song[`image_url`]"
          :alt="`images is for song${song[`song_id`]}`"/> 
        <p>artist: {{ song[`artist`] }}</p>
        <p>sond_id: {{ song[`song_id`] }}</p>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    send_to_playlist(details) {
      let sent_song = details[`target`][`parentElement`][`innerHTML`];
      this.$root.$emit(`get_song`, sent_song);
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
.list_all{
    text-align: center;
    display:grid;
    place-items: center;
}
img {
  display: grid;
  height: 100px;
  width: 100px;
}
.song_outer_div{
    width: 30vw;
}
.song_inner_div {
  display: grid;
  grid-template-columns: 1fr 1fr ;
  place-items: center;
  width: 100%;
  background-color: bisque;
 margin: 10px 0px 10px 0px;
}
</style>
