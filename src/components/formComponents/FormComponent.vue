<template>
  <div><SpeakComponent v-on:search="search($event)" v-on:cancel="closeForm()"/></div>
</template>

<script>
import SpeakComponent from './SpeakComponent'
export default {
  name: 'FormComponent',
  components: {
    SpeakComponent
  },
  data () {
    return {
      record: null,
      tab: 'write'
    }
  },
  methods: {
    closeForm () {
      this.$emit('close')
    },
    search ($event) {
      // Todo call the api
      // The result from the request
      console.log($event)
      this.closeForm()
    }
  }
}
</script>

<style>

</style>
