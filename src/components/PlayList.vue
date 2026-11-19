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
  gap: 13px;
}

.empty-message {
  text-align: center;
  color: #92968c;
  line-height: 2;
  padding: 30px 5px;
  font-size: 13px;
}

.playlist-song {
  display: flex;
  align-items: center;
  gap: 12px;
  background: #f5f3ed;
  padding: 12px;
  border-radius: 13px;
  transition: 0.3s;
}

.playlist-song:hover {
  background: #eaece3;
  transform: translateX(3px);
}

.playlist-song img {
  width: 52px;
  height: 52px;
  object-fit: cover;
  border-radius: 10px;
}

.song-info {
  flex: 1;
  min-width: 0;
}

.song-info h4 {
  font-family: 'Playfair Display', serif;
  color: #20392b;
  margin: 0 0 5px;
  font-size: 14px;
}

.song-info p {
  margin: 0;
  color: #858a80;
  font-size: 11px;
}

.play-button,
.remove-button {
  border: none;
  cursor: pointer;
  background: transparent;
  font-size: 17px;
  transition: 0.2s;
}

.play-button {
  color: #245c43;
}

.play-button:hover {
  color: #b47a46;
  transform: scale(1.2);
}

.remove-button {
  color: #c46e61;
  font-size: 23px;
}

.remove-button:hover {
  transform: scale(1.2);
}
</style>
