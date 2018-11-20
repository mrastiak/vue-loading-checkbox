<template>
  <div
    id="loadingCheckbox"
    :style="containerStyles"
  >
    <div
      class="checkbox"
      :class="status"
      :style="checkboxStyles"
    >
      <div
        class="loader"
        ref="loading"
        v-if="status === 'loading'"
        :style="loaderStyles"
      ></div>
      <div
        class="check"
        v-else-if="status === 'checked'"
        :style="checkStyles"
      ></div>
      <div
        class="empty"
        v-else
      ></div>
    </div>
    <p
      class="label"
      v-if="label"
      :style="labelStyles"
    >{{ label }}</p>
  </div>
</template>

<script>
export default {
  name: 'PendingCheckbox',
  props: {
    status: {
      type: String,
      default: 'unchecked'
    },
    label: {
      type: String,
      default: null
    },
    size: {
      type: Number,
      default: 30
    },
    fontSize: {
      type: Number,
      default: null
    },
    gap: {
      type: Number,
      default: null
    }
  },
  computed: {
    checkboxStyles () {
      return Object.assign(
        {
          width: `${this.size}px`,
          height: `${this.size}px`,
          borderWidth: '1px',
          borderColor: 'black',
          borderStyle: 'solid',
          position: 'relative'
        },
        this.checkedStyles,
        this.loadingStyles
      )
    },
    checkedStyles () {
      if (this.status === 'checked') {
        return {
          background: 'gray'
        }
      } else {
        return {}
      }
    },
    loadingStyles () {
      if (this.status === 'loading') {
        return {
          background: 'gray'
        }
      } else {
        return {}
      }
    },
    checkStyles () {
      return {
        position: 'absolute',
        border: 'solid white',
        top: '50%',
        left: '50%',
        transform: 'translate(-60%, -65%) rotate(45deg)',
        transformOrigin: '55% 55%',
        width: `${this.size * 0.33}px`,
        height: `${this.size * 0.66}px`,
        borderWidth: `0 ${this.size * 0.1 >= 2 ? this.size * 0.1 : 2}px ${this.size * 0.1 >= 2 ? this.size * 0.1 : 2}px 0`
      }
    },
    loaderStyles () {
      return Object.assign(
        {
          border: `${this.size * 0.2}px solid lightgray`,
          borderRadius: '50%',
          borderTop: `${this.size * 0.2}px solid black`,
          width: `${this.size}px`,
          height: `${this.size}px`,
          boxSizing: 'border-box'
        }
      )
    },
    containerStyles () {
      return Object.assign(
        {
          display: 'grid',
          gridTemplateColumns: 'auto 1fr',
          alignItems: 'center',
          width: 'fit-content',
          cursor: 'pointer'
        },
        this.computedGap
      )
    },
    labelStyles () {
      if (this.fontSize) {
        return {
          fontSize: `${this.fontSize}px`,
          lineHeight: `${this.fontSize}px`
        }
      } else {
        return {
          fontSize: `${this.size * 1.1}px`,
          lineHeight: `${this.size * 1.1}px`
        }
      }
    },
    computedGap () {
      if (this.gap) {
        return {
          gridColumnGap: `${this.gap}px`
        }
      } else {
        return {
          gridColumnGap: `${this.size * 0.2}px`
        }
      }
    }
  }
}
</script>

<style scoped lang="sass">
  *
    padding: 0
    margin: 0
  @-webkit-keyframes spin
    0%
      -webkit-transform: rotate(0deg)
    100%
      -webkit-transform: rotate(360deg)

  @keyframes spin
    0%
      transform: rotate(0deg)
    100%
      transform: rotate(360deg)

  .loader
    animation: spin 1s linear infinite
</style>
