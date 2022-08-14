<template>
  <div id="app">
  <song-list></song-list>
  <play-list></play-list>
  <now-playing></now-playing>
  </div>
</template>

<script>
import SongList from "@/components/songList.vue";
import PlayList from "@/components/playList.vue";
import NowPlaying from "@/components/nowPlaying.vue";
export default {
  name: 'App',
  components: {
    SongList,
    PlayList,
    NowPlaying
  }
}
</script>

<style scoped>
img{
  height: 100px;
  width: 100px;
}
#app{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  text-align: center;
  justify-items: center;
}
</style>
