<p align="center">
  <a href="#">
    <img src="https://github.com/Carrene/vue-loading-checkbox/blob/master/src/assets/checkbox-demo.gif?raw=true" alt="vue-loading-checkbox" />
  </a>
</p>

<h1 align="center" >vue-loading-checkbox</h1>

<p align="center" class="badges" >
  <a href="https://www.npmjs.com/package/vue-loading-checkbox"><img src="https://badge.fury.io/js/vue-loading-checkbox.svg" alt="npm version" /></a>
</p>

A vue UI component for loading checkbox

## How to install

```
npm install vue-loading-checkbox --save
```

## How to use

Inside your `.vue` files

```vue
<template>
  <div id="your-component">
    <!-- Using Component -->
    <loading-checkbox
      :checked="checked"
      :loading="loading"
      label="Title of checkbox"
      @click.native="toggleStatus"
    />
  </div>
</template>
<script>
// Importing Component and style
import LoadingCheckbox from 'vue-loading-checkbox'
import 'vue-loading-checkbox/dist/LoadingCheckbox.css'

export default {
  name: 'YourComponentName',
  data() {
    return {
      checked: false,
      loading: false
    }
  },
  methods: {
    toggleStatus() {
      this.loading = true
      setTimeout(() => {
        this.loading = false
        this.checked = !this.checked
      }, 2000)
    }
  },
  components: {
    LoadingCheckbox // Registering Component
  }
}
</script>
```

## Component props

| prop                       | description                                                                      | default                             |
| -------------------------- | -------------------------------------------------------------------------------- | ----------------------------------- |
| `borderColor`              | Color of checkbox border                                                         | `black`                             |
| `borderStyle`              | Style of checkbox border, (solid, dashed, dotted, ...)                           | `solid`                             |
| `borderWidth`              | width of checkbox border. You have to insert unit (`px`,`em`...)                 | `1px`                               |
| `checkColor`               | Color of check mark                                                              | `white`                             |
| `checked`                  | Status of component. can be `true`(checked) or `false`(unchecked)                | `false`                             |
| `checkedBackgroundColor`   | Background color of checkbox when status is checked                              | `gray`                              |
| `checkedBorderColor`       | Border color of checkbox when status is checked                                  | `null` (same as `borderColor`)      |
| `checkedBorderStyle`       | Border style of checkbox when status is checked                                  | `null` (same as `borderStyle`)      |
| `checkedBorderWidth`       | Border width of checkbox when status is checked                                  | `null` (same as `borderWidth`)      |
| `checkIcon`                | Custom check mark image (.svg, png, etc)                                         | `null` A default pure css check     |
| `checkIconPadding`         | Padding of the given custom check mark image (This will not affect the `size`)   | `null`                              |
| `fontColor`                | Text color of label                                                              | `black`                             |
| `fontSize`                 | Font size of label                                                               | `null` (calculated based on `size`) |
| `gap`                      | Gap size between checkbox and its label in `px`.                                 | `null` (calculated based on `size`) |
| `label`                    | Label of checkbox                                                                | `null` (no label)                   |
| `loading`                  | If `true` component is in loading state. it has a higher priority than `checked` | `false`                             |
| `loadingBackgroundColor`   | Background color of checkbox when status is loading                              | `white`                             |
| `loadingBorderColor`       | Border color of checkbox when status is loading                                  | `null` (same as `borderColor`)      |
| `loadingBorderStyle`       | Border style of checkbox when status is loading                                  | `null` (same as `borderStyle`)      |
| `loadingBorderWidth`       | Border width of checkbox when status is loading                                  | `null` (same as `borderWidth`)      |
| `size`                     | Size of component in `px`.                                                       | `30`                                |
| `spinnerColor`             | Color of spinner                                                                 | `black`                             |
| `spinnerRingColor`         | Color of loading ring                                                            | `lightgray`                         |
| `uncheckedBackgroundColor` | Background color of checkbox when status is unchecked                            | `white`                             |
| `uncheckedBorderColor`     | Border color of checkbox when status is unchecked                                | `null` (same as `borderColor`)      |
| `uncheckedBorderStyle`     | Border style of checkbox when status is unchecked                                | `null` (same as `borderStyle`)      |
| `uncheckedBorderWidth`     | Border width of checkbox when status is unchecked                                | `null` (same as `borderWidth`)      |

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build-bundle
```

### Lints and fixes files

```
npm run lint
```

## License

MIT
