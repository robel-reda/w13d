<template>
  <section class="now-playing">
    <p class="eyebrow">NOW PLAYING</p>

    <div v-if="song" class="playing-content">
      <img :src="song.image" :alt="song.title">

      <h2>{{ song.title }}</h2>
      <p>{{ song.artist }}</p>

      <div class="music-progress">
        <div class="progress"></div>
      </div>

      <div class="time">
        <span>0:00</span>
        <span>{{ song.duration }}</span>
      </div>

      <div class="controls">
        <span>⏮</span>
        <button class="main-play">▶</button>
        <span>⏭</span>
      </div>
    </div>

    <div v-else class="no-song">
      <div class="music-icon">♫</div>
      <h3>Nothing playing yet</h3>
      <p>Select a song from your playlist to get started.</p>
    </div>
  </section>
</template>

<script>
export default {
  name: "NowPlaying",

  props: {
    song: {
      type: Object,
      default: null
    }
  }
};
</script>

<style scoped>
.now-playing {
  background: linear-gradient(145deg, #24203a, #171824);
  border: 1px solid #39304f;
  border-radius: 18px;
  padding: 25px;
}

.eyebrow {
  color: #a78bfa;
  font-size: 11px;
  letter-spacing: 2px;
  font-weight: 700;
}

.playing-content {
  text-align: center;
}

.playing-content img {
  width: 180px;
  height: 180px;
  object-fit: cover;
  border-radius: 15px;
  margin: 15px auto;
  box-shadow: 0 12px 35px #0008;
}

.playing-content h2 {
  font-size: 21px;
  margin-bottom: 5px;
}

.playing-content p,
.no-song p {
  color: #aaaabd;
  font-size: 13px;
}

.music-progress {
  height: 5px;
  background: #454154;
  border-radius: 10px;
  margin-top: 25px;
}

.progress {
  width: 35%;
  height: 100%;
  background: #a78bfa;
  border-radius: 10px;
}

.time {
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  color: #aaaabd;
  margin-top: 10px;
}

.controls {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 35px;
  margin-top: 25px;
  color: #aaaabd;
}

.main-play {
  background: #a78bfa;
  color: #111;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 18px;
  cursor: pointer;
}

.no-song {
  text-align: center;
  padding: 25px 5px;
}

.music-icon {
  font-size: 55px;
  color: #a78bfa;
}

.no-song h3 {
  font-size: 17px;
}
</style>