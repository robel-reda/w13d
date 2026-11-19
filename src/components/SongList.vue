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
  gap: 15px;
}

.song-card {
  display: flex;
  align-items: center;
  gap: 18px;
  background: #fffefa;
  padding: 15px;
  border: 1px solid #ebe8df;
  border-radius: 16px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px #263b2808;
}

.song-card:hover {
  transform: translateY(-4px);
  border-color: #a6bca9;
  box-shadow: 0 12px 25px #263b2815;
}

.song-card img {
  width: 72px;
  height: 72px;
  object-fit: cover;
  border-radius: 12px;
}

.song-info {
  flex: 1;
  min-width: 0;
}

.song-info h3 {
  font-family: 'Playfair Display', serif;
  font-size: 17px;
  color: #20392b;
  margin: 0 0 6px;
}

.song-info p {
  color: #777f76;
  font-size: 12px;
  margin: 0 0 5px;
}

.song-info small {
  color: #aaa99d;
  font-size: 10px;
}

.duration {
  font-size: 11px;
  color: #858a80;
}

.add-button {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: none;
  background: #245c43;
  color: white;
  font-size: 23px;
  cursor: pointer;
  transition: 0.3s;
}

.add-button:hover {
  background: #b47a46;
  transform: rotate(90deg);
}
</style>