<template>
  <div class="playlist">

    <p v-if="playlist.length === 0" class="empty-message">
      Your playlist is empty.
      <br>
      Add some songs to get started!
    </p>

    <div
      v-for="song in playlist"
      :key="song.id"
      class="playlist-song"
    >
      <img :src="song.image" :alt="song.title">

      <div class="song-info">
        <h4>{{ song.title }}</h4>
        <p>{{ song.artist }}</p>
      </div>

      <button
        class="play-button"
        @click="$emit('play-song', song)"
      >
        ▶
      </button>

      <button
        class="remove-button"
        @click="$emit('remove-song', song.id)"
      >
        ×
      </button>
    </div>

  </div>
</template>

<script>
export default {
  name: "PlayList",

  props: {
    playlist: {
      type: Array,
      required: true
    },

    currentSong: {
      type: Object,
      default: null
    }
  },

  emits: ["play-song", "remove-song"]
};
</script>

<style scoped>
.playlist {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.empty-message {
  text-align: center;
  color: #85879a;
  line-height: 2;
  padding: 25px 5px;
  font-size: 13px;
}

.playlist-song {
  display: flex;
  align-items: center;
  gap: 12px;
  background: #202230;
  padding: 10px;
  border-radius: 10px;
}

.playlist-song img {
  width: 45px;
  height: 45px;
  object-fit: cover;
  border-radius: 8px;
}

.song-info {
  flex: 1;
  min-width: 0;
}

.song-info h4 {
  margin: 0 0 5px;
  font-size: 12px;
}

.song-info p {
  margin: 0;
  color: #85879a;
  font-size: 11px;
}

.play-button,
.remove-button {
  border: none;
  cursor: pointer;
  background: transparent;
  font-size: 16px;
}

.play-button {
  color: #a78bfa;
}

.remove-button {
  color: #ff7777;
  font-size: 22px;
}
</style>