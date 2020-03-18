<template>
  <div class="song">
    <i>{{artist}}</i>
    <p>{{title}}</p>
    <svg @click="removeSong" class="svg-circleminus" viewBox="0 0 100 100">
      <circle class="shadow-circle" cx="50" cy="50" r="45" stroke-width="7.5" />
      <line x1="32.5" y1="50" x2="67.5" y2="50" stroke-width="5" />
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
    removeSong: function() {
      this.$root.$emit("removeSong", {
        title: this.title,
        artist: this.artist
      });
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
.svg-circleminus {
  height: 40px;
  stroke: white;
  fill: red;
}
.svg-circleminus:hover {
    cursor: pointer;
}
</style>