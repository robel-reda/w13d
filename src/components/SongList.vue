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
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.song-card {
  display: flex;
  align-items: center;
  gap: 15px;
  background: #151720;
  padding: 13px;
  border: 1px solid #292b38;
  border-radius: 13px;
  transition: 0.3s;
}

.song-card:hover {
  background: #202231;
  transform: translateY(-2px);
}

.song-card img {
  width: 60px;
  height: 60px;
  object-fit: cover;
  border-radius: 9px;
}

.song-info {
  flex: 1;
  min-width: 0;
}

.song-info h3 {
  font-size: 14px;
  margin: 0 0 5px;
}

.song-info p {
  color: #aaaabd;
  font-size: 12px;
  margin: 0 0 4px;
}

.song-info small {
  color: #707386;
  font-size: 10px;
}

.duration {
  font-size: 11px;
  color: #85879a;
}

.add-button {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  border: 1px solid #a78bfa;
  background: transparent;
  color: #a78bfa;
  font-size: 22px;
  cursor: pointer;
}

.add-button:hover {
  background: #a78bfa;
  color: #111;
}
</style>