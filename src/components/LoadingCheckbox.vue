<template>
  <div
    id="loadingCheckbox"
    :style="containerStyles"
  >
    <div
      class="checkbox"
      :style="checkboxStyles"
    >
      <div
        class="loader"
        ref="loading"
        v-if="loading"
        :style="loaderStyles"
      ></div>
      <div
        :class="checkIcon ? 'checkContainer' : 'check'"
        v-else-if="checked"
        :style="!checkIcon ? checkStyles : null"
      >
        <img
          v-if="checkIcon"
          :src="checkIcon"
          class="icon"
          :style="iconStyles"
        >
      </div>
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
    // GENERAL PROPS

    checked: {
      type: Boolean,
      default: false
    },
    loading: {
      type: Boolean,
      default: false
    },
    size: {
      type: Number,
      default: 30
    },
    gap: {
      type: Number,
      default: null
    },
    borderWidth: {
      type: String,
      default: '1px'
    },
    borderStyle: {
      type: String,
      default: 'solid'
    },
    borderColor: {
      type: String,
      default: 'black'
    },

    // LABEL PROPS

    label: {
      type: String,
      default: null
    },
    fontColor: {
      type: String,
      default: 'black'
    },
    fontSize: {
      type: Number,
      default: null
    },

    // CHECKED PROPS

    checkedBackgroundColor: {
      type: String,
      default: 'gray'
    },
    checkedBorderWidth: {
      type: String,
      default: null
    },
    checkedBorderStyle: {
      type: String,
      default: null
    },
    checkedBorderColor: {
      type: String,
      default: null
    },
    checkColor: {
      type: String,
      default: 'white'
    },

    // LOADING PROPS

    loadingBackgroundColor: {
      type: String,
      default: 'white'
    },
    loadingBorderWidth: {
      type: String,
      default: null
    },
    loadingBorderStyle: {
      type: String,
      default: null
    },
    loadingBorderColor: {
      type: String,
      default: null
    },
    spinnerRingColor: {
      type: String,
      default: 'lightgray'
    },
    spinnerColor: {
      type: String,
      default: 'black'
    },

    // UNCHECKED PROPS

    uncheckedBackgroundColor: {
      type: String,
      default: 'white'
    },
    uncheckedBorderWidth: {
      type: String,
      default: null
    },
    uncheckedBorderStyle: {
      type: String,
      default: null
    },
    uncheckedBorderColor: {
      type: String,
      default: null
    },
    checkIcon: {
      type: String,
      default: null
    },
    checkIconPadding: {
      type: String,
      default: null
    }
  },
  computed: {
    checkboxStyles () {
      return Object.assign(
        {
          width: `${this.size}px`,
          height: `${this.size}px`,
          position: 'relative'
        },
        this.checked && !this.loading ? this.checkedStyles : {},
        this.loading ? this.loadingStyles : {},
        !this.checked && !this.loading ? this.uncheckedStyles : {}
      )
    },
    checkedStyles () {
      return {
        backgroundColor: this.checkedBackgroundColor,
        borderWidth: this.checkedBorderWidth || this.borderWidth,
        borderStyle: this.checkedBorderStyle || this.borderStyle,
        borderColor: this.checkedBorderColor || this.borderColor
      }
    },
    loadingStyles () {
      return {
        backgroundColor: this.loadingBackgroundColor,
        borderWidth: this.loadingBorderWidth || this.borderWidth,
        borderColor: this.loadingBorderColor || this.borderColor,
        borderStyle: this.loadingBorderStyle || this.borderStyle
      }
    },
    uncheckedStyles () {
      return {
        backgroundColor: this.uncheckedBackgroundColor,
        borderWidth: this.uncheckedBorderWidth || this.borderWidth,
        borderColor: this.uncheckedBorderColor || this.borderColor,
        borderStyle: this.uncheckedBorderStyle || this.borderStyle
      }
    },
    checkStyles () {
      return {
        width: `${this.size * 0.33}px`,
        height: `${this.size * 0.66}px`,
        borderWidth: `0 ${this.size * 0.1 >= 2 ? this.size * 0.1 : 2}px ${this.size * 0.1 >= 2 ? this.size * 0.1 : 2}px 0`,
        borderColor: this.checkColor
      }
    },
    iconStyles () {
      return {
        padding: this.checkIconPadding
      }
    },
    loaderStyles () {
      return Object.assign(
        {
          borderWidth: `${this.size * 0.2}px`,
          borderStyle: 'solid',
          borderColor: this.spinnerRingColor,
          borderTopWidth: `${this.size * 0.2}px`,
          borderTopColor: this.spinnerColor,
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
        {
          color: this.fontColor
        },
        this.labelFontSize
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
      position: relative

    .loader
      animation: spin 1s linear infinite
      border-radius: 50%
      box-sizing: border-box

    .check
      position: absolute
      border-style: solid
      top: 50%
      left: 50%
      transform: translate(-60%, -65%) rotate(45deg)
      transform-origin: 55% 55%

    .check-container
      display: grid
      height: 100%
      align-items: center
      .icon
        max-height: 100%
        max-width: 100%
        box-sizing: border-box
</style>
