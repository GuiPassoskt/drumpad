<template>
  <q-page class="q-pa-md flex">
      <a 
      href="#" v-for="(s, index) in sounds" 
      class="pad" @click="playDrum(s.name)" 
      :name="s.name" 
      :key="`${index} - ${s.name}`">
        <img :src="s.icon" alt="" width="35">
      </a>
  </q-page>
</template>

<script>
import sounds from '../assets/sounds'
export default {
  name: 'PageIndex',
  data() {
    return {
      sounds: []
    }
  },
  methods: {
    playDrum(pad) {
      let audio = new Audio()
      audio.src = sounds.filter(item => item.name == pad)[0].sound
      audio.currentTime = -1
      audio.play()
    }
  },
  mounted() {
    this.sounds = sounds
  }
}
</script>

<style scoped>
.pad {
  background: var(--q-color-dark);
  border-radius: 5px;
  color: white;
  padding: 10px;
  margin: 5px;
  width: 100%;
  flex: 1 142px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
}
.pad:active {
  background: var(--orange);
}
</style>
