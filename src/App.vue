<template>
  <div id="q-app">
    <router-view />
  </div>
</template>
<script>
import Vue from 'vue'
import AudioRecorder from 'vue-audio-recorder'
import VueRecord from '@codekraft-studio/vue-record'
export default {
  name: 'App',
  mounted () {
    Vue.use(VueRecord)
    Vue.use(AudioRecorder)
  }
}
</script>
