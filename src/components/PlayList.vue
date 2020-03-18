<template>
    <div class="song-list">
      <Song v-for="song in songs" :key="song.title" :artist="song.artist" :title="song.title" />
    </div>
</template>

<script>
import Song from "./PlaySong.vue";

export default {
  name: "PlayList",
  components: {
    Song
  },
  props: {
    songs: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.song-list {
  width: 40vw;
  height: 60vh;
  overflow: auto;
  box-shadow: 10px 10px 20px grey;
  display: grid;
  justify-items: center;
  align-items: center;
}
</style>