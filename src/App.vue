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
  },
  created () {
    this.$root.$on('notify', this.showNotif)
  },
  methods: {
    showNotif (props) {
      this.$q.notify({
        icon: props[0],
        color: props[1],
        message: this.$t(props[2]),
        position: 'top-right'
      })
    }
  }
}
</script>
