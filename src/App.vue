<template>
  <div id="app">
    <h1>Warcraft 3 Soundboard</h1>
    <div class="actionButtons-wrapper">
      <button class="actionButton" @click="stopSound">Stop</button>
      <button class="actionButton" @click="pauseSound">Pause</button>
      <button class="actionButton" @click="resumeSound">Resume</button>
    </div>
    <div class="soundButtons-wrapper">
      <button 
      class="soundButton"
      @click="playSound(sound.file)" 
      type="button" 
      v-for="sound in sounds" 
      :key="sound.id">{{sound.name}}</button>
    </div>
  </div>
</template>

<script>
import SoundButton from './components/SoundButton'

export default {
  name: 'App',
  components: {
    SoundButton
  },
  data () {
    return {
      currentAudio: new Audio(),
      sounds: [
        {
          id: 1,
          name: 'Bergziege',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/bergziege.wav',
        },
        {
          id: 2,
          name: 'Blut überall',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/blut.wav',
        },
        {
          id: 3,
          name: 'Blutelfen Gewerkschaft',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/blutelfengewerkschaft.wav',
        },
        {
          id: 4,
          name: 'Dahinten hinstellen',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/dahinten_hinstellen.wav',
        },
        {
          id: 5,
          name: 'Hilfe Hilfe',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/hilfe_hilfe.wav',
        },
        {
          id: 6,
          name: 'Ich bin Roy',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/ich_bin_roy.wav',
        },
        {
          id: 7,
          name: 'Ist das ein Pferd?',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/ist_das_ein_pferd.wav',
        },
        {
          id: 8,
          name: 'Plasmaphotonengedöns',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/plasma.wav',
        },
        {
          id: 9,
          name: 'Seid ihr der König?',
          file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/66c7441f/src/assets/seid_ihr_der_k%C3%B6nig.wav',
        },

      ],
    }
  },
  methods: {
    resumeSound() {
      this.currentAudio.play();
    },
    pauseSound() {
      this.currentAudio.pause();
    },
    stopSound () {
      this.currentAudio.pause();
      this.currentAudio.currentTime = 0;
    },
    playSound (sound) {
      if(this.currentAudio.paused){
        this.currentAudio = new Audio(sound);
        this.currentAudio.play();
      }
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  dipslay: flex;
  justify-content: center;
  align-items: center;
}
button{
  padding: 0;
  margin: 0;
  border: none;
  background: none;
}
.soundButtons-wrapper{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
  max-width: 1024px;
  margin: 0 auto;
}
.soundButton{
  padding: 6px;
  margin: 6px 0;
  background: #252525;
  min-width: 75px;
  color: white;
  border-radius: 3px;
  transition: all ease .3s;
}
.soundButton:hover {
  background-color: rgba(#252525, .6);
  transform: translateY(-6px);
}

.actionButtons-wrapper{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  max-width: 1024px;
  margin: 0 auto 24px;;
}
.actionButton{
  padding: 6px;
  border: 1px solid #252525;
  border-radius: 3px;
  min-width: 75px;
  margin: 0 3px;
  background: white;
  transition: all ease .3s;
}
.actionButton:hover {
  background-color: rgba(#252525, .6);
  transform: translateY(-6px);
}

</style>
