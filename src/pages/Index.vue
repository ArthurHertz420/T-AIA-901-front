<template>
  <q-page>
    <div style="height: 65vh">{{result}}</div>
    <FormComponent/>
  </q-page>
</template>

<script>
import FormComponent from 'components/formComponents/FormComponent'
export default {
  name: 'PageIndex',
  data () {
    return {
      result: ''
    }
  },
  components: {
    FormComponent
  },
  created () {
    this.$root.$on('result', event => {
      this.result = event.data
    })
  }
}
</script>
