<template>
  <div class="song-list">

    <div
      v-for="song in songs"
      :key="song.id"
      class="song-card"
    >
      <img :src="song.image" :alt="song.title">

      <div class="song-info">
        <h3>{{ song.title }}</h3>
        <p>{{ song.artist }}</p>
        <small>{{ song.album }}</small>
      </div>

      <span class="duration">{{ song.duration }}</span>

      <button
        class="add-button"
        @click="$emit('add-song', song)"
      >
        +
      </button>
    </div>

  </div>
</template>

<script>
export default {
  name: "SongList",

  props: {
    songs: {
      type: Array,
      required: true
    }
  },

  emits: ["add-song"]
};
</script>

<style scoped>
.song-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 20px;
}

.song-card {
  background: #17171b;
  border: 1px solid #302b22;
  border-radius: 16px;
  padding: 14px;
  transition: 0.3s ease;
}

.song-card:hover {
  transform: translateY(-7px);
  border-color: #d6b36a;
  box-shadow: 0 12px 30px #0008;
}

.song-card img {
  width: 100%;
  aspect-ratio: 1;
  object-fit: cover;
  border-radius: 11px;
}

.song-card h3 {
  color: #f5f0e6;
  font-size: 17px;
  margin: 14px 0 5px;
}

.song-card p {
  color: #96939a;
  font-size: 13px;
}

.song-card button {
  width: 100%;
  background: #d6b36a;
  color: #111;
  border: none;
  border-radius: 8px;
  padding: 11px;
  font-weight: 700;
  cursor: pointer;
  transition: 0.2s;
}

.song-card button:hover {
  background: #f0d18f;
}
</style>