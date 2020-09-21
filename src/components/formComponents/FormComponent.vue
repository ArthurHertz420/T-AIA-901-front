<template>
  <q-card style="width: 100vw !important">
    <q-card-section class="row justify-between">
      <textarea class="col-8" v-model="query" placeholder="Tapez votre requête ici"></textarea>
      <vue-record-audio
        @result="onResult"
        mode="hold"
      />
    </q-card-section>
    <q-card-actions class="row justify-center">
      <q-btn
        color="positive"
        label="Valider"
        icon="search"
        @click="search"
      />
      <q-btn
        color="negative"
        label="Annuler"
        icon="clear"
        @click="closeForm"
      />
    </q-card-actions>
  </q-card>
</template>

<script>
export default {
  name: 'FormComponent',
  data () {
    return {
      query: '',
      record: null
    }
  },
  methods: {
    closeForm () {
      this.$emit('close')
    },
    search () {
      // Todo call the api
      this.closeForm()
    },
    mic () {
      console.log('test')
    },
    onResult (data) {
      // TODO make the call to send the blob to the backend
      console.log('The blob data:', data)
      console.log('Downloadable audio', window.URL.createObjectURL(data))
    }
  }
}
</script>

<style>

</style>
