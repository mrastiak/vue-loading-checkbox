<template>
  <div id="app">
    <loading-checkbox
      label="Checkbox"
      :size="50"
      :status="status"
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
      status: 'unchecked'
    }
  },
  methods: {
    check () {
      let prevStatus = this.status
      this.status = 'loading'
      setTimeout(() => {
        if (prevStatus === 'unchecked') {
          this.status = 'checked'
        } else if (prevStatus === 'checked') {
          this.status = 'unchecked'
        }
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
