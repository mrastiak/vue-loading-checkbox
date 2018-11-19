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
  name: 'LoadingCheckbox',
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
    fontColor: {
      type: String,
      default: 'black'
    },
    gap: {
      type: Number,
      default: null
    },
    borderColor: {
      type: String,
      default: 'black'
    }
  },
  computed: {
    checkboxStyles () {
      return Object.assign(
        {
          width: `${this.size}px`,
          height: `${this.size}px`,
          borderWidth: '1px',
          borderColor: this.borderColor,
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
        width: `${this.size * 0.33}px`,
        height: `${this.size * 0.66}px`,
        borderWidth: `0 ${this.size * 0.1 >= 2 ? this.size * 0.1 : 2}px ${this.size * 0.1 >= 2 ? this.size * 0.1 : 2}px 0`
      }
    },
    loaderStyles () {
      return Object.assign(
        {
          border: `${this.size * 0.2}px solid lightgray`,
          borderTop: `${this.size * 0.2}px solid black`,
          width: `${this.size}px`,
          height: `${this.size}px`
        }
      )
    },
    containerStyles () {
      return Object.assign(
        {},
        this.computedGap
      )
    },
    labelStyles () {
      return Object.assign(
        {},
        this.labelFontSize,
        this.labelColor
      )
    },
    labelFontSize () {
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
    labelColor () {
      if (this.fontColor) {
        return {
          color: this.fontColor
        }
      } else {
        return {
          color: `black`
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

  #loadingCheckbox
    display: grid
    grid-template-columns: auto 1fr
    align-items: center
    width: fit-content
    cursor: pointer
    .checkbox
      border-width: 1px
      border-color: black
      border-style: solid
      position: relative

    .loader
      animation: spin 1s linear infinite
      border-radius: 50%
      box-sizing: border-box

    .check
      position: absolute
      border: solid white
      top: 50%
      left: 50%
      transform: translate(-60%, -65%) rotate(45deg)
      transform-origin: 55% 55%
</style>
