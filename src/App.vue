<template>
  <div id="app">
    <SongList :songs="songs" />
    <PlayList :songs="playSongs" />
  </div>
</template>

<script>
import SongList from "./components/SongList";
import PlayList from "./components/PlayList";

export default {
  name: "App",
  components: {
    SongList,
    PlayList
  },
  mounted: function () {
    this.$root.$on("addSong", this.addSongToPlaylist);
    this.$root.$on("removeSong", this.removeSongFromPlaylist);
  },
  methods: {
    addSongToPlaylist: function(song) {
      for (let i = 0; i < this.songs.length; i++) {
        if (this.songs[i].title == song.title) {
          this.songs.splice(i, 1);
          break;
        }
      }
      this.playSongs.push(song);
    },
    removeSongFromPlaylist: function(song) {
      for (let i = 0; i < this.playSongs.length; i++) {
        if (this.playSongs[i].title == song.title) {
          this.playSongs.splice(i, 1);
          break;
        }
      }
      this.songs.push(song);
    }
  },
  data() {
    return {
      songs: [
        {
          artist: "Kanye West",
          title: "Runaway"
        },
        {
          artist: "Tom Petty",
          title: "American Girl"
        },
        {
          artist: "Lionel Richie",
          title: "All Night Long"
        },
        {
          artist: "Stevie Wonder",
          title: "Superstition"
        },
        {
          artist: "Kings of Leon",
          title: "Beautiful War"
        }
      ],
      playSongs: []
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-left: 2.5vw;
  width: 95vw;
  min-height: 95vh;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  justify-items: center;
}
</style>
