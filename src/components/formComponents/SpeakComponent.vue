<template>
  <div>
    <div class="row justify-center" style="margin-bottom: 2em;">
      <vue-record-audio
        v-if="!requestSend"
        @result="onResult"
        mode="hold"
      />
      <textarea class="col-12" v-model="result" v-if="requestSend"></textarea>
    </div>
    <div class="row justify-around" v-if="requestSend">
      <q-btn
        color="positive"
        :label="$t('actions.search')"
        v-on:click="search()"
      />
      <q-btn
        color="primary"
        :label="$t('actions.retry')"
        v-on:click="retry()"
      />
      <q-btn
        color="negative"
        :label="$t('actions.cancel')"
        v-on:click="cancel()"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'SpeakComponent',
  data () {
    return {
      result: '',
      requestSend: false
    }
  },
  methods: {
    onResult (data) {
      var toWav = require('audiobuffer-to-wav')
      var xhr = require('xhr')
      var axios = require('axios')
      var audioContext = new AudioContext()

      // Convert blob returned to webm file
      var file = new File([data], 'output', {
        type: 'audio/webm',
        lastModified: new Date()
      })

      xhr({
        uri: window.URL.createObjectURL(file),
        responseType: 'arraybuffer'
      }, function (err, body, resp) {
        if (err) throw err

        audioContext.decodeAudioData(resp, async function (buffer) {
          // Convert file to wav
          var wav = toWav(buffer)
          var blob = new window.Blob([new DataView(wav)], {
            type: 'audio/wav'
          })

          // Create form data and append the file
          var formData = new FormData()
          formData.append('file', blob, 'output.wav')

          // Post the file
          await axios({
            method: 'post',
            url: 'https://stt-tts-middleware.herokuapp.com/api/stt/audio',
            data: formData,
            headers: {
              'Content-Type': 'multipart/form-data'
            }
          }).then((response) => {
            // Show to front the text returned from middleware
            console.log(response)
          })
        })
      })

      this.requestSend = true
      this.result = 'test'
    },
    retry () {
      this.result = ''
      this.requestSend = false
    },
    search () {
      // Todo make this function
      this.$emit('search', this.result)
    },
    cancel () {
      // TODO make this function
      this.$emit('cancel')
    }
  }
}
</script>

<style>

</style>
