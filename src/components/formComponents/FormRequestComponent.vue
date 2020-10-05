<template>
  <div class="column flex-center justify-between">
    <q-btn
      class="col-12 q-pa-md"
      size="xl"
      round
      color="primary"
      :icon="showForm === true ? 'keyboard_arrow_down': 'keyboard_arrow_up'"
      @click="showForm = ! showForm"
      style="margin-bottom: 1em;"
    />
    <FormComponent
      v-on:close="close"
      v-if="showForm"
      class="col-12"
    />
  </div>
</template>

<script>
import FormComponent from './FormComponent'
export default {
  name: 'FormRequestComponent',
  components: {
    FormComponent
  },
  data () {
    return {
      showForm: false
    }
  },
  methods: {
    close () {
      this.showForm = false
    }
  }
}
</script>

<style>

</style>
