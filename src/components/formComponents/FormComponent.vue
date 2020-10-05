<template>
  <q-card style="width: 100vw !important">
    <q-tabs
      v-model="tab"
      dense
      align="justify"
      class="bg-grey-3 text-grey-7"
      active-bg-color="primary"
      active-color="white"
    >
      <q-tab name="write" label="Ecrire"/>
      <q-tab name="speak" label="parler"/>
    </q-tabs>
    <q-tab-panels v-model="tab" animated>
      <q-tab-panel name="write">
        <!-- Call component to write request -->
        <WriteComponent/>
      </q-tab-panel>
      <q-tab-panel name="speak">
        <!-- Call component to tell the resquest -->
        <SpeakComponent v-on:search="search($event)"/>
      </q-tab-panel>
    </q-tab-panels>
  </q-card>
</template>

<script>
import WriteComponent from './WriteComponent'
import SpeakComponent from './SpeakComponent'
export default {
  name: 'FormComponent',
  components: {
    WriteComponent,
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
