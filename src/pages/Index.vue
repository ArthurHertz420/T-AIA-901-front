<template>
  <q-page class="flex flex-center">
    <div>{{result}}</div>
    <q-footer class="flex flex-center" style="background-color: white;">
      <FormRequestComponent/>
    </q-footer>
  </q-page>
</template>

<script>
import FormRequestComponent from '../components/formComponents/FormRequestComponent'
export default {
  name: 'PageIndex',
  data () {
    return {
      result: ''
    }
  },
  components: {
    FormRequestComponent
  },
  created () {
    this.$root.$on('result', event => {
      this.result = event.data
    })
  }
}
</script>
