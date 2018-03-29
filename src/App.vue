<template>
  <div id="app">
    <div class="soundButton">
      <button @click="playSound(sound_1.file)" type="button">{{sound_1.name}}</button>
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
      sound_1: {
        id: 1,
        name: 'Bergziege',
        file: 'https://cdn.rawgit.com/pWnH/soundboard_for_pnp/c4e8af95/src/bergziege.mp3',
      },
    }
  },
  methods: {
    playSound (sound) {
      let audio = new Audio(sound);
      setTimeout(() => {
        audio.play();
      }, 2000);
      
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
</style>
