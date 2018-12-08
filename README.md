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
      :status="status"
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
      status: 'unchecked'
    }
  },
  methods: {
    toggleStatus() {
      let prevStatus = this.status
      this.status = 'loading'
      setTimeout(() => {
        this.status = prevStatus === 'checked' ? 'unchecked' : 'checked'
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

| prop                       | description                                                                  | default                             |
| -------------------------- | ---------------------------------------------------------------------------- | ----------------------------------- |
| `checked`                  | Status of component. can be `true`(checked) or `false`(unchecked)            | `false`                             |
| `loading`                  | If `true` component is in loading state. it has more priority than `checked` | `false`                             |
| `size`                     | Size of component in `px`.                                                   | `30`                                |
| `gap`                      | Gap size between checkbox and its label in `px`.                             | `null` (calculated based on `size`) |
| `borderWidth`              | width of checkbox border. You have to insert unit (`px`,`em`...)             | `1px`                               |
| `borderStyle`              | Style of checkbox border, (solid, dashed, dotted, ...)                       | `solid`                             |
| `borderColor`              | Color of checkbox border                                                     | `black`                             |
| `label`                    | Label of checkbox                                                            | `null` (no label)                   |
| `fontColor`                | Text color of label                                                          | `black`                             |
| `fontSize`                 | Font size of label                                                           | `null` (calculated based on `size`) |
| `checkedBackgroundColor`   | Background color of checkbox when status is checked                          | `gray`                              |
| `checkedBorderWidth`       | Border width of checkbox when status is checked                              | `null` (same as `borderWidth`)      |
| `checkedBorderStyle`       | Border style of checkbox when status is checked                              | `null` (same as `borderStyle`)      |
| `checkedBorderColor`       | Border color of checkbox when status is checked                              | `null` (same as `borderColor`)      |
| `checkColor`               | Color of check mark                                                          | `white`                             |
| `loadingBackgroundColor`   | Background color of checkbox when status is loading                          | `white`                             |
| `loadingBorderWidth`       | Border width of checkbox when status is loading                              | `null` (same as `borderWidth`)      |
| `loadingBorderStyle`       | Border style of checkbox when status is loading                              | `null` (same as `borderStyle`)      |
| `loadingBorderColor`       | Border color of checkbox when status is loading                              | `null` (same as `borderColor`)      |
| `spinnerRingColor`         | Color of loading ring                                                        | `lightgray`                         |
| `spinnerColor`             | Color of spinner                                                             | `black`                             |
| `uncheckedBackgroundColor` | Background color of checkbox when status is unchecked                        | `white`                             |
| `uncheckedBorderWidth`     | Border width of checkbox when status is unchecked                            | `null` (same as `borderWidth`)      |
| `uncheckedBorderStyle`     | Border style of checkbox when status is unchecked                            | `null` (same as `borderStyle`)      |
| `uncheckedBorderColor`     | Border color of checkbox when status is unchecked                            | `null` (same as `borderColor`)      |

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
