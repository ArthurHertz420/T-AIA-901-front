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
      // TODO make the call to send the blob to the backend
      // console.log('The blob data:', data)
      // console.log('Downloadable audio', window.URL.createObjectURL(data))
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
