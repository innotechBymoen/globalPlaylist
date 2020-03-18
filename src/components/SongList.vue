<template>
      <div class="song-list">
        <Song v-for="listItem in songs" :key="listItem.title" :artist="listItem.artist" :title="listItem.title" />
      </div>
</template>

<script>
import Song from "./Song.vue";

export default {
  name: "SongList",
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