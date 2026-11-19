<template>
  <div class="app">
    <header class="header">
      <div class="logo">♫ MP3 {2}</div>
      <span class="header-label">YOUR PERSONAL MUSIC SPACE</span>
    </header>

    <main class="container">
      <section class="hero">
        <p class="eyebrow">YOUR MUSIC. YOUR MOMENT.</p>
        <h1>Feel every <span>beat.</span></h1>
        <p class="subtitle">
          Discover your favourite songs and create your own playlist.
        </p>
      </section>

      <div class="music-layout">

        <section class="songs-section">
          <div class="section-heading">
            <div>
              <p class="eyebrow">DISCOVER</p>
              <h2>Available Songs</h2>
            </div>
            <span class="count">{{ songs.length }} TRACKS</span>
          </div>

          <SongList
            :songs="songs"
            @add-song="addToPlaylist"
          />
        </section>

        <aside class="side-section">

          <div class="playlist-panel">
            <div class="section-heading">
              <div>
                <p class="eyebrow">YOUR COLLECTION</p>
                <h2>My Playlist</h2>
              </div>
              <span class="count">{{ playlist.length }}</span>
            </div>

            <PlayList
              :playlist="playlist"
              :currentSong="currentSong"
              @play-song="playSong"
              @remove-song="removeSong"
            />
          </div>

          <NowPlaying :song="currentSong" />

        </aside>
      </div>
    </main>

    <footer>
      MP3 {2}© 2026 — MADE FOR MUSIC LOVERS
    </footer>
  </div>
</template>

<script>
import SongList from "./components/SongList.vue";
import PlayList from "./components/PlayList.vue";
import NowPlaying from "./components/NowPlaying.vue";

export default {
  name: "App",

  components: {
    SongList,
    PlayList,
    NowPlaying
  },

  data() {
    return {
      songs: [
        {
          id: 1,
          title: "Blinding Lights",
          artist: "The Weeknd",
          album: "After Hours",
          duration: "3:20",
          image: "https://picsum.photos/seed/song1/300"
        },
        {
          id: 2,
          title: "Levitating",
          artist: "Dua Lipa",
          album: "Future Nostalgia",
          duration: "3:23",
          image: "https://picsum.photos/seed/song2/300"
        },
        {
          id: 3,
          title: "As It Was",
          artist: "Harry Styles",
          album: "Harry's House",
          duration: "2:47",
          image: "https://picsum.photos/seed/song3/300"
        },
        {
          id: 4,
          title: "Starboy",
          artist: "The Weeknd",
          album: "Starboy",
          duration: "3:50",
          image: "https://picsum.photos/seed/song4/300"
        },
        {
          id: 5,
          title: "Flowers",
          artist: "Miley Cyrus",
          album: "Endless Summer Vacation",
          duration: "3:20",
          image: "https://picsum.photos/seed/song5/300"
        },
        {
          id: 6,
          title: "Perfect",
          artist: "Ed Sheeran",
          album: "Divide",
          duration: "4:23",
          image: "https://picsum.photos/seed/song6/300"
        }
      ],

      playlist: [],
      currentSong: null
    };
  },

  methods: {
    addToPlaylist(song) {
      const alreadyAdded = this.playlist.some(
        item => item.id === song.id
      );

      if (!alreadyAdded) {
        this.playlist.push(song);
      }
    },

    playSong(song) {
      this.currentSong = song;
    },

    removeSong(songId) {
      this.playlist = this.playlist.filter(
        song => song.id !== songId
      );

      if (this.currentSong && this.currentSong.id === songId) {
        this.currentSong = null;
      }
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap');

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background: #0b0d12;
  color: #ffffff;
  font-family: 'DM Sans', sans-serif;
}

button {
  font-family: inherit;
}

.app {
  min-height: 100vh;
}

.header {
  height: 25px;
  padding: 0 8%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #242630;
}

.logo {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 24px;
  font-weight: 700;
  color:yellowgreen;
  letter-spacing: 1px;
}

.header-label,
.count {
  font-size: 11px;
  letter-spacing: 2px;
  color: #888a9b;
}

.container {
  max-width: 1250px;
  margin: auto;
  padding: 65px 30px;
}

.hero {
  margin-bottom: 55px;
}

.eyebrow {
  font-size: 11px;
  color: #a78bfa;
  letter-spacing: 2px;
  font-weight: 700;
}

.hero h1 {
  font-family: 'Space Grotesk', sans-serif;
  font-size: clamp(42px, 7vw, 72px);
  margin: 15px 0;
}

.hero h1 span {
  color: #a78bfa;
}

.subtitle {
  color: #9698a7;
  font-size: 15px;
}

.music-layout {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 35px;
}

.section-heading {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
}

.section-heading h2 {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 23px;
  margin: 5px 0;
}

.side-section {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.playlist-panel {
  background: #151720;
  padding: 25px;
  border-radius: 18px;
  border: 1px solid #292b38;
}

footer {
  text-align: center;
  color: #686a78;
  font-size: 10px;
  letter-spacing: 2px;
  padding: 35px;
  border-top: 1px solid #242630;
}

@media (max-width: 850px) {
  .music-layout {
    grid-template-columns: 1fr;
  }

  .container {
    padding: 40px 20px;
  }
}
</style>