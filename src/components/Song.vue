<template>
  <div class="song">
    <i>{{artist}}</i>
    <p>{{title}}</p>
    <svg @click="addSong" class="svg-circleplus" viewBox="0 0 100 100">
      <circle class='shadow-circle' cx="50" cy="50" r="45" stroke-width="7.5" />
      <line x1="32.5" y1="50" x2="67.5" y2="50" stroke-width="5" />
      <line x1="50" y1="32.5" x2="50" y2="67.5" stroke-width="5" />
    </svg>
  </div>
</template>

<script>
export default {
  name: "Song",
  props: {
    title: {
      type: String,
      required: true
    },
    artist: {
      type: String,
      required: true
    }
  },
  methods: {
    addSong: function() {
      this.$root.$emit("addSong", { title: this.title, artist: this.artist });
    }
  }
};
</script>

<style scoped>
.song {
  width: 50%;
  margin: 2.5vh 0;
  padding: 2vh 0;
  box-shadow: 5px 5px 10px grey;
}
.svg-circleplus {
  height: 40px;
  stroke: white;
  fill: green;
}
.svg-circleplus:hover {
    cursor: pointer;
}
</style>