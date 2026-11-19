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
  background: #245c43;
  border-radius: 22px;
  padding: 30px;
  color: white;
  box-shadow: 0 15px 35px #245c4325;
}

.eyebrow {
  color: #d6bd91;
  font-size: 11px;
  letter-spacing: 3px;
  font-weight: 800;
}

.playing-content {
  text-align: center;
}

.playing-content img {
  width: 210px;
  height: 210px;
  object-fit: cover;
  border-radius: 18px;
  margin: 20px auto;
  box-shadow: 0 15px 35px #102d1e70;
}

.playing-content h2 {
  font-family: 'Playfair Display', serif;
  font-size: 26px;
  margin-bottom: 7px;
  color: #fffefa;
}

.playing-content p,
.no-song p {
  color: #d0ded4;
  font-size: 13px;
}

.music-progress {
  height: 5px;
  background: #648873;
  border-radius: 10px;
  margin-top: 30px;
}

.progress {
  width: 35%;
  height: 100%;
  background: #e4bd83;
  border-radius: 10px;
}

.time {
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  color: #d0ded4;
  margin-top: 10px;
}

.controls {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 35px;
  margin-top: 30px;
  color: #e4bd83;
}

.main-play {
  background: #e4bd83;
  color: #20392b;
  border: none;
  border-radius: 50%;
  width: 55px;
  height: 55px;
  font-size: 19px;
  cursor: pointer;
  transition: 0.3s;
}

.main-play:hover {
  transform: scale(1.1);
  background: white;
}

.no-song {
  text-align: center;
  padding: 35px 5px;
}

.music-icon {
  font-size: 65px;
  color: #e4bd83;
}

.no-song h3 {
  font-family: 'Playfair Display', serif;
  font-size: 22px;
  color: white;
}
</style>