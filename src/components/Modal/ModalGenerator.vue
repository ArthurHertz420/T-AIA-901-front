<template>
  <q-dialog
    v-model="openIt"
    transition-show="slide-up"
    transition-hide="slide-down"
    :full-width="fullWidth"
  >
    <!-- Modal's template list -->
    <div></div>
    <!-- End of modal's template list -->
  </q-dialog>
</template>

<script>
export default {
  name: 'ModalGenerator',
  data () {
    return {
      openIt: false,
      modalToOpen: '',
      id: null
    }
  },
  created () {
    this.$root.$on('openModal', this.openModal)
    this.$root.$on('close-modal', this.closeModal)
  },
  methods: {
    closeModal () {
      this.modalToOpen = ''
      this.id = null
      this.openIt = false
    },
    openModal (props) {
      this.modalToOpen = props[0]
      this.id = props[1]
      this.openIt = true
    }
  },
  computed: {
    fullWidth () {
      return false
    }
  }
}
</script>

<style>

</style>
