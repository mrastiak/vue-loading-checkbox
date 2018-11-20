# vue-loading-checkbox

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
  data () {
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
