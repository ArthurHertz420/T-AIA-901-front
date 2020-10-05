<template>
  <div id="q-app">
    <router-view />
    <ModalGenerator/>
  </div>
</template>
<script>
import Vue from 'vue'
import AudioRecorder from 'vue-audio-recorder'
import VueRecord from '@codekraft-studio/vue-record'
import ModalGenerator from './components/Modal/ModalGenerator'
export default {
  name: 'App',
  mounted () {
    Vue.use(VueRecord)
    Vue.use(AudioRecorder)
  },
  components: {
    ModalGenerator
  }
}
</script>
