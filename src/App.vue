<template>
  <div id="app">
    <loading-checkbox
      label="Checkbox"
      :size="50"
      :checked="checked"
      :loading="loading"
      @click.native="check"
      class="checkbox"
    />

  </div>
</template>

<script>
import LoadingCheckbox from './components/LoadingCheckbox'

export default {
  name: 'App',
  data () {
    return {
      checked: false,
      loading: false
    }
  },
  methods: {
    check () {
      this.loading = true
      setTimeout(() => {
        this.loading = false
        this.checked = !this.checked
      }, 1000)
    }
  },
  components: {
    LoadingCheckbox
  }
}
</script>

<style lang="sass">
#app
  margin: 100px auto
  width: fit-content
</style>
