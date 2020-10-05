<template>
  <div>
    <div class="row" style="margin-bottom: 2em;">
      <textarea class="col-12" v-model="query" placeholder="Tapez votre requête ici"></textarea>
    </div>
    <div class="row justify-around">
      <q-btn
        color="positive"
        label="Rechercher"
        @click="search()"
      />
      <q-btn
        color="negative"
        label="Annuler"
        @click="cancel()"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'WriteComponent',
  data () {
    return {
      query: ''
    }
  },
  methods: {
    search () {
      // TODO emit the search query
      this.$emit('search', this.query)
    },
    cancel () {
      // TODO emit the cancel query
      this.$emit('cancel')
    }
  }
}
</script>

<style>

</style>
