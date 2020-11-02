<template>
  <q-page class="flex flex-center">
    <q-footer class="flex flex-center" style="background-color: white;">
      <FormRequestComponent/>
    </q-footer>
  </q-page>
</template>

<script>
import FormRequestComponent from '../components/formComponents/FormRequestComponent'
export default {
  name: 'PageIndex',
  components: {
    FormRequestComponent
  }
}
</script>
